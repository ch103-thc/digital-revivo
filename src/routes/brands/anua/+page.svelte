<script>
    const productCards = [
        {
            image: "/img/anua/heartleaf-70-intense-calming-cream.jpg",
            title: "ANUA Heartleaf 70 Intense Calming Cream",
            price: "$25.00",
            numericPrice: 25.0,
            category: "Moisturizers",
            link: "https://amzn.to/3DQzS7N",
        },
        {
            image: "/img/anua/heartleaf-daily-lotion.jpg",
            title: "ANUA Heartleaf Daily Lotion",
            price: "$24.90",
            numericPrice: 24.9,
            category: "Moisturizers",
            link: "https://amzn.to/42eNvXy",
        },
        {
            image: "/img/anua/rice-70-intensive-moisturizing-milk.jpg",
            title: "ANUA Rice 70 Intensive Moisturizing Milk",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Moisturizers",
            link: "https://amzn.to/3FE5A8Y",
        },
        {
            image: "/img/anua/3-ceramide-panthenol-moisture-barrier-cream.jpg",
            title: "ANUA 3 Ceramide Panthenol Moisture Barrier Cream",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Moisturizers",
            link: "https://amzn.to/4bD1GJg",
        },
        {
            image: "/img/anua/heartleaf-pore-control-cleansing-oil.jpg",
            title: "ANUA Heartleaf Pore Control Cleansing Oil",
            price: "$17.70",
            numericPrice: 17.7,
            category: "Face Cleansers",
            link: "https://amzn.to/4iAM6QS",
        },
        {
            image: "/img/anua/heartleaf-quercetinol-pore-deep-cleansing-foam.jpg",
            title: "ANUA Heartleaf Quercetinol Pore Deep Cleansing Foam",
            price: "$13.00",
            numericPrice: 13.0,
            category: "Face Cleansers",
            link: "https://amzn.to/4c0fg9B",
        },
        {
            image: "/img/anua/rice-enzyme-brightening-cleansing-powder.jpg",
            title: "ANUA Rice Enzyme Brightening Cleansing Powder",
            price: "$15.90",
            numericPrice: 15.9,
            category: "Face Cleansers",
            link: "https://amzn.to/3DAIE9Z",
        },
        {
            image: "/img/anua/heartleaf-77-soothing-toner.jpg",
            title: "Anua Heartleaf 77 Soothing Toner",
            price: "$19.70",
            numericPrice: 19.7,
            category: "Toners",
            link: "https://amzn.to/3Fz3KGg",
        },
        {
            image: "/img/anua/niacinamide-10-txa-4-serum.jpg",
            title: "Anua Niacinamide 10 + TXA 4 Serum",
            price: "$22.00",
            numericPrice: 22.0,
            category: "Face Serums",
            link: "https://amzn.to/4bD41E0",
        },
        {
            image: "/img/anua/heartleaf-77-toner-pad.jpg",
            title: "ANUA Heartleaf 77 Toner Pad",
            price: "$22.00",
            numericPrice: 22.0,
            category: "Toners",
            link: "https://amzn.to/43QYo34",
        },
        {
            image: "/img/anua/heartleaf-silky-moisture-mild-sunscreen.jpg",
            title: "ANUA Heartleaf Silky Moisture Mild Sunscreen",
            price: "$23.00",
            numericPrice: 23.0,
            category: "Sunscreen",
            link: "https://amzn.to/4hGmdhe",
        },
        {
            image: "/img/anua/peach-70-niacinamide-serum.jpg",
            title: "ANUA Peach 70 Niacinamide Serum",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Face Serums",
            link: "https://amzn.to/4iRguGw",
        },
        {
            image: "/img/anua/peach-77-niacin-essence-toner.jpg",
            title: "ANUA Peach 77 Niacin Essence Toner",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Toners",
            link: "https://amzn.to/3DNc4BH",
        },
        {
            image: "/img/anua/rice-70-glow-milky-toner.jpg",
            title: "ANUA Rice 70 Glow Milky Toner",
            price: "$21.00",
            numericPrice: 21.0,
            category: "Toners",
            link: "https://amzn.to/3DCoBbc",
        },
        {
            image: "/img/anua/rice-ceramide-7-hydrating-barrier-serum.jpg",
            title: "ANUA Rice Ceramide 7 Hydrating Barrier Serum",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Face Serums",
            link: "https://amzn.to/3DAPqMX",
        },
        {
            image: "/img/anua/bha-2-gentle-exfoliating-toner.jpg",
            title: "ANUA BHA 2% Gentle Exfoliating Toner",
            price: "$18.00",
            numericPrice: 18.0,
            category: "Toners",
            link: "https://amzn.to/43Ufkps",
        },
    ];

    // Filter and sort state
    let selectedPriceRange = "all";
    let selectedCategory = "all";
    let sortBy = "default";

    // Price ranges
    const priceRanges = [
        { value: "all", label: "All Prices" },
        { value: "under-15", label: "Under $15" },
        { value: "15-20", label: "$15 - $20" },
        { value: "20-25", label: "$20 - $25" },
        { value: "over-25", label: "Over $25" },
    ];

    // Categories
    const categories = [
        { value: "all", label: "All Categories" },
        { value: "Face Cleansers", label: "Face Cleansers" },
        { value: "Moisturizers", label: "Moisturizers" },
        { value: "Toners", label: "Toners" },
        { value: "Face Serums", label: "Face Serums" },
        { value: "Masks & Exfoliators", label: "Masks & Exfoliators" },
        { value: "Acne Patches", label: "Acne Patches" },
        { value: "Sunscreen", label: "Sunscreen" },
        { value: "Eye Care", label: "Eye Care" },
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
            case "20-25":
                return price > 20 && price <= 25;
            case "over-25":
                return price > 25;
            default:
                return true;
        }
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
    $: filteredProducts = productCards
        .filter((product) => filterByPrice(product, selectedPriceRange))
        .filter((product) => filterByCategory(product, selectedCategory));

    $: sortedProducts = sortProducts(filteredProducts, sortBy);

    // Clear filters function
    function clearFilters() {
        selectedPriceRange = "all";
        selectedCategory = "all";
        sortBy = "default";
    }

    // Count active filters
    $: activeFiltersCount =
        (selectedPriceRange !== "all" ? 1 : 0) +
        (selectedCategory !== "all" ? 1 : 0);

    // Determine if filters are active
    $: hasActiveFilters =
        selectedPriceRange !== "all" || selectedCategory !== "all";
