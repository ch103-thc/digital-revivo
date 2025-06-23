<script>
    const serumCards = [
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
            image: "/img/boj/calming-serum-green-tea-panthenol.jpg",
            title: "Beauty of Joseon Calming Serum Green Tea + Panthenol",
            price: "$16.90",
            numericPrice: 16.9,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3FNrfeB",
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
            image: "/img/boj/ginseng-essence-water.jpg",
            title: "Beauty of Joseon Ginseng Essence Water",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3XY9Sy0",
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
            image: "/img/cosrx/niacinamide-15-peptide-booster-set.jpg",
            title: "COSRX Niacinamide 15% Peptide Booster Set",
            price: "$35.00",
            numericPrice: 35.0,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/4kof5se",
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
            image: "/img/cosrx/full-fit-propolis-light-ampoule.jpg",
            title: "COSRX Full Fit Propolis Light Ampoule",
            price: "$19.40",
            numericPrice: 19.4,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/41VQfYE",
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
            image: "/img/anua/peach-70-niacinamide-serum.jpg",
            title: "ANUA Peach 70 Niacinamide Serum",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Face Serums",
            brand: "ANUA",
            link: "https://amzn.to/4iRguGw",
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
    ];

    // Filter and sort state
    let selectedPriceRange = "all";
    let selectedBrand = "all";
    let selectedCategory = "all";
    let sortBy = "default";

    // Extract unique brands from serums - now using the brand property
    const brands = [...new Set(serumCards.map((card) => card.brand))].sort();

    // Extract unique categories from serums
    const categories = [...new Set(serumCards.map((card) => card.category))];

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
    $: filteredProducts = serumCards
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

<section class="serums-page">
    <!-- Breadcrumb Navigation -->
    <nav class="breadcrumb">
        <a href="/">Home</a>
        <span class="separator">/</span>
        <a href="/collections">Collections</a>
        <span class="separator">/</span>
        <span class="current">Face Serums</span>
    </nav>

    <!-- Page Title -->
    <div class="header-section">
        <h1>Face Serums</h1>
        <p class="product-count">
            {#if hasActiveFilters}
                {sortedProducts.length} of {serumCards.length} products
            {:else}
                {serumCards.length} products
            {/if}
        </p>
    </div>

    <!-- Description Text -->
    <div class="description">
        <p>
            Serums, treatment liquids (essence) and ampoules contain active
            ingredients that are absorbed deep into the skin and care for the
            skin from the inside.
        </p>
        <p>
            Apply essence after toner, before an ampoule or a serum. Serums and
            ampoules are added after toner or essence, if such is part of your
            skin care routine. Serums and ampoules are always added before
            moisturizer.
        </p>
        <p>
            If you use several different serums and ampoules in your routine,
            add the products starting from the most liquid consistency and end
            with product with thickest consistency.
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
    .serums-page {
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

        .description {
            max-width: 1000px;
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
            grid-template-columns: repeat(1, 1fr);
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
