<script>
    const shopAllCards = [
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
            image: "/img/cosrx/acne-pimple-master-patch.jpg",
            title: "COSRX Acne Pimple Master Patch",
            price: "$12.30",
            numericPrice: 12.3,
            category: "Acne Patches",
            brand: "COSRX",
            link: "https://amzn.to/4hG4eYm",
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
            image: "/img/boj/revive-eye-serum.jpg",
            title: "Beauty of Joseon Revive Eye Serum",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Eye Care",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4bYhRRr",
        },
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
            image: "/img/cosrx/advanced-snail-92-all-in-one-cream.jpg",
            title: "COSRX Advanced Snail 92 All In One Cream",
            price: "$20.50",
            numericPrice: 20.5,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/3Fy8CM9",
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
            image: "/img/cosrx/full-fit-propolis-light-ampoule.jpg",
            title: "COSRX Full Fit Propolis Light Ampoule",
            price: "$19.40",
            numericPrice: 19.4,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/41VQfYE",
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
            image: "/img/anua/heartleaf-pore-control-cleansing-oil.jpg",
            title: "ANUA Heartleaf Pore Control Cleansing Oil",
            price: "$17.70",
            numericPrice: 17.7,
            category: "Face Cleansers",
            brand: "ANUA",
            link: "https://amzn.to/4iAM6QS",
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
            image: "/img/boj/calming-serum-green-tea-panthenol.jpg",
            title: "Beauty of Joseon Calming Serum Green Tea + Panthenol",
            price: "$16.90",
            numericPrice: 16.9,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3FNrfeB",
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
            image: "/img/boj/ginseng-essence-water.jpg",
            title: "Beauty of Joseon Ginseng Essence Water",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Face Serums",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3XY9Sy0",
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
            image: "/img/anua/rice-ceramide-7-hydrating-barrier-serum.jpg",
            title: "ANUA Rice Ceramide 7 Hydrating Barrier Serum",
            price: "$17.00",
            numericPrice: 17.0,
            category: "Face Serums",
            brand: "ANUA",
            link: "https://amzn.to/3DAPqMX",
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
            image: "/img/boj/red-bean-water-gel.jpg",
            title: "Beauty of Joseon Red Bean Water Gel",
            price: "$16.90",
            numericPrice: 16.9,
            category: "Moisturizers",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4bDWrZZ",
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
            image: "/img/cosrx/oil-free-ultra-moisturizing-lotion-with-birch-sap.jpg",
            title: "COSRX Oil Free Ultra Moisturizing Lotion with Birch Sap",
            price: "$18.70",
            numericPrice: 18.7,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/4hiSmeT",
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
            image: "/img/cosrx/hyaluronic-acid-intensive-cream.jpg",
            title: "COSRX Hyaluronic Acid Intensive Cream",
            price: "$20.50",
            numericPrice: 20.5,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/3DwI2lK",
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
            image: "/img/anua/peach-70-niacinamide-serum.jpg",
            title: "ANUA Peach 70 Niacinamide Serum",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Face Serums",
            brand: "ANUA",
            link: "https://amzn.to/4iRguGw",
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
            image: "/img/cosrx/the-retinol-0.3-cream.jpg",
            title: "COSRX The Retinol 0.3 Cream",
            price: "$21.00",
            numericPrice: 21.0,
            category: "Moisturizers",
            brand: "COSRX",
            link: "https://amzn.to/41E2Yiz",
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
            image: "/img/cosrx/hyaluronic-acid-hydra-power-essence.jpg",
            title: "COSRX Hyaluronic Acid Hydra Power Essence",
            price: "$19.00",
            numericPrice: 19.0,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/4hC3R0X",
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
            image: "/img/cosrx/the-niacinamide-15-serum.jpg",
            title: "COSRX The Niacinamide 15 Serum",
            price: "$20.00",
            numericPrice: 20.0,
            category: "Face Serums",
            brand: "COSRX",
            link: "https://amzn.to/4bFyC3U",
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
            image: "/img/anua/heartleaf-silky-moisture-mild-sunscreen.jpg",
            title: "ANUA Heartleaf Silky Moisture Mild Sunscreen",
            price: "$23.00",
            numericPrice: 23.0,
            category: "Sunscreen",
            brand: "ANUA",
            link: "https://amzn.to/4hGmdhe",
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
            image: "/img/anua/bha-2-gentle-exfoliating-toner.jpg",
            title: "ANUA BHA 2% Gentle Exfoliating Toner",
            price: "$18.00",
            numericPrice: 18.0,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/43Ufkps",
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
            image: "/img/anua/heartleaf-77-toner-pad.jpg",
            title: "ANUA Heartleaf 77 Toner Pad",
            price: "$22.00",
            numericPrice: 22.0,
            category: "Toners",
            brand: "ANUA",
            link: "https://amzn.to/43QYo34",
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
            image: "/img/cosrx/aha-bha-clarifying-treatment-toner.jpg",
            title: "COSRX AHA/BHA Clarifying Treatment Toner",
            price: "$15.20",
            numericPrice: 15.2,
            category: "Toners",
            brand: "COSRX",
            link: "https://amzn.to/4izP1cA",
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
            image: "/img/boj/ground-rice-and-honey-glow-mask.jpg",
            title: "Beauty of Joseon Ground Rice and Honey Glow Mask",
            price: "$18.00",
            numericPrice: 18.0,
            category: "Masks & Exfoliators",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/3DCFJ0x",
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
            image: "/img/boj/glow-replenishing-rice-milk.jpg",
            title: "Beauty of Joseon Glow Replenishing Rice Milk",
            price: "$18.00",
            numericPrice: 18.0,
            category: "Toners",
            brand: "Beauty of Joseon",
            link: "https://amzn.to/4kYLh67",
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
    ];

    // Filter and sort state
    let selectedPriceRange = "all";
    let selectedBrand = "all";
    let selectedCategory = "all";
    let sortBy = "default";

    // Extract unique brands from shop all - now using the brand property
    const brands = [...new Set(shopAllCards.map((card) => card.brand))].sort();

    // Extract unique categories from shop all
    const categories = [...new Set(shopAllCards.map((card) => card.category))];

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
    $: filteredProducts = shopAllCards
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