</script>

<section class="products-page">
    <!-- Breadcrumb Navigation -->
    <nav class="breadcrumb">
        <a href="/">Home</a>
        <span class="separator">/</span>
        <a href="/brands">Brands</a>
        <span class="separator">/</span>
        <span class="current">ANUA</span>
    </nav>
    <div class="header-section">
        <h1>ANUA</h1>
        <p class="product-count">
            {#if hasActiveFilters}
                {sortedProducts.length} of {productCards.length} products
            {:else}
                {productCards.length} products
            {/if}
        </p>
    </div>

    <!-- Filters Section -->
    <div class="filters-section">
        <h2 class="filters-title">Filter:</h2>
        <div class="filters-controls">
            <div class="filter-group">
                <label for="category">Category</label>
                <select id="category" bind:value={selectedCategory}>
                    {#each categories as category}
                        <option value={category.value}>{category.label}</option>
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

    <!-- Products Grid -->
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
    .products-page {
        padding: 7rem 1.5rem;
        background-color: #f3eeea;

        .breadcrumb {
            text-align: left;
            max-width: 1000px;
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
            max-width: 1000px;
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

        .filters-section {
            max-width: 1000px;
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
                    // flex: 1;

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
                    }
                }
            }
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.5rem;
            max-width: 1000px;
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
