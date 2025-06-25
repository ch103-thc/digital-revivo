<script>
	import "../app.css";
	import Icon from "@iconify/svelte";
	import "@fontsource/poppins";
	import { onMount } from "svelte";
	let { children } = $props();

	let searchQuery = $state("");
	let isMenuOpen = $state(false);
	let isMobile = $state(false);
	let showAutocomplete = $state(false);
	let autocompleteResults = $state([]);
	let selectedIndex = $state(-1);
	let searchInputRef;

	// Sample products for autocomplete (you can import this from a shared file)
	const allProducts = [
		{
			title: "COSRX Advanced Snail 96 Mucin Power Essence",
			category: "Face Serums",
		},
		{
			title: "COSRX Full Fit Propolis Light Ampoule",
			category: "Face Serums",
		},
		{
			title: "COSRX Low pH Good Morning Gel Cleanser",
			category: "Face Cleansers",
		},
		{
			title: "COSRX Full Fit Propolis Light Cream",
			category: "Moisturizers",
		},
		{
			title: "COSRX Oil Free Ultra Moisturizing Lotion with Birch Sap",
			category: "Moisturizers",
		},
		{
			title: "COSRX Hyaluronic Acid Intensive Cream",
			category: "Moisturizers",
		},
		{
			title: "COSRX Advanced Snail 92 All In One Cream",
			category: "Moisturizers",
		},
		{
			title: "COSRX Ultimate Nourishing Rice Overnight Spa Mask",
			category: "Masks & Exfoliators",
		},
		{
			title: "COSRX Niacinamide 15% Peptide Booster Set",
			category: "Face Serums",
		},
		{ title: "COSRX The Niacinamide 15 Serum", category: "Face Serums" },
		{ title: "COSRX Acne Pimple Master Patch", category: "Acne Patches" },
		{ title: "COSRX Full Fit Propolis Synergy Toner", category: "Toners" },
		{ title: "COSRX The Vitamin C 23 Serum", category: "Face Serums" },
		{ title: "COSRX The Retinol 0.3 Cream", category: "Moisturizers" },
		{ title: "COSRX The Retinol 0.5 Oil", category: "Moisturizers" },
		{
			title: "COSRX AHA/BHA Clarifying Treatment Toner",
			category: "Toners",
		},
		{
			title: "COSRX Hyaluronic Acid Hydra Power Essence",
			category: "Face Serums",
		},
		{
			title: "COSRX Advanced Snail Mucin Glass Glow Hydrogel Mask",
			category: "Masks & Exfoliators",
		},
		{
			title: "COSRX The Peptide Collagen Hydrogel Eye Patch",
			category: "Eye Care",
		},
		{
			title: "ANUA Heartleaf 70 Intense Calming Cream",
			category: "Moisturizers",
		},
		{ title: "ANUA Heartleaf Daily Lotion", category: "Moisturizers" },
		{
			title: "ANUA Rice 70 Intensive Moisturizing Milk",
			category: "Moisturizers",
		},
		{
			title: "ANUA 3 Ceramide Panthenol Moisture Barrier Cream",
			category: "Moisturizers",
		},
		{
			title: "ANUA Heartleaf Quercetinol Pore Deep Cleansing Foam",
			category: "Face Cleansers",
		},
		{
			title: "ANUA Rice Enzyme Brightening Cleansing Powder",
			category: "Face Cleansers",
		},
		{
			title: "ANUA Heartleaf 77 Toner Pad",
			category: "Toners",
		},
		{
			title: "ANUA Heartleaf Silky Moisture Mild Sunscreen",
			category: "Sunscreen",
		},
		{
			title: "ANUA Peach 70 Niacinamide Serum",
			category: "Face Serums",
		},
		{
			title: "ANUA Peach 77 Niacin Essence Toner",
			category: "Toners",
		},
		{
			title: "ANUA Rice 70 Glow Milky Toner",
			category: "Toners",
		},
		{
			title: "ANUA Rice Ceramide 7 Hydrating Barrier Serum",
			category: "Face Serums",
		},
		{
			title: "ANUA BHA 2% Gentle Exfoliating Toner",
			category: "Toners",
		},
		{
			title: "ANUA Heartleaf Pore Control Cleansing Oil",
			category: "Face Cleansers",
		},
		{ title: "ANUA Heartleaf 77 Soothing Toner", category: "Toners" },
		{ title: "ANUA Niacinamide 10 + TXA 4 Serum", category: "Face Serums" },
		{ title: "Beauty of Joseon Dynasty Cream", category: "Moisturizers" },
		{
			title: "Beauty of Joseon Ginseng Cleansing Oil",
			category: "Face Cleansers",
		},
		{
			title: "Beauty of Joseon Glow Deep Serum Rice + Alpha-Arbutin",
			category: "Face Serums",
		},
		{
			title: "Beauty of Joseon Green Plum Refreshing Cleanser",
			category: "Face Cleansers",
		},
		{
			title: "Beauty of Joseon Ground Rice and Honey Glow Mask",
			category: "Masks & Exfoliators",
		},
		{
			title: "Beauty of Joseon Red Bean Water Gel",
			category: "Moisturizers",
		},
		{
			title: "Beauty of Joseon Revive Eye Serum",
			category: "Eye Care",
		},
		{
			title: "Beauty of Joseon Apricot Blossom Peeling Gel",
			category: "Masks & Exfoliators",
		},
		{
			title: "Beauty of Joseon Calming Serum Green Tea + Panthenol",
			category: "Face Serums",
		},
		{
			title: "Beauty of Joseon Ginseng Essence Water",
			category: "Face Serums",
		},
		{
			title: "Beauty of Joseon Glow Replenishing Rice Milk",
			category: "Toners",
		},
		{
			title: "Beauty of Joseon Light On Serum Centella + Vita C",
			category: "Face Serums",
		},
		{
			title: "Beauty of Joseon Red Bean Refreshing Pore Mask",
			category: "Masks & Exfoliators",
		},
	];

	// Debounce function for better performance
	function debounce(func, wait) {
		let timeout;
		return function executedFunction(...args) {
			const later = () => {
				clearTimeout(timeout);
				func(...args);
			};
			clearTimeout(timeout);
			timeout = setTimeout(later, wait);
		};
	}

	// Update autocomplete results
	const updateAutocomplete = debounce((query) => {
		if (!query.trim()) {
			autocompleteResults = [];
			showAutocomplete = false;
			return;
		}

		const filtered = allProducts
			.filter((product) =>
				product.title.toLowerCase().includes(query.toLowerCase()),
			)
			.slice(0, 5); // Limit to 5 results

		autocompleteResults = filtered;
		showAutocomplete = filtered.length > 0;
		selectedIndex = -1;
	}, 300);

	// Handle search input changes
	function handleSearchInput(event) {
		searchQuery = event.target.value;
		updateAutocomplete(searchQuery);
	}

	// Handle keyboard navigation
	function handleKeydown(event) {
		if (!showAutocomplete) return;

		switch (event.key) {
			case "ArrowDown":
				event.preventDefault();
				selectedIndex = Math.min(
					selectedIndex + 1,
					autocompleteResults.length - 1,
				);
				break;
			case "ArrowUp":
				event.preventDefault();
				selectedIndex = Math.max(selectedIndex - 1, -1);
				break;
			case "Enter":
				event.preventDefault();
				if (selectedIndex >= 0) {
					selectAutocompleteResult(
						autocompleteResults[selectedIndex],
					);
				} else {
					handleSearch();
				}
				break;
			case "Escape":
				showAutocomplete = false;
				selectedIndex = -1;
				searchInputRef?.blur();
				break;
		}
	}

	// Select autocomplete result
	function selectAutocompleteResult(product) {
		searchQuery = product.title;
		showAutocomplete = false;
		selectedIndex = -1;
		handleSearch();
	}

	// Handle search
	function handleSearch() {
		console.log("Search query:", searchQuery.trim());
		if (searchQuery.trim()) {
			showAutocomplete = false;
			window.location.href = `/search?q=${encodeURIComponent(searchQuery.trim())}`;
			console.log(
				"Navigating to:",
				`/search?q=${encodeURIComponent(searchQuery.trim())}`,
			);
		}
	}

	// Hide autocomplete when clicking outside
	function handleClickOutside(event) {
		if (!event.target.closest(".search-container")) {
			showAutocomplete = false;
			selectedIndex = -1;
		}
	}

	const checkMobile = () => {
		isMobile = window.innerWidth <= 768;
	};

	const toggleMenu = () => {
		isMenuOpen = !isMenuOpen;
	};

	onMount(() => {
		checkMobile();
		window.addEventListener("resize", checkMobile);
		document.addEventListener("click", handleClickOutside);

		return () => {
			window.removeEventListener("resize", checkMobile);
			document.removeEventListener("click", handleClickOutside);
		};
	});
