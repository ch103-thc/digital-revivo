<script>
    const tonerCards = [
        {
            image: "/img/boj/glow-replenishing-rice-milk.jpg",
            title: "Beauty of Joseon Glow Replenishing Rice Milk",
            price: "$18.00",
            numericPrice: 18.0,
            category: "Toners",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4kYLh67",
        },
        {
            image: "/img/cosrx/full-fit-propolis-synergy-toner.jpg",
            title: "COSRX Full Fit Propolis Synergy Toner",
            price: "$20.50",
            numericPrice: 20.5,
            category: "Toners",
            brand: "COSRX",
            link: "https://amzn.to/4kD6nH3",
        },
        {
            image: "/img/anua/heartleaf-77-soothing-toner.jpg",
            title: "Anua Heartleaf 77 Soothing Toner",
            price: "$19.70",
            numericPrice: 19.7,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/3Fz3KGg",
        },
        {
            image: "/img/anua/rice-70-glow-milky-toner.jpg",
            title: "ANUA Rice 70 Glow Milky Toner",
            price: "$21.00",
            numericPrice: 21.0,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/3DCoBbc",
        },
        {
            image: "/img/anua/peach-77-niacin-essence-toner.jpg",
            title: "ANUA Peach 77 Niacin Essence Toner",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/3DNc4BH",
        },
        {
            image: "/img/anua/bha-2-gentle-exfoliating-toner.jpg",
            title: "ANUA BHA 2% Gentle Exfoliating Toner",
            price: "$18.00",
            numericPrice: 18.0,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/43Ufkps",
        },
        {
            image: "/img/anua/heartleaf-77-toner-pad.jpg",
            title: "ANUA Heartleaf 77 Toner Pad",
            price: "$22.00",
            numericPrice: 22.0,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/43QYo34",
        },
        {
            image: "/img/cosrx/aha-bha-clarifying-treatment-toner.jpg",
            title: "COSRX AHA/BHA Clarifying Treatment Toner",
            price: "$15.20",
            numericPrice: 15.2,
            category: "Toners",
            brand: "COSRX",
            link: "https://amzn.to/4izP1cA",
        },
    ];

    // Filter and sort state
    let selectedPriceRange = "all";
    let selectedBrand = "all";
    let selectedCategory = "all";
    let sortBy = "default";

    // Extract unique brands from toners - now using the brand property
    const brands = [...new Set(tonerCards.map((card) => card.brand))].sort();

    // Extract unique categories from toners
    const categories = [...new Set(tonerCards.map((card) => card.category))];

    // Price ranges
    const priceRanges = [
        { value: "all", label: "All Prices" },
        { value: "under-15", label: "Under $15" },
        { value: "15-20", label: "$15 - $20" },
        { value: "20-25", label: "$20 - $25" },
        { value: "over-20", label: "Over $20" },
    ];

    // Brand options
    const brandOptions = [
        { value: "all", label: "All Brands" },
        ...brands.map((brand) => ({ value: brand, label: brand })),
    ];

    // Category options
    const categoryOptions = [
        { value: "all", label: "All Categories" },
        ...categories.map((category) => ({ value: category, label: category })),
    ];

    // Sort options
    const sortOptions = [
        { value: "default", label: "Default" },
        { value: "price-low-high", label: "Price: Low to High" },
        { value: "price-high-low", label: "Price: High to Low" },
        { value: "name-a-z", label: "Name: A to Z" },
        { value: "name-z-a", label: "Name: Z to A" },
    ];

    // Filter function
    function filterByPrice(product, range) {
        const price = product.numericPrice;
        switch (range) {
            case "under-15":
                return price < 15;
            case "15-20":
                return price >= 15 && price <= 20;
            case "over-20":
                return price > 20;
            default:
                return true;
        }
    }

    // Updated brand filter function to match search page
    function filterByBrand(product, brand) {
        return brand === "all" || product.brand === brand;
    }

    function filterByCategory(product, category) {
        return category === "all" || product.category === category;
    }

    // Sort function
    function sortProducts(products, sortBy) {
        const sorted = [...products];
        switch (sortBy) {
            case "price-low-high":
                return sorted.sort((a, b) => a.numericPrice - b.numericPrice);
            case "price-high-low":
                return sorted.sort((a, b) => b.numericPrice - a.numericPrice);
            case "name-a-z":
                return sorted.sort((a, b) => a.title.localeCompare(b.title));
            case "name-z-a":
                return sorted.sort((a, b) => b.title.localeCompare(a.title));
            default:
                return sorted;
        }
    }

    // Reactive filtered and sorted products
    $: filteredProducts = tonerCards
        .filter((product) => filterByPrice(product, selectedPriceRange))
        .filter((product) => filterByBrand(product, selectedBrand))
        .filter((product) => filterByCategory(product, selectedCategory));

    $: sortedProducts = sortProducts(filteredProducts, sortBy);

    // Clear filters function
    function clearFilters() {
        selectedPriceRange = "all";
        selectedBrand = "all";
        selectedCategory = "all";
        sortBy = "default";
    }

    // Count active filters
    $: activeFiltersCount =
        (selectedPriceRange !== "all" ? 1 : 0) +
        (selectedBrand !== "all" ? 1 : 0) +
        (selectedCategory !== "all" ? 1 : 0);

    // Determine if filters are active
    $: hasActiveFilters =
        selectedPriceRange !== "all" ||
        selectedBrand !== "all" ||
        selectedCategory !== "all";
