<script>
    import Icon from "@iconify/svelte";
    import { onMount } from "svelte";

    // Sample collections data
    const collections = [
        {
            id: "bestsellers",
            name: "Best Sellers",
            description:
                "Our most popular K-beauty products loved by customers worldwide",
            image: "/img/best-sellers.jpg",
            productCount: 24,
            featured: true,
        },
        {
            id: "cleansers",
            name: "Face Cleansers",
            description: "Gentle yet effective cleansers for all skin types",
            image: "/img/collections/cleansers.jpg",
            productCount: 18,
            featured: true,
        },
        {
            id: "toners",
            name: "Toners",
            description: "Balancing and hydrating toners for healthy skin prep",
            image: "/img/collections/toners.jpg",
            productCount: 16,
            featured: false,
        },
        {
            id: "moisturizers",
            name: "Moisturizers",
            description:
                "Hydrating creams and lotions for healthy, glowing skin",
            image: "/img/collections/moisturizers.jpg",
            productCount: 22,
            featured: true,
        },
        {
            id: "serums",
            name: "Face Serums",
            description:
                "Concentrated treatments for targeted skincare concerns",
            image: "/img/collections/face-serums.jpg",
            productCount: 31,
            featured: false,
        },
        {
            id: "masks-and-exfoliators",
            name: "Masks & Exfoliators",
            description:
                "Sheet masks and exfoliators for instant skin transformation",
            image: "/img/collections/masks-exfoliators.jpg",
            productCount: 28,
            featured: false,
        },
        {
            id: "acne-patches",
            name: "Acne Patches",
            description: "Targeted solutions for blemish-prone skin",
            image: "/img/collections/acne-patches.png",
            productCount: 14,
            featured: false,
        },
        {
            id: "sunscreen",
            name: "Sunscreen",
            description:
                "Protect your skin with Korean sunscreens and UV protection",
            image: "/img/collections/sunscreen.jpg",
            productCount: 12,
            featured: false,
        },
        {
            id: "eye-care",
            name: "Eye Care",
            description: "Specialized treatments for the delicate eye area",
            image: "/img/collections/eye-care.jpg",
            productCount: 9,
            featured: false,
        },
    ];

    // Filter and search functionality
    let searchQuery = "";
    let selectedFilter = "all";
    let sortBy = "featured";
    let filteredCollections = collections;

    // Filter options
    const filterOptions = [
        { value: "all", label: "All Collections" },
        { value: "featured", label: "Featured" },
        { value: "skincare", label: "Skincare" },
        // { value: "popular", label: "Most Popular" },
    ];

    // Sort options
    const sortOptions = [
        { value: "featured", label: "Featured First" },
        { value: "name", label: "Alphabetical A-Z" },
        { value: "products", label: "Most Products" },
        { value: "newest", label: "Newest" },
    ];

    // Apply filters and search
    function updateFilteredCollections() {
        let filtered = [...collections];

        // Apply search filter
        if (searchQuery.trim()) {
            filtered = filtered.filter(
                (collection) =>
                    collection.name
                        .toLowerCase()
                        .includes(searchQuery.toLowerCase()) ||
                    collection.description
                        .toLowerCase()
                        .includes(searchQuery.toLowerCase()),
            );
        }

        // Apply category filter
        if (selectedFilter === "featured") {
            filtered = filtered.filter((collection) => collection.featured);
        }

        // Apply sorting
        switch (sortBy) {
            case "name":
                filtered.sort((a, b) => a.name.localeCompare(b.name));
                break;
            case "products":
                filtered.sort((a, b) => b.productCount - a.productCount);
                break;
            case "featured":
            default:
                filtered.sort((a, b) => {
                    if (a.featured && !b.featured) return -1;
                    if (!a.featured && b.featured) return 1;
                    return 0;
                });
                break;
        }

        filteredCollections = filtered;
    }

    // Reactive updates
    $: {
        searchQuery, selectedFilter, sortBy;
        updateFilteredCollections();
    }

    // Clear search
    function clearSearch() {
        searchQuery = "";
    }

    // Featured collections for hero section
    const featuredCollections = collections
        .filter((c) => c.featured)
        .slice(0, 3);
</script>

<!-- Hero Section -->
<section class="collections-hero">
    <div class="hero-content">
        <div class="hero-text">
            <h1>Discover Our Collections</h1>
            <p>
                Curated selections of the finest Korean beauty products,
                organized by category and skin concern
            </p>
        </div>
    </div>