</script>

<svelte:window on:resize={checkMobile} />

<main>
	<div class="nav">
		<div class="nav-content">
			<div class="logo">
				<a href="/" class="logo-link">
					<h1 class="username">Digital Revivo</h1>
				</a>
			</div>

			<div class="nav-right">
				<div class="search-container">
					<div class="search-wrapper">
						<Icon
							icon="mingcute:search-line"
							width="20"
							height="20"
							class="search-icon"
						/>
						<input
							bind:this={searchInputRef}
							type="text"
							bind:value={searchQuery}
							oninput={handleSearchInput}
							onkeydown={handleKeydown}
							placeholder="Search products..."
							class="search-input"
							autocomplete="off"
						/>
					</div>

					<!-- Autocomplete Dropdown -->
					{#if showAutocomplete && autocompleteResults.length > 0}
						<div class="autocomplete-dropdown">
							{#each autocompleteResults as product, index}
								<div
									class="autocomplete-item"
									class:selected={index === selectedIndex}
									onclick={() =>
										selectAutocompleteResult(product)}
								>
									<div class="product-info">
										<span class="product-title"
											>{product.title}</span
										>
										<span class="product-category"
											>{product.category}</span
										>
									</div>
								</div>
							{/each}
						</div>
					{/if}
				</div>

				<ul class="menulist" class:active={isMenuOpen}>
					<li>
						<a href="/collections/bestsellers" onclick={toggleMenu}>
							Bestsellers
							{#if isMobile}
								<Icon
									icon="ep:right"
									width="20"
									height="20"
									class="menu-icon"
								/>
							{/if}
						</a>
					</li>
					<li>
						<a href="/skincare-routine" onclick={toggleMenu}>
							Skincare Routine
							{#if isMobile}
								<Icon
									icon="ep:right"
									width="20"
									height="20"
									class="menu-icon"
								/>
							{/if}
						</a>
					</li>
					<li>
						<a href="/collections/shop-all" onclick={toggleMenu}>
							Shop All
							{#if isMobile}
								<Icon
									icon="ep:right"
									width="20"
									height="20"
									class="menu-icon"
								/>
							{/if}
						</a>
					</li>
					<li class="social-links">
						<a
							href="https://www.instagram.com/swiftcurated"
							target="_blank"
							rel="noopener"
						>
							<Icon icon="mdi:instagram" width="20" height="20" />
						</a>
					</li>
				</ul>
			</div>

			<button class="menu-toggle" onclick={toggleMenu}>
				<Icon
					icon={isMenuOpen ? "mdi:close" : "mdi:menu"}
					width="24"
					height="24"
				/>
			</button>
		</div>
	</div>

	{@render children()}

	<footer class="footer">
		<div class="footer-content">
			<div class="footer-top">
				<div class="footer-brand">
					<h3>Digital Revivo</h3>
					<p>
						Your trusted partner for premium Korean skincare
						products. Discover the secret to healthy, glowing skin
						with our curated collection.
					</p>
					<div class="social-links">
						<a
							href="mailto:hello@digitalrevivo.com"
							aria-label="Email us"
						>
							<Icon
								icon="mdi:email-outline"
								width="24"
								height="24"
							/>
						</a>
						<a
							href="https://www.instagram.com/"
							target="_blank"
							rel="noopener"
							aria-label="Follow us on Instagram"
						>
							<Icon icon="mdi:instagram" width="24" height="24" />
						</a>
						<a
							href="https://www.facebook.com/"
							target="_blank"
							rel="noopener"
							aria-label="Follow us on Facebook"
						>
							<Icon icon="mdi:facebook" width="24" height="24" />
						</a>
						<a href="tel:+1234567890" aria-label="Call us">
							<Icon icon="mdi:pinterest" width="24" height="24" />
						</a>
					</div>
				</div>

				<div class="footer-links">
					<div class="footer-column">
						<h4>Shop</h4>
						<ul>
							<li>
								<a href="/collections/bestsellers">
									Bestsellers
								</a>
							</li>
							<li>
								<a href="/collections/cleansers"
									>Face Cleansers</a
								>
							</li>
							<li>
								<a href="/collections/moisturizers"
									>Moisturizers</a
								>
							</li>
							<li><a href="/collections/toners">Toners</a></li>
							<li>
								<a href="/collections/serums">Face Serums</a>
							</li>
							<li>
								<a href="/collections/masks-and-exfoliators"
									>Masks & Exfoliators</a
								>
							</li>
							<li>
								<a href="/collections/acne-patches"
									>Acne Patches</a
								>
							</li>
							<li>
								<a href="/collections/sunscreen">Sunscreen</a>
							</li>
							<li>
								<a href="/collections/eye-care">Eye Care</a>
							</li>
						</ul>
					</div>

					<div class="footer-column">
						<h4>Brands</h4>
						<ul>
							<li><a href="/brands/cosrx">COSRX</a></li>
							<li><a href="/brands/anua">ANUA</a></li>
							<li>
								<a href="/brands/beauty-of-joseon"
									>Beauty of Joseon</a
								>
							</li>
						</ul>
					</div>

					<div class="footer-column">
						<h4>Skincare Tips</h4>
						<ul>
							<li>
								<a href="/articles/korean-skincare-routine"
									>Skincare Guide
								</a>
							</li>
							<li>
								<a href="/skincare-routine">Skincare Routine</a>
							</li>
							<!-- <li>
								<a href="/ingredient-guide">Ingredient Guide</a>
							</li>
							<li><a href="/skin-concerns">Skin Concerns</a></li>
							<li>
								<a href="/morning-routine">Morning Routine</a>
							</li>
							<li>
								<a href="/evening-routine">Evening Routine</a>
							</li> -->
							<li><a href="/seasonal-care">Seasonal Care</a></li>
						</ul>
					</div>

					<div class="footer-column">
						<h4>Support</h4>
						<ul>
							<li><a href="/contact">Contact Us</a></li>
							<li><a href="/faq">FAQ</a></li>
						</ul>
					</div>
				</div>
			</div>

			<div class="footer-bottom">
				<div class="footer-bottom-content">
					<p>
						&copy; {new Date().getFullYear()} Digital Revivo. All rights
						reserved.
					</p>
				</div>
			</div>
		</div>
	</footer>
</main>

<style lang="scss">
	main {
		font-family: "Poppins", sans-serif;
	}

	.nav {
		position: fixed;
		top: 0;
		right: 0;
		width: 100%;
		z-index: 1000;
		transition: all 0.6s ease;
		background: rgba(255, 255, 255, 0.4);
		backdrop-filter: blur(10px);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		height: 80px;

		.nav-content {
			max-width: 1200px;
			margin: 0 auto;
			padding: 1rem 2rem;
			display: flex;
			align-items: center;
			justify-content: space-between;
			height: 100%;

			@media (max-width: 768px) {
				padding: 15px 5%;
			}
		}

		.nav-right {
			display: flex;
			align-items: center;
			gap: 1rem;
		}

		.logo {
			display: flex;
			align-items: center;

			.logo-link {
				display: flex;
				align-items: center;
				text-decoration: none;

				.logo-img {
					width: 50px;
					height: 50px;
					border-radius: 50%;
					object-fit: cover;
					margin-right: 10px;
				}
			}

			.username {
				font-weight: bold;
			}
		}

		.menu-toggle {
			display: none;
			background: none;
			border: none;
			cursor: pointer;
			padding: 5px;
			z-index: 1001;
		}

		.search-container {
			position: relative;
			display: flex;
			align-items: center;
			justify-content: center;
			padding: 0 1rem;

			.search-wrapper {
				position: relative;
				display: flex;
				align-items: center;
				width: 400px;
				border: 1px solid #ccc;
				border-radius: 20px;
				transition: all 0.3s ease;

				&:focus-within {
					border-color: #999;
					box-shadow: 0 0 0 2px rgba(0, 0, 0, 0.1);
				}

				:global(.search-icon) {
					position: absolute;
					left: 12px;
					color: #666;
					z-index: 1;
					pointer-events: none;
				}

				.search-input {
					padding: 8px 12px 8px 40px;
					border: none;
					border-radius: 20px;
					width: 100%;
					background: transparent;

					&:focus {
						outline: none;
					}
				}
			}

			.autocomplete-dropdown {
				position: absolute;
				top: 100%;
				left: 1rem;
				right: 1rem;
				background: white;
				border: 1px solid #ddd;
				border-radius: 12px;
				box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
				z-index: 1001;
				max-height: 300px;
				overflow-y: auto;
				margin-top: 4px;

				.autocomplete-item {
					padding: 12px 16px;
					cursor: pointer;
					transition: background-color 0.2s ease;
					border-bottom: 1px solid #f0f0f0;

					&:last-child {
						border-bottom: none;
					}

					&:hover,
					&.selected {
						background-color: #f8f9fa;
					}

					.product-info {
						display: flex;
						flex-direction: column;
						gap: 4px;

						.product-title {
							font-size: 0.9rem;
							font-weight: 500;
							color: #333;
							line-height: 1.3;
						}

						.product-category {
							font-size: 0.8rem;
							color: #666;
							text-transform: uppercase;
							letter-spacing: 0.5px;
						}
					}
				}
			}
		}

		@media (max-width: 768px) {
			.menu-toggle {
				display: block;
			}

			.search-container {
				width: 100%;
				padding: 10px 5%;
				order: 2;

				.search-wrapper {
					width: 100%;

					.search-input {
						width: 100%;
					}
				}

				.autocomplete-dropdown {
					left: 5%;
					right: 5%;
				}
			}
		}

		.menulist {
			display: flex;
			list-style: none;
			margin: 0;
			padding: 0;
			gap: 10px;

			li {
				a {
					display: flex;
					align-items: center;
					text-decoration: none;
					color: inherit;
					padding: 8px 16px;

					.menu-icon {
						margin-left: 10px;
						flex-shrink: 0;
					}
				}
			}

			&.active {
				right: 0;
			}

			.social-links {
				display: none;

				@media (max-width: 768px) {
					display: flex;
					justify-content: center;
					width: 100%;
					margin-top: auto;
					padding: 1rem 0;
					border-top: 1px solid rgba(0, 0, 0, 0.1);
				}

				a {
					color: inherit;
				}
			}
		}

		@media (max-width: 768px) {
			.menulist {
				position: fixed;
				top: 80px;
				right: -100%;
				width: 70%;
				height: calc(100vh - 80px);
				background: white;
				backdrop-filter: blur(10px);
				flex-direction: column;
				align-items: flex-start;
				justify-content: flex-start;
				transition: all 0.5s ease;
				padding: 30px 0;
				gap: 10px;
				z-index: 999;
				border-left: 1px solid rgba(0, 0, 0, 0.1);

				li {
					width: 100%;
					padding: 5px 10px;

					a {
						display: flex;
						align-items: center;
						justify-content: space-between;
						width: 100%;
						padding: 6px 1.5rem;
					}
				}
			}
		}

		@media (max-width: 480px) {
			.logo {
				.logo-link {
					.logo-img {
						width: 40px;
						height: 40px;
					}
				}

				.username {
					font-size: 0.9rem;
				}
			}

			.menulist {
				width: 80%;
			}
		}
	}

	.footer {
		background-color: #f3eeea;

		.footer-content {
			max-width: 1200px;
			margin: 0 auto;
			padding: 0 2rem;
		}

		.footer-top {
			display: grid;
			grid-template-columns: 1fr 2fr;
			gap: 3rem;
			padding: 3rem 0;
			border-bottom: 1px solid rgba(0, 0, 0, 0.1);

			@media (max-width: 768px) {
				grid-template-columns: 1fr;
				gap: 2rem;
				text-align: center;
			}
		}

		.footer-brand {
			h3 {
				font-size: 1.5rem;
				margin-bottom: 1rem;
				color: #2c3e50;
				font-weight: 600;
			}

			p {
				color: #6c757d;
				line-height: 1.6;
				margin-bottom: 1.5rem;
				font-size: 0.95rem;
			}

			.social-links {
				display: flex;
				gap: 1rem;

				@media (max-width: 768px) {
					justify-content: center;
				}

				a {
					display: flex;
					align-items: center;
					justify-content: center;
					width: 40px;
					height: 40px;
					background: #fff;
					border-radius: 50%;
					color: #6c757d;
					text-decoration: none;
					transition: all 0.3s ease;
					box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

					&:hover {
						background: #314438;
						color: #fff;
						transform: translateY(-2px);
						box-shadow: 0 4px 8px rgba(0, 123, 255, 0.3);
					}
				}
			}
		}

		.footer-links {
			display: grid;
			grid-template-columns: repeat(4, 1fr);
			gap: 2rem;

			@media (max-width: 768px) {
				grid-template-columns: repeat(2, 1fr);
				gap: 1.5rem;
			}

			@media (max-width: 480px) {
				grid-template-columns: 1fr;
			}
		}

		.footer-column {
			h4 {
				font-size: 1.1rem;
				margin-bottom: 1rem;
				color: #2c3e50;
				font-weight: 600;
			}

			ul {
				list-style: none;
				padding: 0;

				li {
					margin-bottom: 0.5rem;

					a {
						color: #6c757d;
						text-decoration: none;
						font-size: 0.9rem;
						transition: color 0.3s ease;

						&:hover {
							text-decoration: underline;
						}
					}
				}
			}
		}

		.footer-bottom {
			padding: 1.5rem 0;

			.footer-bottom-content {
				display: flex;
				justify-content: space-between;
				align-items: center;

				@media (max-width: 768px) {
					flex-direction: column;
					gap: 1rem;
					text-align: center;
				}

				p {
					font-size: 0.85rem;
					color: #6c757d;
					margin: 0;
				}
			}
		}
	}
</style>
