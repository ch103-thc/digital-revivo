<script>
    import Icon from "@iconify/svelte";
    import { onMount, onDestroy } from "svelte";

    let currentIndex = 0;
    const cardsToShow = 4;

    const moveToNext = () => {
        if (currentIndex + cardsToShow < infoCards.length) {
            currentIndex += 1;
        }
    };

    const moveToPrevious = () => {
        if (currentIndex > 0) {
            currentIndex -= 1;
        }
    };

    const bestsellers = [
        {
            image: "/img/cosrx/advanced-snail-96-mucin-power-essence.jpg",
            title: "COSRX Advanced Snail 96 Mucin Power Essence",
            price: "$17.00",
            link: "https://amzn.to/3HluISH",
        },
        {
            image: "/img/cosrx/acne-pimple-master-patch.jpg",
            title: "COSRX Acne Pimple Master Patch",
            price: "$12.30",
            link: "https://amzn.to/4hG4eYm",
        },
        {
            image: "/img/boj/dynasty-cream.jpg",
            title: "Beauty of Joseon Dynasty Cream",
            price: "$23.00",
            link: "https://amzn.to/41HLxOi",
        },
        {
            image: "/img/cosrx/advanced-snail-92-all-in-one-cream.jpg",
            title: "COSRX Advanced Snail 92 All In One Cream",
            price: "$20.50",
            link: "https://amzn.to/3Fy8CM9",
        },
    ];

    const infoCards = [
        {
            image: "/img/cosrx/advanced-snail-96-mucin-power-essence.jpg",
            title: "COSRX Advanced Snail 96 Mucin Power Essence",
            price: "$17.00",
            link: "https://amzn.to/3HluISH",
        },
        {
            image: "/img/cosrx/advanced-snail-92-all-in-one-cream.jpg",
            title: "COSRX Advanced Snail 92 All In One Cream",
            price: "$20.50",
            link: "https://amzn.to/3Fy8CM9",
        },
        {
            image: "/img/anua/heartleaf-77-soothing-toner.jpg",
            title: "Anua Heartleaf 77 Soothing Toner",
            price: "$19.70",
            link: "https://amzn.to/3Fz3KGg",
        },
        {
            image: "/img/boj/glow-deep-serum-rice-alpha-arbutin.jpg",
            title: "Beauty of Joseon Glow Deep Serum Rice + Alpha-Arbutin",
            price: "$16.50",
            link: "https://amzn.to/3Rnjsqp",
        },
        {
            image: "/img/anua/niacinamide-10-txa-4-serum.jpg",
            title: "Anua Niacinamide 10 + TXA 4 Serum",
            price: "$22.00",
            link: "https://amzn.to/4bD41E0",
        },
        {
            image: "/img/anua/heartleaf-pore-control-cleansing-oil.jpg",
            title: "Anua Heartleaf Pore Control Cleansing Oil",
            price: "$17.70",
            link: "https://amzn.to/4iAM6QS",
        },
        {
            image: "/img/cosrx/full-fit-propolis-light-ampoule.jpg",
            title: "COSRX Full Fit Propolis Light Ampoule",
            price: "$19.40",
            link: "https://amzn.to/41VQfYE",
        },
        {
            image: "/img/cosrx/low-pH-good-morning-gel-cleanser.jpg",
            title: "COSRX Low pH Good Morning Gel Cleanser",
            price: "$11.90",
            link: "https://amzn.to/3FwFWTf",
        },
    ];

    const deviceCards = [
        {
            image: "/img/devices/booster-pro.png",
            title: "Ultimate 6-in-1",
            name: "Booster Pro",
            link: "/products/device-1",
        },
        {
            image: "/img/devices/booster-h.png",
            title: "Glow Booster",
            name: "Booster-H",
            link: "/products/device-2",
        },
        {
            image: "/img/devices/airshot.png",
            title: "Needle-Free Pore Care",
            name: "ATS Air Shot",
            link: "/products/device-3",
        },
    ];

    let videoIndex = 0;
    const videoProducts = [
        {
            video: "/videos/boj/revive-eye-serum.MP4",
            image: "/img/boj/revive-eye-serum.jpg",
            title: "BOJ Revive Eye Serum",
            price: "$17.00",
        },
        {
            video: "/videos/cosrx/advanced-snail-96-mucin-power-essence.mp4",
            image: "/img/cosrx/advanced-snail-96-mucin-power-essence.jpg",
            title: "COSRX Advanced Snail 96 Mucin Power Essence",
            price: "$17.00",
        },
        {
            video: "/videos/anua/heartleaf-77-soothing-toner.MP4",
            image: "/img/anua/heartleaf-77-soothing-toner.jpg",
            title: "ANUA Heartleaf 77 Soothing Toner",
            price: "$19.70",
        },
        {
            video: "/videos/boj/ginseng-cleansing-oil.MP4",
            image: "/img/boj/ginseng-cleansing-oil.jpg",
            title: "BOJ Ginseng Cleansing Oil",
            price: "$19.00",
        },
        {
            video: "/videos/anua/niacinamide-10-txa-4-serum.MP4",
            image: "/img/anua/niacinamide-10-txa-4-serum.jpg",
            title: "ANUA Niacinamide 10 + TXA 4 Serum",
            price: "$22.00",
        },
        {
            video: "/videos/anua/heartleaf-pore-control-cleansing-oil.mp4",
            image: "/img/anua/heartleaf-pore-control-cleansing-oil.jpg",
            title: "ANUA Heartleaf Pore Control Cleansing Oil",
            price: "$17.70",
        },
        {
            video: "/videos/boj/ground-rice-and-honey-glow-mask.mp4",
            image: "/img/boj/ground-rice-and-honey-glow-mask.jpg",
            title: "BOJ Ground Rice and Honey Glow Mask",
            price: "$18.00",
        },
        {
            video: "/videos/anua/heartleaf-quercetinol-pore-deep-cleansing-foam.MP4",
            image: "/img/anua/heartleaf-quercetinol-pore-deep-cleansing-foam.jpg",
            title: "ANUA Heartleaf Quercetinol Pore Deep Cleansing Foam",
            price: "$13.00",
        },
    ];

    const moveVideoNext = () => {
        if (videoIndex + cardsToShow < videoProducts.length) {
            videoIndex += 1;
        }
    };

    const moveVideoPrevious = () => {
        if (videoIndex > 0) {
            videoIndex -= 1;
        }
    };