</section>

<!-- Breadcrumb Navigation -->
<nav class="breadcrumb">
    <a href="/">Home</a>
    <span class="separator">/</span>
    <span class="current">Collections</span>
</nav>

<!-- Featured Collections Carousel -->
<section class="featured-collections">
    <div class="featured-content">
        <h2>Featured Collections</h2>
        <div class="featured-grid">
            {#each featuredCollections as collection}
                <a href="/collections/{collection.id}" class="featured-card">
                    <div class="image-wrapper">
                        <img src={collection.image} alt={collection.name} />
                        <div class="overlay">
                            <div class="overlay-content">
                                <h3>{collection.name}</h3>
                                <p>{collection.description}</p>
                                <span class="product-count"
                                    >{collection.productCount} Products</span
                                >
                            </div>
                        </div>
                    </div>
                </a>
            {/each}
        </div>
    </div>
</section>

<!-- Collections Grid -->
<section class="collections-grid-section">
    <div class="grid-content">
        {#if filteredCollections.length > 0}
            <div class="collections-grid">
                {#each filteredCollections as collection}
                    <a
                        href="/collections/{collection.id}"
                        class="collection-card"
                    >
                        <div class="card-image">
                            <img src={collection.image} alt={collection.name} />
                            {#if collection.featured}
                                <div class="featured-badge">Featured</div>
                            {/if}
                        </div>
                        <div class="card-content">
                            <h3>{collection.name}</h3>
                            <p>{collection.description}</p>
                            <div class="card-footer">
                                <span class="product-count">
                                    <Icon
                                        icon="mingcute:grid-line"
                                        width="16"
                                        height="16"
                                    />
                                    {collection.productCount} Products
                                </span>
                                <span class="view-collection">
                                    View Collection
                                    <Icon
                                        icon="mingcute:arrow-right-line"
                                        width="16"
                                        height="16"
                                    />
                                </span>
                            </div>
                        </div>
                    </a>
                {/each}
            </div>
        {:else}
            <div class="no-results">
                <Icon icon="mingcute:search-line" width="48" height="48" />
                <h3>No collections found</h3>
                <p>Try adjusting your search or filter criteria</p>
                <button
                    class="reset-filters"
                    on:click={() => {
                        searchQuery = "";
                        selectedFilter = "all";
                    }}
                >
                    Reset Filters
                </button>
            </div>
        {/if}
    </div>
</section>

<style lang="scss">
    .collections-hero {
        background:
            linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
            url("https://images.unsplash.com/photo-1556228720-195a672e8a03?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2340&q=80")
                center/cover;
        padding: 12rem 1.5rem 10rem;
        text-align: center;
        color: white;
        position: relative;

        &::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(49, 68, 56, 0.1);
            z-index: 1;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
            position: relative;
            z-index: 2;

            .hero-text {
                h1 {
                    font-size: 3rem;
                    font-weight: 700;
                    margin-bottom: 1.5rem;
                    line-height: 1.2;
                    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);

                    @media (max-width: 768px) {
                        font-size: 2.5rem;
                    }
                }

                p {
                    font-size: 1.25rem;
                    opacity: 0.95;
                    line-height: 1.6;
                    max-width: 600px;
                    margin: 0 auto;
                    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);

                    @media (max-width: 768px) {
                        font-size: 1.125rem;
                    }
                }
            }
        }
    }

    .breadcrumb {
        text-align: left;
        max-width: 1140px;
        margin: 2rem auto;
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

    .featured-collections {
        padding: 4rem 1.5rem;
        background-color: #fafafa;
        border-bottom: 1px solid #e5e7eb;

        .featured-content {
            max-width: 1140px;
            margin: 0 auto;

            h2 {
                font-size: 2rem;
                font-weight: 700;
                color: #111827;
                margin-bottom: 2rem;
                text-align: center;
            }

            .featured-grid {
                display: grid;
                grid-template-columns: 1fr;
                gap: 2rem;

                @media (min-width: 768px) {
                    grid-template-columns: repeat(2, 1fr);
                }

                @media (min-width: 1024px) {
                    grid-template-columns: repeat(3, 1fr);
                }

                .featured-card {
                    border-radius: 1rem;
                    overflow: hidden;
                    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
                    transition:
                        transform 0.3s ease,
                        box-shadow 0.3s ease;

                    &:hover {
                        transform: translateY(-8px);
                        box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);

                        .overlay {
                            opacity: 1;
                        }
                    }

                    .image-wrapper {
                        position: relative;
                        height: 300px;
                        overflow: hidden;

                        img {
                            width: 100%;
                            height: 100%;
                            object-fit: cover;
                            transition: transform 0.3s ease;
                        }

                        .overlay {
                            position: absolute;
                            top: 0;
                            left: 0;
                            right: 0;
                            bottom: 0;
                            background: linear-gradient(
                                to bottom,
                                rgba(0, 0, 0, 0.3) 0%,
                                rgba(0, 0, 0, 0.7) 100%
                            );
                            display: flex;
                            align-items: flex-end;
                            padding: 2rem;
                            opacity: 0.8;
                            transition: opacity 0.3s ease;

                            .overlay-content {
                                color: white;

                                h3 {
                                    font-size: 1.5rem;
                                    font-weight: 700;
                                    margin-bottom: 0.5rem;
                                }

                                p {
                                    opacity: 0.9;
                                    margin-bottom: 1rem;
                                    line-height: 1.5;
                                }

                                .product-count {
                                    background-color: rgba(255, 255, 255, 0.2);
                                    padding: 0.5rem 1rem;
                                    border-radius: 2rem;
                                    font-size: 0.875rem;
                                    font-weight: 600;
                                }
                            }
                        }
                    }
                }
            }
        }
    }

    .collections-grid-section {
        padding: 4rem 1.5rem;
        background-color: #f3eeea;

        .grid-content {
            max-width: 1140px;
            margin: 0 auto;

            .collections-grid {
                display: grid;
                grid-template-columns: 1fr;
                gap: 2rem;

                @media (min-width: 640px) {
                    grid-template-columns: repeat(2, 1fr);
                }

                @media (min-width: 1024px) {
                    grid-template-columns: repeat(3, 1fr);
                }

                .collection-card {
                    background: white;
                    border-radius: 1rem;
                    overflow: hidden;
                    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
                    transition: all 0.3s ease;

                    &:hover {
                        transform: translateY(-4px);
                        box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);

                        .card-image img {
                            transform: scale(1.05);
                        }

                        .view-collection {
                            color: #314438;
                        }
                    }

                    .card-image {
                        position: relative;
                        height: 200px;
                        overflow: hidden;

                        img {
                            width: 100%;
                            height: 100%;
                            object-fit: cover;
                            transition: transform 0.3s ease;
                        }

                        .featured-badge {
                            position: absolute;
                            top: 1rem;
                            right: 1rem;
                            background-color: #dc2626;
                            color: white;
                            padding: 0.25rem 0.75rem;
                            border-radius: 1rem;
                            font-size: 0.75rem;
                            font-weight: 600;
                            text-transform: uppercase;
                            letter-spacing: 0.5px;
                        }
                    }

                    .card-content {
                        padding: 1.5rem;

                        h3 {
                            font-size: 1.25rem;
                            font-weight: 700;
                            color: #111827;
                            margin-bottom: 0.5rem;
                        }

                        p {
                            color: #6b7280;
                            line-height: 1.5;
                            margin-bottom: 1rem;
                        }

                        .card-footer {
                            display: flex;
                            justify-content: space-between;
                            align-items: center;

                            .product-count {
                                display: flex;
                                align-items: center;
                                gap: 0.25rem;
                                font-size: 0.875rem;
                                color: #6b7280;
                            }

                            .view-collection {
                                display: flex;
                                align-items: center;
                                gap: 0.25rem;
                                font-size: 0.875rem;
                                font-weight: 600;
                                color: #374151;
                                transition: color 0.2s ease;
                            }
                        }
                    }
                }
            }

            .no-results {
                text-align: center;
                padding: 4rem 2rem;
                color: #6b7280;

                :global(svg) {
                    margin-bottom: 1rem;
                    opacity: 0.5;
                }

                h3 {
                    font-size: 1.5rem;
                    font-weight: 600;
                    margin-bottom: 0.5rem;
                    color: #374151;
                }

                p {
                    margin-bottom: 2rem;
                }

                .reset-filters {
                    background-color: #314438;
                    color: white;
                    padding: 0.75rem 1.5rem;
                    border-radius: 0.5rem;
                    border: none;
                    font-weight: 600;
                    cursor: pointer;
                    transition: background-color 0.3s ease;

                    &:hover {
                        background-color: #1d4ed8;
                    }
                }
            }
        }
    }
</style>