<section class="shopAll-page">
    <!-- Breadcrumb Navigation -->
    <nav class="breadcrumb">
        <a href="/">Home</a>
        <span class="separator">/</span>
        <a href="/collections">Collections</a>
        <span class="separator">/</span>
        <span class="current">Shop All</span>
    </nav>

    <!-- Page Title -->
    <div class="header-section">
        <h1>Korean skin care</h1>
        <p class="product-count">
            {#if hasActiveFilters}
                {sortedProducts.length} of {shopAllCards.length} products
            {:else}
                {shopAllCards.length} products
            {/if}
        </p>
    </div>

    <!-- Korean Skincare Routine Steps -->
    <div class="skincare-routine">
        <p>A Korean skincare routine includes these steps:</p>
        <div class="routine-steps">
            1. Makeup removal with an oil-based cleansing product<br />
            2. Skin cleansing with a water-based cleansing product<br />
            3. Peeling<br />
            4. Mask (wash-off or sheet mask)<br />
            5. Toner<br />
            6. Serum, ampoule and essence<br />
            7. Eye cream<br />
            8. Moisturizer<br />
            9. Sleeping masks and lip masks<br />
            10. Sunscreen
        </div>
        <!-- Description Text -->
        <div class="description">
            <p>
                However, it is by no means meant to do all the steps in one
                routine or even one day, but instead these are all part of a
                comprehensive routine to take care of the skin. The products and
                steps are applied according to the needs of the skin and, of
                course, your own preference.
            </p>
        </div>
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
    .shopAll-page {
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

        .skincare-routine {
            max-width: 1000px;
            margin: 0 auto 3rem auto;
            color: #6b7280;
            text-align: left;

            p {
                margin-bottom: 1rem;
                font-weight: 500;
            }

            .routine-steps {
                margin-left: 1rem;
                font-size: 0.95rem;
                line-height: 2.5;
            }

            .description {
                max-width: 1000px;
                margin: 1rem auto 3rem auto;
                text-align: left;

                p {
                    margin-bottom: 1rem;
                    line-height: 1.6;

                    &:last-child {
                        margin-bottom: 0;
                    }
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
