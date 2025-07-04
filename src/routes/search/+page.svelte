<script>
    import { page } from "$app/stores";
    import { onMount } from "svelte";
    import Icon from "@iconify/svelte";

    // Fake static data to search from
    const allProducts = [
        {
            image: "/img/cosrx/low-pH-good-morning-gel-cleanser.jpg",
            title: "COSRX Low pH Good Morning Gel Cleanser",
            price: "$11.90",
            numericPrice: 11.9,
            category: "Face Cleansers",
            brand: "COSRX",
            link: "https://amzn.to/3FwFWTf",
        },
        {
            image: "/img/cosrx/full-fit-propolis-light-cream.jpg",
            title: "COSRX Full Fit Propolis Light Cream",
            price: "$23.00",
            numericPrice: 23.0,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/3FDqMMg",
        },
        {
            image: "/img/cosrx/oil-free-ultra-moisturizing-lotion-with-birch-sap.jpg",
            title: "COSRX Oil Free Ultra Moisturizing Lotion with Birch Sap",
            price: "$18.70",
            numericPrice: 18.7,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/4hiSmeT",
        },
        {
            image: "/img/cosrx/hyaluronic-acid-intensive-cream.jpg",
            title: "COSRX Hyaluronic Acid Intensive Cream",
            price: "$20.50",
            numericPrice: 20.5,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/3DwI2lK",
        },
        {
            image: "/img/cosrx/advanced-snail-92-all-in-one-cream.jpg",
            title: "COSRX Advanced Snail 92 All In One Cream",
            price: "$20.50",
            numericPrice: 20.5,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/3Fy8CM9",
        },
        {
            image: "/img/cosrx/ultimate-nourishing-rice-overnight-spa-mask.jpg",
            title: "COSRX Ultimate Nourishing Rice Overnight Spa Mask",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Masks & Exfoliators",
            brand: "COSRX",
            link: "https://amzn.to/41A59Un",
        },
        {
            image: "/img/cosrx/niacinamide-15-peptide-booster-set.jpg",
            title: "COSRX Niacinamide 15% Peptide Booster Set",
            price: "$35.00",
            numericPrice: 35.0,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/4kof5se",
        },
        {
            image: "/img/cosrx/the-niacinamide-15-serum.jpg",
            title: "COSRX The Niacinamide 15 Serum",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/4bFyC3U",
        },
        {
            image: "/img/cosrx/acne-pimple-master-patch.jpg",
            title: "COSRX Acne Pimple Master Patch",
            price: "$12.30",
            numericPrice: 12.3,
            category: "Acne Patches",
            brand: "COSRX",
            link: "https://amzn.to/4hG4eYm",
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
            image: "/img/cosrx/full-fit-propolis-light-ampoule.jpg",
            title: "COSRX Full Fit Propolis Light Ampoule",
            price: "$19.40",
            numericPrice: 19.4,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/41VQfYE",
        },
        {
            image: "/img/cosrx/the-vitamin-C-23-serum.jpg",
            title: "COSRX The Vitamin C 23 Serum",
            price: "$19.90",
            numericPrice: 19.9,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/4iolfru",
        },
        {
            image: "/img/cosrx/the-retinol-0.3-cream.jpg",
            title: "COSRX The Retinol 0.3 Cream",
            price: "$21.00",
            numericPrice: 21.0,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/41E2Yiz",
        },
        {
            image: "/img/cosrx/the-retinol-0.5-oil.jpg",
            title: "COSRX The Retinol 0.5 Oil",
            price: "$20.50",
            numericPrice: 20.5,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/3RhgO5z",
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
        {
            image: "/img/cosrx/hyaluronic-acid-hydra-power-essence.jpg",
            title: "COSRX Hyaluronic Acid Hydra Power Essence",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/4hC3R0X",
        },
        {
            image: "/img/cosrx/advanced-snail-96-mucin-power-essence.jpg",
            title: "COSRX Advanced Snail 96 Mucin Power Essence",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/3HluISH",
        },
        {
            image: "/img/cosrx/advanced-snail-mucin-glass-glow-hydrogel-mask.jpg",
            title: "COSRX Advanced Snail Mucin Glass Glow Hydrogel Mask",
            price: "$15.00",
            numericPrice: 15.0,
            category: "Masks & Exfoliators",
            brand: "COSRX",
            link: "https://amzn.to/41Q5vWV",
        },
        {
            image: "/img/cosrx/the-peptide-collagen-hydrogel-eye-patch.jpg",
            title: "COSRX The Peptide Collagen Hydrogel Eye Patch",
            price: "$23.00",
            numericPrice: 23.0,
            category: "Eye Care",
            brand: "COSRX",
            link: "https://amzn.to/3T1o6eF",
        },
        {
            image: "/img/anua/heartleaf-70-intense-calming-cream.jpg",
            title: "ANUA Heartleaf 70 Intense Calming Cream",
            price: "$25.00",
            numericPrice: 25.0,
            category: "Moisturizers",
            brand: "ANUA",
            link: "https://amzn.to/3DQzS7N",
        },
        {
            image: "/img/anua/heartleaf-daily-lotion.jpg",
            title: "ANUA Heartleaf Daily Lotion",
            price: "$24.90",
            numericPrice: 24.9,
            category: "Moisturizers",
            brand: "ANUA",
            link: "https://amzn.to/42eNvXy",
        },
        {
            image: "/img/anua/rice-70-intensive-moisturizing-milk.jpg",
            title: "ANUA Rice 70 Intensive Moisturizing Milk",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Moisturizers",
            brand: "ANUA",
            link: "https://amzn.to/3FE5A8Y",
        },
        {
            image: "/img/anua/3-ceramide-panthenol-moisture-barrier-cream.jpg",
            title: "ANUA 3 Ceramide Panthenol Moisture Barrier Cream",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Moisturizers",
            brand: "ANUA",
            link: "https://amzn.to/4bD1GJg",
        },
        {
            image: "/img/anua/heartleaf-pore-control-cleansing-oil.jpg",
            title: "ANUA Heartleaf Pore Control Cleansing Oil",
            price: "$17.70",
            numericPrice: 17.7,
            category: "Face Cleansers",
            brand: "ANUA",
            link: "https://amzn.to/4iAM6QS",
        },
        {
            image: "/img/anua/heartleaf-quercetinol-pore-deep-cleansing-foam.jpg",
            title: "ANUA Heartleaf Quercetinol Pore Deep Cleansing Foam",
            price: "$13.00",
            numericPrice: 13.0,
            category: "Face Cleansers",
            brand: "ANUA",
            link: "https://amzn.to/4c0fg9B",
        },
        {
            image: "/img/anua/rice-enzyme-brightening-cleansing-powder.jpg",
            title: "ANUA Rice Enzyme Brightening Cleansing Powder",
            price: "$15.90",
            numericPrice: 15.9,
            category: "Face Cleansers",
            brand: "ANUA",
            link: "https://amzn.to/3DAIE9Z",
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
            image: "/img/anua/niacinamide-10-txa-4-serum.jpg",
            title: "Anua Niacinamide 10 + TXA 4 Serum",
            price: "$22.00",
            numericPrice: 22.0,
            category: "Face Serums",
            brand: "ANUA",
            link: "https://amzn.to/4bD41E0",
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
            image: "/img/anua/heartleaf-silky-moisture-mild-sunscreen.jpg",
            title: "ANUA Heartleaf Silky Moisture Mild Sunscreen",
            price: "$23.00",
            numericPrice: 23.0,
            category: "Sunscreen",
            brand: "ANUA",
            link: "https://amzn.to/4hGmdhe",
        },
        {
            image: "/img/anua/peach-70-niacinamide-serum.jpg",
            title: "ANUA Peach 70 Niacinamide Serum",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Face Serums",
            brand: "ANUA",
            link: "https://amzn.to/4iRguGw",
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
            image: "/img/anua/rice-70-glow-milky-toner.jpg",
            title: "ANUA Rice 70 Glow Milky Toner",
            price: "$21.00",
            numericPrice: 21.0,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/3DCoBbc",
        },
        {
            image: "/img/anua/rice-ceramide-7-hydrating-barrier-serum.jpg",
            title: "ANUA Rice Ceramide 7 Hydrating Barrier Serum",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Face Serums",
            brand: "ANUA",
            link: "https://amzn.to/3DAPqMX",
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
            image: "/img/boj/dynasty-cream.jpg",
            title: "Beauty of Joseon Dynasty Cream",
            price: "$23.00",
            numericPrice: 23.0,
            category: "Moisturizers",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/41HLxOi",
        },
        {
            image: "/img/boj/ginseng-cleansing-oil.jpg",
            title: "Beauty of Joseon Ginseng Cleansing Oil",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Face Cleansers",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3DS8Blj",
        },
        {
            image: "/img/boj/glow-deep-serum-rice-alpha-arbutin.jpg",
            title: "Beauty of Joseon Glow Deep Serum Rice + Alpha-Arbutin",
            price: "$16.50",
            numericPrice: 16.5,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3Rnjsqp",
        },
        {
            image: "/img/boj/green-plum-refreshing-cleanser.jpg",
            title: "Beauty of Joseon Green Plum Refreshing Cleanser",
            price: "$13.00",
            numericPrice: 13.0,
            category: "Face Cleansers",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4iwoqwL",
        },
        {
            image: "/img/boj/ground-rice-and-honey-glow-mask.jpg",
            title: "Beauty of Joseon Ground Rice and Honey Glow Mask",
            price: "$18.00",
            numericPrice: 18.0,
            category: "Masks & Exfoliators",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3DCFJ0x",
        },
        {
            image: "/img/boj/red-bean-water-gel.jpg",
            title: "Beauty of Joseon Red Bean Water Gel",
            price: "$16.90",
            numericPrice: 16.9,
            category: "Moisturizers",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4bDWrZZ",
        },
        {
            image: "/img/boj/revive-eye-serum.jpg",
            title: "Beauty of Joseon Revive Eye Serum",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Eye Care",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4bYhRRr",
        },
        {
            image: "/img/boj/apricot-blossom-peeling-gel.jpg",
            title: "Beauty of Joseon Apricot Blossom Peeling Gel",
            price: "$13.00",
            numericPrice: 13.0,
            category: "Masks & Exfoliators",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3DDz8mt",
        },
        {
            image: "/img/boj/calming-serum-green-tea-panthenol.jpg",
            title: "Beauty of Joseon Calming Serum Green Tea + Panthenol",
            price: "$16.90",
            numericPrice: 16.9,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3FNrfeB",
        },
        {
            image: "/img/boj/ginseng-essence-water.jpg",
            title: "Beauty of Joseon Ginseng Essence Water",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3XY9Sy0",
        },
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
            image: "/img/boj/light-on-serum-centella-vita-c.jpg",
            title: "Beauty of Joseon Light On Serum Centella + Vita C",
            price: "$16.40",
            numericPrice: 16.4,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4bzxpLt",
        },
        {
            image: "/img/boj/red-bean-refreshing-pore-mask.jpg",
            title: "Beauty of Joseon Red Bean Refreshing Pore Mask",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Masks & Exfoliators",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4kCklZS",
        },
    ];

    // State variables
    let searchQuery = $state("");
    let results = $state([]);
    let filteredResults = $state([]);

    // Filter and sort state
    let selectedBrand = $state("all");
    let selectedCategory = $state("all");
    let selectedPriceRange = $state("all");
    let sortBy = $state("relevance");
    let showFilters = $state(false);

    // Extract unique values for filters
    const brands = [...new Set(allProducts.map((p) => p.brand))].sort();
    const categories = [...new Set(allProducts.map((p) => p.category))].sort();
    const priceRanges = [
        { label: "Under $15", min: 0, max: 15 },
        { label: "$15 - $20", min: 15, max: 20 },
        { label: "$20 - $25", min: 20, max: 25 },
        { label: "Over $25", min: 25, max: 999 },
    ];

    // Apply filters and sorting
    function applyFiltersAndSort() {
        let filtered = [...results];

        // Apply brand filter
        if (selectedBrand !== "all") {
            filtered = filtered.filter(
                (product) => product.brand === selectedBrand,
            );
        }

        // Apply category filter
        if (selectedCategory !== "all") {
            filtered = filtered.filter(
                (product) => product.category === selectedCategory,
            );
        }

        // Apply price range filter
        if (selectedPriceRange !== "all") {
            const range = priceRanges.find(
                (r) => r.label === selectedPriceRange,
            );
            if (range) {
                filtered = filtered.filter(
                    (product) =>
                        product.numericPrice >= range.min &&
                        product.numericPrice <= range.max,
                );
            }
        }

        // Apply sorting
        switch (sortBy) {
            case "price-low":
                filtered.sort((a, b) => a.numericPrice - b.numericPrice);
                break;
            case "price-high":
                filtered.sort((a, b) => b.numericPrice - a.numericPrice);
                break;
            case "name-az":
                filtered.sort((a, b) => a.title.localeCompare(b.title));
                break;
            case "name-za":
                filtered.sort((a, b) => b.title.localeCompare(a.title));
                break;
            case "relevance":
            default:
                // Keep original search relevance order
                break;
        }

        filteredResults = filtered;
    }

    // Clear all filters
    function clearFilters() {
        selectedBrand = "all";
        selectedCategory = "all";
        selectedPriceRange = "all";
        sortBy = "relevance";
        applyFiltersAndSort();
    }

    function hasActiveFilters() {
        return (
            selectedBrand !== "all" ||
            selectedCategory !== "all" ||
            selectedPriceRange !== "all" ||
            sortBy !== "relevance"
        );
    }

    // Get active filter count
    function getActiveFilterCount() {
        let count = 0;
        if (selectedBrand !== "all") count++;
        if (selectedCategory !== "all") count++;
        if (selectedPriceRange !== "all") count++;
        return count;
    }

    onMount(() => {
        // Get initial search query from URL
        const urlParams = new URLSearchParams(window.location.search);
        const query = urlParams.get("q") || "";
        searchQuery = query;

        if (query) {
            results = allProducts.filter((product) =>
                product.title.toLowerCase().includes(query.toLowerCase()),
            );
            applyFiltersAndSort();
        }

        // Subscribe to page store changes
        const unsubscribe = page.subscribe(($page) => {
            const newQuery = $page.url.searchParams.get("q") || "";
            if (newQuery !== searchQuery) {
                searchQuery = newQuery;
                if (newQuery) {
                    results = allProducts.filter((product) =>
                        product.title
                            .toLowerCase()
                            .includes(newQuery.toLowerCase()),
                    );
                    applyFiltersAndSort();
                } else {
                    results = [];
                    filteredResults = [];
                }
            }
        });

        return unsubscribe;
    });

    // Reactive statements to update filtered results when filters change
    $effect(() => {
        applyFiltersAndSort();
    });