</script>

<section class="toners-page">
    <!-- Breadcrumb Navigation -->
    <nav class="breadcrumb">
        <a href="/">Home</a>
        <span class="separator">/</span>
        <a href="/collections">Collections</a>
        <span class="separator">/</span>
        <span class="current">Toners</span>
    </nav>

    <!-- Page Title -->
    <div class="header-section">
        <h1>Toners</h1>
        <p class="product-count">
            {#if hasActiveFilters}
                {sortedProducts.length} of {tonerCards.length} products
            {:else}
                {tonerCards.length} products
            {/if}
        </p>
    </div>

    <!-- Description Text -->
    <div class="description">
        <p>
            Korean toners, toner pad and toner mist products. Toner is the first
            moisturizing step in skin care and therefore one of the most
            important. It balances the skin's pH immediately after washing so
            that the skin's protective layer remains strong and the skin can
            fight against bacteria and impurities.
        </p>
        <p>
            Toner protects the skin from feeling dry after washing and helps
            other skin care products absorb better. You can get the most out of
            your moisturizer and lock in as much moisture as possible by first
            applying a toner and immediately following up with a serum and your
            moisturizer. Toner is important for dry skin as it brings moisture
            to the skin, but it is just as important for oily skin as hydrated
            skin needs to produce less sebum to keep the skin tissue elastic,
            and as a result the skin's sebum production is balanced.
        </p>
        <p>
            Toners, like other products, have different consistencies ranging
            from water-like lightweight ones to thicker essences. Toner can also
            be layered if you feel that the hydration provided by one
            application is not enough.
        </p>
        <p>
            At Digital Revivo, we recommend using a cotton pad to only apply
            exfoliating toners containing acids such as AHA, BHA and PHA. Other
            toners can be directly applied with your hands using a gentle
            patting motion. This way, you can save cotton pads, toner and your
            skin from physical exfoliation and possible irritation.
        </p>
    </div>

    <!-- Filters Section -->
    <div class="filters-section">
        <h2 class="filters-title">Filter:</h2>
        <div class="filters-controls">
            <div class="filter-group">
                <label for="category">Category</label>
                <select id="category" bind:value={selectedCategory}>
                    {#each categoryOptions as category}
                        <option value={category.value}>{category.label}</option>
                    {/each}
                </select>
            </div>

            <div class="filter-group">
                <label for="brand">Brand</label>
                <select id="brand" bind:value={selectedBrand}>
                    {#each brandOptions as brand}
                        <option value={brand.value}>{brand.label}</option>
                    {/each}
                </select>
            </div>

            <div class="filter-group">
                <label for="price-range">Price Range</label>
                <select id="price-range" bind:value={selectedPriceRange}>
                    {#each priceRanges as range}
                        <option value={range.value}>{range.label}</option>
                    {/each}
                </select>
            </div>

            <div class="filter-group">
                <label for="sort-by">Sort By</label>
                <select id="sort-by" bind:value={sortBy}>
                    {#each sortOptions as option}
                        <option value={option.value}>{option.label}</option>
                    {/each}
                </select>
            </div>

            {#if activeFiltersCount > 0}
                <div class="clear-filters-section">
                    <button class="clear-filters" on:click={clearFilters}>
                        Clear All Filters ({activeFiltersCount})
                    </button>
                </div>
            {/if}
        </div>
    </div>

    <!-- Product Cards Grid -->
    <div class="cards-grid">
        {#each sortedProducts as card}
            <a
                href={card.link}
                class="info-card"
                target="_blank"
                rel="noopener"
            >
                <div class="image-wrapper">
                    <img src={card.image} alt={card.title} />
                </div>
                <div class="info-card-content">
                    <h3>{card.title}</h3>
                    <p class="price">{card.price}</p>
                    <span class="buy-button">Buy now</span>
                </div>
            </a>
        {/each}
    </div>

    {#if sortedProducts.length === 0}
        <div class="no-results">
            <p>No products match your current filters.</p>
            <button on:click={clearFilters}>Clear Filters</button>
        </div>
    {/if}
</section>

<style lang="scss">
    .toners-page {
        padding: 7rem 1.5rem;
        background-color: #f3eeea;

        .breadcrumb {
            text-align: left;
            max-width: 1140px;
            margin: 0 auto 2rem auto;
            font-size: 0.9rem;
            color: #6b7280;

            a {
                color: #6b7280;
                text-decoration: none;
                transition: color 0.3s;

                &:hover {
                    color: #314438;
                }
            }

            .separator {
                margin: 0 0.5rem;
            }

            .current {
                color: #314438;
                font-weight: 500;
            }
        }

        .header-section {
            max-width: 1140px;
            margin: 0 auto 2rem;
            text-align: left;

            h1 {
                font-size: 2rem;
                margin-bottom: 0.5rem;
            }

            .product-count {
                font-size: 1rem;
                color: #6b7280;
                margin: 0;
            }
        }

        .description {
            max-width: 1140px;
            margin: 0 auto 3rem auto;
            text-align: left;

            p {
                margin-bottom: 1rem;
                line-height: 1.6;
                color: #374151;

                &:last-child {
                    margin-bottom: 0;
                }
            }
        }

        .filters-section {
            max-width: 1140px;
            margin: 0 auto 3rem;

            .filters-title {
                font-size: 1.2rem;
                color: #1f2937;
                margin-bottom: 1rem;
                text-align: left;
            }

            .filters-controls {
                display: flex;
                flex-wrap: wrap;
                gap: 1.5rem;
                align-items: end;

                .filter-group {
                    display: flex;
                    flex-direction: column;
                    gap: 0.5rem;
                    min-width: 200px;

                    label {
                        font-weight: 500;
                        color: #374151;
                        font-size: 0.875rem;
                    }

                    select {
                        padding: 0.75rem;
                        border: 1px solid #d1d5db;
                        border-radius: 0.375rem;
                        background-color: white;
                        font-size: 0.875rem;
                        cursor: pointer;
                        transition:
                            border-color 0.2s,
                            box-shadow 0.2s;

                        &:focus {
                            outline: none;
                            border-color: #314438;
                            box-shadow: 0 0 0 3px rgba(49, 68, 56, 0.1);
                        }

                        &:hover {
                            border-color: #9ca3af;
                        }
                    }
                }

                .clear-filters-section {
                    .clear-filters {
                        padding: 0.75rem 1.5rem;
                        background-color: #314438;
                        color: white;
                        border: none;
                        border-radius: 0.375rem;
                        cursor: pointer;
                        font-size: 0.875rem;
                        font-weight: 600;
                        transition: background-color 0.2s;
                        white-space: nowrap;

                        &:hover {
                            background-color: #1f2937;
                        }
                    }
                }
            }
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.5rem;
            max-width: 1140px;
            margin: 0 auto;

            @media (min-width: 768px) {
                grid-template-columns: repeat(2, 1fr);
            }

            @media (min-width: 1024px) {
                grid-template-columns: repeat(4, 1fr);
            }

            .info-card {
                display: flex;
                flex-direction: column;
                height: 100%;
                border-radius: 0.5rem;
                text-align: left;
                overflow: hidden;

                .image-wrapper {
                    width: 100%;
                    height: 250px;
                    overflow: hidden;
                    border-radius: 0.5rem;

                    img {
                        width: 100%;
                        height: 250px;
                        object-fit: cover;
                        transition: transform 0.4s ease;
                        will-change: transform;

                        &:hover {
                            transform: scale(1.05);
                        }
                    }
                }

                .info-card-content {
                    display: flex;
                    flex-direction: column;
                    flex: 1;
                    padding: 1rem;

                    h3 {
                        font-weight: 600;
                        color: #1f2937;
                    }

                    .price {
                        font-size: 0.85rem;
                        color: #6b7280;
                        margin: 0.25rem 0;
                    }

                    .buy-button {
                        margin-top: auto;
                        display: block;
                        width: 100%;
                        padding: 0.75rem;
                        background-color: #314438;
                        color: white;
                        font-size: 0.9rem;
                        font-weight: 600;
                        border-radius: 9999px;
                        text-align: center;
                        text-decoration: none;
                        transition: all 0.3s;
                        border: 1px solid #314438;

                        &:hover {
                            background-color: transparent;
                            color: #314438;
                        }
                    }
                }
            }
        }

        .no-results {
            text-align: center;
            padding: 3rem 1rem;
            max-width: 500px;
            margin: 0 auto;

            p {
                color: #6b7280;
                margin-bottom: 1rem;
                font-size: 1.125rem;
            }

            button {
                padding: 0.75rem 1.5rem;
                background-color: #314438;
                color: white;
                border: none;
                border-radius: 0.375rem;
                cursor: pointer;
                font-weight: 500;
                transition: background-color 0.2s;

                &:hover {
                    background-color: #1f2937;
                }
            }
        }
    }
</style>