</script>

<section class="hero-banner">
    <video class="hero-video" autoplay muted loop playsinline>
        <source src="/videos/main-video.mp4" type="video/mp4" />
        Your browser does not support the video tag.
    </video>
    <div class="hero-content">
        <div class="hero-text">
            <h1>Transform Your Skin with Premium K-Beauty</h1>
            <p>
                Discover the secrets of Korean skincare with our curated
                collection of authentic products
            </p>
            <a href="/collections/shop-all" class="hero-cta">Shop Now</a>
        </div>
    </div>
</section>

<!-- NEW BESTSELLERS SECTION -->
<section class="bestsellers">
    <div class="bestsellers-content">
        <h2>Best selling products</h2>
        <a href="/collections/bestsellers" class="view-all-link">View All</a>
    </div>
    <div class="cards-grid">
        {#each bestsellers as product}
            <a
                href={product.link}
                class="bestseller-card"
                target="_blank"
                rel="noopener noreferrer"
            >
                <div class="bestseller-card">
                    <div class="image-wrapper">
                        <img src={product.image} alt={product.title} />
                    </div>
                    <div class="bestseller-card-content">
                        <h3>{product.title}</h3>
                        <p class="price">{product.price}</p>
                        <span class="buy-button">Buy now</span>
                    </div>
                </div>
            </a>
        {/each}
    </div>
</section>

<section class="info-cards">
    <div class="info-cards-content">
        <h2>Our Featured Products</h2>
        <div class="carousel-arrows">
            <button class="arrow left" on:click={moveToPrevious}>
                <Icon icon="mingcute:left-line" width="24" height="24" />
            </button>
            <button class="arrow right" on:click={moveToNext}>
                <Icon icon="mingcute:right-line" width="24" height="24" />
            </button>
        </div>
    </div>
    <div class="cards-grid">
        <!-- MODIFY: Show all cards on mobile for horizontal scroll, sliced cards for desktop -->
        {#each typeof window !== "undefined" && window.innerWidth <= 768 ? infoCards : infoCards.slice(currentIndex, currentIndex + cardsToShow) as card}
            <a
                href={card.link}
                class="info-card"
                target="_blank"
                rel="noopener noreferrer"
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
</section>

<section class="brand-cards">
    <div class="brand-cards-content">
        <h2>Shop By Brands</h2>
        <div class="brand-grid">
            <a href="/brands/cosrx" class="brand-card">
                <img src="/img/cosrx.jpg" alt="Cosrx" />
            </a>
            <a href="/brands/anua" class="brand-card">
                <img src="/img/anua.jpg" alt="Anua" />
            </a>
            <a href="/brands/beauty-of-joseon" class="brand-card">
                <img src="/img/beauty-of-joseon.jpg" alt="Beauty of Joseon" />
            </a>
        </div>
    </div>
</section>

<section class="promo-cards">
    <div class="promo-cards-content">
        <div class="promo-header">
            <h2>Skincare Essentials</h2>
            <a href="/collections" class="view-all-link">View All</a>
        </div>
        <div class="promo-grid">
            <a href="/collections/moisturizers" class="promo-card">
                <img
                    src="/img/collections/moisturizers.jpg"
                    alt="Moisturizers"
                />
                <div class="promo-card-content">
                    <span class="shop-button">Shop Moisturizers </span>
                </div>
            </a>
            <a href="/collections/cleansers" class="promo-card">
                <img src="/img/collections/cleansers.jpg" alt="Cleansers" />
                <div class="promo-card-content">
                    <span class="shop-button">Shop Face Cleansers </span>
                </div>
            </a>
        </div>
    </div>
</section>

<section class="device-cards">
    <div class="device-cards-content">
        <h2>Beauty Device Picks</h2>
        <div class="device-grid">
            {#each deviceCards as card}
                <a
                    href={card.link}
                    class="device-card"
                    target="_blank"
                    rel="noopener noreferrer"
                >
                    <div class="device-container">
                        <img src={card.image} alt={card.title} />
                        <div class="device-overlay">
                            <div class="device-info">
                                <h3>{card.title}</h3>
                                <p class="device-name">
                                    {card.name}
                                </p>
                            </div>
                        </div>
                    </div>
                </a>
            {/each}
        </div>
    </div>
</section>

<section class="video-cards">
    <div class="video-cards-content">
        <h2>Product Demonstrations</h2>
        <div class="carousel-arrows">
            <button class="arrow left" on:click={moveVideoPrevious}>
                <Icon icon="mingcute:left-line" width="24" height="24" />
            </button>
            <button class="arrow right" on:click={moveVideoNext}>
                <Icon icon="mingcute:right-line" width="24" height="24" />
            </button>
        </div>
    </div>
    <div class="cards-grid">
        <!-- MODIFY: Show all cards on mobile for horizontal scroll, sliced cards for desktop -->
        {#each typeof window !== "undefined" && window.innerWidth <= 768 ? videoProducts : videoProducts.slice(videoIndex, videoIndex + cardsToShow) as product}
            <div class="video-card">
                <div class="video-container">
                    <video src={product.video} muted loop autoplay playsinline
                    ></video>
                    <div class="video-overlay">
                        <div class="product-thumbnail">
                            <img src={product.image} alt={product.title} />
                        </div>
                        <div class="product-info">
                            <h3>{product.title}</h3>
                            <p class="price">{product.price}</p>
                        </div>
                    </div>
                </div>
            </div>
        {/each}
    </div>
</section>

<style lang="scss">
    .hero-banner {
        position: relative;
        overflow: hidden;
        padding: 6rem 1.5rem 4rem;
        min-height: 120vh;
        display: flex;
        align-items: center;

        .hero-video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: 0;
            opacity: 1;
        }

        .hero-content {
            position: relative;
            z-index: 1;
            max-width: 1000px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;

            @media (max-width: 768px) {
                grid-template-columns: 1fr;
                gap: 2rem;
                text-align: left;
                position: absolute;
                bottom: 4rem;
                left: 1.5rem;
                right: 1.5rem;
                margin: 0;
            }

            .hero-text {
                h1 {
                    font-size: 3rem;
                    font-weight: 700;
                    color: #111827;
                    margin-bottom: 1.5rem;
                    line-height: 1.2;

                    @media (max-width: 768px) {
                        font-size: 2.5rem;
                    }

                    @media (max-width: 480px) {
                        font-size: 2rem;
                    }
                }

                p {
                    font-size: 1.25rem;
                    color: #6b7280;
                    margin-bottom: 2rem;
                    line-height: 1.6;

                    @media (max-width: 768px) {
                        font-size: 1.125rem;
                    }
                }

                .hero-cta {
                    background-color: #314438;
                    color: white;
                    padding: 1rem 2.5rem;
                    font-size: 1.125rem;
                    font-weight: 600;
                    border-radius: 0.75rem;
                    border: none;
                    cursor: pointer;
                    transition: all 0.3s ease;
                    text-transform: uppercase;
                    letter-spacing: 0.5px;

                    &:hover {
                        transform: translateY(-2px);
                        box-shadow: 0 8px 20px rgba(49, 68, 56, 0.3);
                    }
                }
            }
        }
    }

    .bestsellers {
        padding: 4rem 1.5rem;
        background-color: #ffffff;
        text-align: center;

        .bestsellers-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1000px;
            margin: 0 auto 2rem;

            h2 {
                font-size: 1.875rem;
                font-weight: 700;
                color: #111827;
                margin: 0;
                text-align: left;

                @media (max-width: 768px) {
                    font-size: 1.5rem;
                }
            }

            .view-all-link {
                color: #314438;
                font-weight: 600;
                text-decoration: underline;
                text-underline-offset: 4px;
                transition: color 0.3s;
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
        }

        .bestseller-card {
            display: flex;
            flex-direction: column;
            height: 100%;
            border-radius: 0.5rem;
            text-align: left;
            overflow: hidden;

            .image-wrapper {
                position: relative;
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

            .bestseller-card-content {
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

    .info-cards {
        padding: 4rem 1.5rem;
        background-color: #f3eeea;
        text-align: center;

        .info-cards-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1000px;
            margin: 0 auto 2rem;

            @media (max-width: 768px) {
                padding-left: 1rem;
            }

            h2 {
                font-size: 1.875rem;
                font-weight: 700;
                color: #111827;
                margin: 0;
                text-align: left;

                @media (max-width: 768px) {
                    font-size: 1.5rem;
                }
            }

            .carousel-arrows {
                display: flex;
                gap: 0.75rem;

                @media (max-width: 768px) {
                    display: none;
                }

                .arrow {
                    background-color: transparent;
                    border: 1px solid #d1d5db;
                    border-radius: 50%;
                    width: 45px;
                    height: 45px;
                    cursor: pointer;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    padding: 0;
                    transition:
                        border-color 0.3s,
                        background-color 0.3s;

                    &:hover {
                        border-color: #9ca3af;
                        background-color: rgba(0, 0, 0, 0.05);
                    }

                    &:focus {
                        outline: none;
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

            @media (max-width: 768px) {
                display: flex;
                overflow-x: auto;
                scroll-behavior: smooth;
                gap: 1rem;
                padding: 0 1rem 1rem 1rem;
                margin: 0;
                max-width: none;

                scrollbar-width: none;
                -ms-overflow-style: none;
                &::-webkit-scrollbar {
                    display: none;
                }
            }
        }

        .info-card {
            display: flex;
            flex-direction: column;
            height: 100%;
            border-radius: 0.5rem;
            text-align: left;
            overflow: hidden;

            @media (max-width: 768px) {
                flex: 0 0 280px;
                width: 280px;
            }

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

    .brand-cards {
        padding: 4rem 1.5rem;
        background-color: #ffffff;
        text-align: center;

        .brand-cards-content {
            max-width: 1000px;
            margin: 0 auto;

            h2 {
                font-size: 1.875rem;
                font-weight: 700;
                color: #111827;
                margin-bottom: 2rem;
                text-align: left;

                @media (max-width: 768px) {
                    font-size: 1.5rem;
                }
            }

            .brand-grid {
                display: grid;
                grid-template-columns: repeat(1, 1fr);
                gap: 1.5rem;

                @media (min-width: 768px) {
                    grid-template-columns: repeat(3, 1fr);
                }

                .brand-card {
                    border-radius: 0.5rem;
                    overflow: hidden;
                    background: #f9fafb;
                    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
                    text-align: center;
                    transition: transform 0.3s;

                    &:hover {
                        transform: translateY(-4px);
                    }

                    img {
                        width: 100%;
                        height: 300px;
                        object-fit: cover;
                    }

                    h3 {
                        font-size: 1rem;
                        font-weight: 600;
                        margin: 1rem;
                        color: #1f2937;
                    }
                }
            }
        }
    }

    .promo-cards {
        padding: 4rem 1.5rem;
        background-color: #f3eeea;
        text-align: center;

        .promo-cards-content {
            max-width: 1000px;
            margin: 0 auto;

            .promo-header {
                display: flex;
                justify-content: space-between;
                align-items: center;
                margin-bottom: 2rem;

                h2 {
                    margin: 0;
                    font-size: 1.875rem;
                    font-weight: 700;
                    color: #111827;

                    @media (max-width: 768px) {
                        font-size: 1.5rem;
                    }
                }

                .view-all-link {
                    color: #314438;
                    font-weight: 600;
                    text-decoration: underline;
                    text-underline-offset: 4px;
                    transition: color 0.3s;
                }
            }

            .promo-grid {
                display: grid;
                grid-template-columns: 1fr;
                gap: 1.5rem;

                @media (min-width: 768px) {
                    grid-template-columns: repeat(2, 1fr);
                }
            }

            .promo-card {
                position: relative;
                border-radius: 0.5rem;
                overflow: hidden;
                text-align: center;
                box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);

                img {
                    width: 100%;
                    height: 450px;
                    object-fit: cover;
                    display: block;
                }

                .promo-card-content {
                    position: absolute;
                    top: 50%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    padding: 0;

                    .shop-button {
                        background-color: #314438;
                        color: white;
                        padding: 1rem 2rem;
                        font-size: 0.9rem;
                        border-radius: 0.375rem;
                        border: none;
                        transition: all 0.3s ease;
                        cursor: pointer;

                        &:hover {
                            transform: translateY(-2px);
                            box-shadow: 0 8px 20px rgba(49, 68, 56, 0.3);
                        }
                    }
                }
            }
        }
    }

    .device-cards {
        padding: 4rem 1.5rem;
        background-color: #ffffff;
        text-align: center;

        .device-cards-content {
            max-width: 1000px;
            margin: 0 auto;

            h2 {
                font-size: 1.875rem;
                font-weight: 700;
                color: #111827;
                margin-bottom: 2rem;
                text-align: left;

                @media (max-width: 768px) {
                    font-size: 1.5rem;
                }
            }

            .device-grid {
                display: grid;
                grid-template-columns: repeat(1, 1fr);
                gap: 1.5rem;

                @media (min-width: 768px) {
                    grid-template-columns: repeat(2, 1fr);
                }

                @media (min-width: 1024px) {
                    grid-template-columns: repeat(3, 1fr);
                }
            }

            .device-card {
                background: white;
                border-radius: 0.75rem;
                overflow: hidden;
                box-shadow: 0 4px 6px rgba(0, 0, 0, 0.07);
                transition:
                    transform 0.3s,
                    box-shadow 0.3s;
                display: block;
                text-decoration: none;

                &:hover {
                    transform: translateY(-4px);
                    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
                }

                .device-container {
                    position: relative;
                    height: 400px;

                    img {
                        width: 100%;
                        height: 100%;
                        object-fit: cover;
                        display: block;
                    }

                    .device-overlay {
                        position: absolute;
                        top: 0;
                        left: 0;
                        right: 0;
                        background: linear-gradient(
                            to bottom,
                            rgba(0, 0, 0, 0.8) 0%,
                            rgba(0, 0, 0, 0.4) 50%,
                            transparent 100%
                        );
                        padding: 1.5rem 1rem;
                        display: flex;
                        align-items: flex-start;
                        justify-content: center;

                        .device-info {
                            text-align: center;
                            max-width: 250px;

                            h3 {
                                font-size: 0.9rem;
                                font-weight: 400;
                                color: rgba(255, 255, 255, 0.9);
                                margin: 0;
                                line-height: 1.5;
                                text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
                            }

                            .device-name {
                                color: white;
                                margin: 0 0 0.5rem 0;
                                font-size: 1.25rem;
                                font-weight: 700;
                                line-height: 1.4;
                                text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
                            }
                        }
                    }
                }
            }
        }
    }

    .video-cards {
        padding: 4rem 1.5rem;
        background-color: #f3eeea;
        text-align: center;

        .video-cards-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1000px;
            margin: 0 auto 2rem;

            @media (max-width: 768px) {
                padding-left: 1rem;
            }

            h2 {
                font-size: 1.875rem;
                font-weight: 700;
                color: #111827;
                margin: 0;
                text-align: left;

                @media (max-width: 768px) {
                    font-size: 1.5rem;
                }
            }

            .carousel-arrows {
                display: flex;
                gap: 0.75rem;

                @media (max-width: 768px) {
                    display: none;
                }

                .arrow {
                    background-color: transparent;
                    border: 1px solid #d1d5db;
                    border-radius: 50%;
                    width: 45px;
                    height: 45px;
                    cursor: pointer;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    padding: 0;
                    transition:
                        border-color 0.3s,
                        background-color 0.3s;

                    &:hover {
                        border-color: #9ca3af;
                        background-color: rgba(0, 0, 0, 0.05);
                    }

                    &:focus {
                        outline: none;
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

            @media (max-width: 768px) {
                display: flex;
                overflow-x: auto;
                scroll-behavior: smooth;
                gap: 1rem;
                padding: 0 1rem 1rem 1rem;
                margin: 0;
                max-width: none;

                scrollbar-width: none;
                -ms-overflow-style: none;
                &::-webkit-scrollbar {
                    display: none;
                }
            }
        }

        .video-card {
            background: white;
            border-radius: 0.75rem;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.07);
            transition:
                transform 0.3s,
                box-shadow 0.3s;

            &:hover {
                transform: translateY(-4px);
                box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
            }

            @media (max-width: 768px) {
                flex: 0 0 220px;
                width: 220px;
            }

            .video-container {
                position: relative;
                height: 400px;

                video {
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                }

                .video-overlay {
                    position: absolute;
                    bottom: 0;
                    left: 0;
                    right: 0;
                    background: linear-gradient(
                        to top,
                        rgba(0, 0, 0, 0.8) 0%,
                        rgba(0, 0, 0, 0.4) 50%,
                        transparent 100%
                    );
                    padding: 0.5rem;
                    display: flex;
                    align-items: flex-end;
                    gap: 0.5rem;

                    .product-thumbnail {
                        width: 50px;
                        height: 50px;
                        border-radius: 0.5rem;
                        overflow: hidden;
                        flex-shrink: 0;
                        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);

                        img {
                            width: 100%;
                            height: 100%;
                            object-fit: cover;
                        }
                    }

                    .product-info {
                        flex: 1;
                        text-align: left;

                        h3 {
                            color: white;
                            margin: 0 0 0.25rem 0;
                            font-size: 1rem;
                            line-height: 1.4;
                            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
                            white-space: nowrap;
                            overflow: hidden;
                            text-overflow: ellipsis;
                            max-width: 150px;
                        }

                        .price {
                            font-size: 1rem;
                            color: #fff;
                            margin: 0;
                            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
                        }
                    }
                }
            }
        }

        .video-cards-button {
            background-color: #314438;
            color: white;
            padding: 0.75rem 2rem;
            font-size: 1rem;
            border-radius: 0.5rem;
            border: none;
            text-transform: uppercase;
            cursor: pointer;
            transition: background-color 0.3s;

            &:hover {
                background-color: #1d4ed8;
            }
        }
    }
</style>