</script>

<section class="search-page">
    <!-- Breadcrumb Navigation -->
    <nav class="breadcrumb">
        <a href="/">Home</a>
        <span class="separator">/</span>
        <span class="search-crumb">
            {#if searchQuery}
                Search results for "{searchQuery}"
            {:else}
                Search
            {/if}
        </span>
    </nav>

    <div class="search-header">
        <h1>Search Results</h1>
        {#if searchQuery}
            <p class="search-info">Results for "{searchQuery}"</p>
        {/if}
        <p class="product-count">
            {#if hasActiveFilters() && filteredResults.length !== results.length}
                {filteredResults.length} of {results.length} product{results.length !==
                1
                    ? "s"
                    : ""} found
            {:else}
                {filteredResults.length} product{filteredResults.length !== 1
                    ? "s"
                    : ""} found
            {/if}
        </p>
    </div>

    {#if !searchQuery}
        <div class="no-search">
            <p>Enter a search term to find products.</p>
        </div>
    {:else if results.length === 0}
        <div class="no-results">
            <p>No products found matching "{searchQuery}".</p>
            <p>Try searching for different keywords or check your spelling.</p>
        </div>
    {:else}
        <div class="filters-section">
            <h2 class="filters-title">Filter:</h2>
            <div class="filters-controls">
                <div class="filter-group">
                    <label for="category">Category</label>
                    <select id="category" bind:value={selectedCategory}>
                        <option value="all">All Categories</option>
                        {#each categories as category}
                            <option value={category}>{category}</option>
                        {/each}
                    </select>
                </div>

                <div class="filter-group">
                    <label for="brand">Brand</label>
                    <select id="brand" bind:value={selectedBrand}>
                        <option value="all">All Brands</option>
                        {#each brands as brand}
                            <option value={brand}>{brand}</option>
                        {/each}
                    </select>
                </div>

                <div class="filter-group">
                    <label for="price-range">Price Range</label>
                    <select id="price-range" bind:value={selectedPriceRange}>
                        <option value="all">All Prices</option>
                        {#each priceRanges as range}
                            <option value={range.label}>{range.label}</option>
                        {/each}
                    </select>
                </div>

                <div class="filter-group">
                    <label for="sort-by">Sort By</label>
                    <select id="sort-by" bind:value={sortBy}>
                        <option value="relevance">Relevance</option>
                        <option value="price-low">Price: Low to High</option>
                        <option value="price-high">Price: High to Low</option>
                        <option value="name-az">Name: A-Z</option>
                        <option value="name-za">Name: Z-A</option>
                    </select>
                </div>

                {#if getActiveFilterCount() > 0}
                    <div class="clear-filters-section">
                        <button class="clear-filters" on:click={clearFilters}>
                            Clear All Filters ({getActiveFilterCount()})
                        </button>
                    </div>
                {/if}
            </div>
        </div>

        <!-- Results Grid -->
        {#if filteredResults.length === 0}
            <div class="no-results">
                <p>No products match your current filters.</p>
                <button on:click={clearFilters}>Clear Filters</button>
            </div>
        {:else}
            <div class="cards-grid">
                {#each filteredResults as product}
                    <a
                        href={product.link}
                        class="info-card"
                        target="_blank"
                        rel="noopener"
                    >
                        <div class="image-wrapper">
                            <img src={product.image} alt={product.title} />
                            <div class="product-badge">
                                {product.brand}
                            </div>
                        </div>
                        <div class="info-card-content">
                            <div class="product-category">
                                {product.category}
                            </div>
                            <h3>{product.title}</h3>
                            <p class="price">{product.price}</p>
                            <span class="buy-button">Buy now</span>
                        </div>
                    </a>
                {/each}
            </div>
        {/if}
    {/if}
</section>

<style lang="scss">
    .search-page {
        padding: 7rem 1.5rem;
        background-color: #f3eeea;
        min-height: 100vh;

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

            .search-crumb {
                color: #314438;
                font-weight: 500;
            }
        }

        .search-header {
            text-align: left;
            max-width: 1140px;
            margin: 0 auto 2rem;

            h1 {
                font-size: 2rem;
                margin-bottom: 0.5rem;
            }

            .search-info {
                font-size: 1.1rem;
                color: #374151;
                margin-bottom: 1rem;
                font-weight: 500;
            }

            .product-count {
                font-size: 1rem;
                color: #6b7280;
                margin: 0;
            }
        }

        .no-search,
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
                text-decoration: none;
                color: inherit;
                position: relative;

                .image-wrapper {
                    width: 100%;
                    height: 250px;
                    overflow: hidden;
                    border-radius: 0.5rem;
                    position: relative;

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

                    .product-badge {
                        position: absolute;
                        top: 0.5rem;
                        left: 0.5rem;
                        background-color: rgba(0, 0, 0, 0.7);
                        color: white;
                        padding: 0.25rem 0.5rem;
                        border-radius: 0.25rem;
                        font-size: 0.75rem;
                        font-weight: 500;
                    }
                }

                .info-card-content {
                    display: flex;
                    flex-direction: column;
                    flex: 1;
                    padding: 1rem;

                    .product-category {
                        font-size: 0.75rem;
                        color: #6b7280;
                        text-transform: uppercase;
                        letter-spacing: 0.05em;
                        margin-bottom: 0.5rem;
                    }

                    h3 {
                        font-weight: 600;
                        color: #1f2937;
                        margin-bottom: 0.5rem;
                    }

                    .price {
                        font-size: 0.85rem;
                        color: #6b7280;
                        margin: 0.25rem 0 1rem 0;
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
    }
</style>
