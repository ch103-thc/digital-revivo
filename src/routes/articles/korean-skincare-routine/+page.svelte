<script>
    // Product recommendations for different skin types
    const productRecommendations = {
        allSkinTypes: [
            {
                name: "Beauty of Joseon Ginseng Cleansing Oil",
                category: "Face Cleansers",
            },
            {
                name: "Beauty of Joseon Green Plum Refreshing Cleanser",
                category: "Face Cleansers",
            },
            {
                name: "ANUA Heartleaf Pore Control Cleansing Oil",
                category: "Face Cleansers",
            },
            {
                name: "ANUA Heartleaf Quercetinol Pore Deep Cleansing Foam",
                category: "Face Cleansers",
            },
            {
                name: "COSRX Low pH Good Morning Gel Cleanser  ",
                category: "Face Cleansers",
            },
            {
                name: "ANUA Heartleaf 77 Soothing Toner",
                category: "Toners",
            },
            {
                name: "ANUA Peach 77 Niacin Essence Toner",
                category: "Toners",
            },
            {
                name: "ANUA Rice 70 Glow Milky Toner",
                category: "Toners",
            },
            {
                name: "COSRX AHA/BHA Clarifying Treatment Toner",
                category: "Toners",
            },
            {
                name: "COSRX Full Fit Propolis Synergy Toner",
                category: "Toners",
            },
            {
                name: "Beauty of Joseon Dynasty Cream",
                category: "Moisturizers",
            },
            {
                name: "ANUA Heartleaf Daily Lotion",
                category: "Moisturizers",
            },
            {
                name: "COSRX Oil-Free Ultra-Moisturizing Lotion with Birch Sap",
                category: "Moisturizers",
            },
            {
                name: "COSRX Full Fit Propolis Light Cream",
                category: "Moisturizers",
            },
            {
                name: "Beauty of Joseon Glow Deep Serum Rice + Alpha-Arbutin",
                category: "Face Serums",
            },
            {
                name: "Beauty of Joseon Calming Serum Green Tea + Panthenol",
                category: "Face Serums",
            },
            {
                name: "Beauty of Joseon Ginseng Essence Water",
                category: "Face Serums",
            },
            {
                name: "COSRX Full Fit Propolis Light Ampoule",
                category: "Face Serums",
            },
            {
                name: "COSRX Hyaluronic Acid Hydra Power Essence",
                category: "Face Serums",
            },
            {
                name: "COSRX Advanced Snail 96 Mucin Power Essence",
                category: "Face Serums",
            },
            {
                name: "Beauty of Joseon Apricot Blossom Peeling Gel",
                category: "Masks & Exfoliators",
            },
            {
                name: "COSRX Acne Pimple Master Patch",
                category: "Acne Patches",
            },
            {
                name: "Beauty of Joseon Revive Eye Serum",
                category: "Eye Care",
            },
            {
                name: "COSRX The Peptide Collagen Hydrogel Eye Patch",
                category: "Eye Care",
            },
            {
                name: "ANUA Heartleaf Silky Moisture Mild Sunscreen",
                category: "Sunscreen",
            },
        ],
        oilySkin: [
            {
                name: "ANUA Heartleaf Pore Control Cleansing Oil",
                category: "Face Cleansers",
            },
            {
                name: "ANUA Heartleaf Quercetinol Pore Deep Cleansing Foam",
                category: "Face Cleansers",
            },
            {
                name: "ANUA Rice Enzyme Brightening Cleansing Powder",
                category: "Face Cleansers",
            },
            {
                name: "COSRX Low pH Good Morning Gel Cleanser",
                category: "Face Cleansers",
            },
            {
                name: "ANUA BHA 2% Gentle Exfoliating Toner",
                category: "Toners",
            },
            {
                name: "COSRX AHA/BHA Clarifying Treatment Toner",
                category: "Toners",
            },
            {
                name: "ANUA Heartleaf 77 Toner Pad",
                category: "Toners",
            },
            {
                name: "Beauty of Joseon Red Bean Water Gel",
                category: "Moisturizers",
            },
            {
                name: "ANUA Heartleaf 70 Intense Calming Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX Oil-Free Ultra-Moisturizing Lotion with Birch Sap",
                category: "Moisturizers",
            },
            {
                name: "ANUA Niacinamide 10 + TXA 4 Serum",
                category: "Face Serums",
            },
            {
                name: "ANUA Peach 70 Niacinamide Serum",
                category: "Face Serums",
            },
            {
                name: "COSRX The Niacinamide 15 Serum",
                category: "Face Serums",
            },
            {
                name: "COSRX Niacinamide 15% Peptide Booster Set",
                category: "Face Serums",
            },
            {
                name: "Beauty of Joseon Red Bean Refreshing Pore Mask",
                category: "Masks & Exfoliators",
            },
            {
                name: "COSRX Acne Pimple Master Patch",
                category: "Acne Patches",
            },
        ],
        drySkin: [
            {
                name: "Beauty of Joseon Ginseng Cleansing Oil",
                category: "Face Cleansers",
            },
            {
                name: "ANUA Rice Enzyme Brightening Cleansing Powder",
                category: "Face Cleansers",
            },
            {
                name: "ANUA Rice 70 Glow Milky Toner",
                category: "Toners",
            },
            {
                name: "COSRX Full Fit Propolis Synergy Toner",
                category: "Toners",
            },
            {
                name: "COSRX Hyaluronic Acid Hydra Power Essence",
                category: "Face Serums",
            },
            {
                name: "Beauty of Joseon Glow Replenishing Rice Milk",
                category: "Toners",
            },
            {
                name: "ANUA 3 Ceramide Panthenol Moisture Barrier Cream",
                category: "Moisturizers",
            },
            {
                name: "ANUA Rice 70 Intensive Moisturizing Milk",
                category: "Moisturizers",
            },
            {
                name: "COSRX Hyaluronic Acid Intensive Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX Full Fit Propolis Light Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX Advanced Snail 92 All In One Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX Ultimate Nourishing Rice Overnight Spa Mask",
                category: "Masks & Exfoliators",
            },
            {
                name: "COSRX Advanced Snail Mucin Glass Glow Hydrogel Mask",
                category: "Masks & Exfoliators",
            },
        ],
        agingSkin: [
            {
                name: "Beauty of Joseon Light On Serum Centella + Vita C",
                category: "Face Serums",
            },
            {
                name: "Beauty of Joseon Ginseng Essence Water",
                category: "Face Serums",
            },
            {
                name: "COSRX The Retinol 0.3 Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX The Retinol 0.5 Oil",
                category: "Moisturizers",
            },
            {
                name: "COSRX The Niacinamide 15 Serum",
                category: "Face Serums",
            },
            {
                name: "COSRX Niacinamide 15% Peptide Booster Set",
                category: "Face Serums",
            },
            {
                name: "COSRX The Vitamin C 23 Serum",
                category: "Face Serums",
            },
            {
                name: "Beauty of Joseon Dynasty Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX Advanced Snail 92 All In One Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX Hyaluronic Acid Intensive Cream",
                category: "Moisturizers",
            },
            {
                name: "COSRX The Peptide Collagen Hydrogel Eye Patch",
                category: "Eye Care",
            },
            {
                name: "Beauty of Joseon Revive Eye Serum",
                category: "Eye Care",
            },
        ],
    };

    // 10-step routine steps
    const tenStepRoutine = [
        {
            step: 1,
            title: "Oil-based Cleanser",
            description:
                "Remove makeup and sunscreen with an oil-based cleansing product",
        },
        {
            step: 2,
            title: "Water-based Cleanser",
            description:
                "Cleanse skin with a water-based cleansing product for double cleansing",
        },
        {
            step: 3,
            title: "Exfoliation",
            description:
                "Remove dead skin cells (2-3 times per week, not daily)",
        },
        {
            step: 4,
            title: "Toner",
            description: "Hydrate and prepare skin for next steps, balance pH",
        },
        {
            step: 5,
            title: "Mask",
            description: "Use wash-off or sheet masks for targeted treatment",
        },
        {
            step: 6,
            title: "Essence/Serum/Ampoule",
            description:
                "Apply active ingredients to treat specific skin concerns",
        },
        {
            step: 7,
            title: "Eye Cream",
            description: "Target the delicate eye area with specialized care",
        },
        {
            step: 8,
            title: "Moisturizer",
            description: "Lock in hydration with face cream or emulsion",
        },
        {
            step: 9,
            title: "Night Mask",
            description: "Apply overnight treatments and lip masks (PM only)",
        },
        {
            step: 10,
            title: "Sunscreen",
            description: "Protect skin from UV damage (AM only)",
        },
    ];

    // Simple 3-step routine
    const simpleRoutine = [
        {
            title: "Double Cleansing",
            description:
                "Remove makeup with oil-based cleanser, then cleanse skin with water-based cleanser",
            tips: "Essential for removing all traces of makeup, sunscreen, and daily buildup",
        },
        {
            title: "Moisturizing",
            description:
                "Use toner, serum, and moisturizer to hydrate and nourish skin",
            tips: "Every skin type needs moisture, even oily and acne-prone skin",
        },
        {
            title: "Sun Protection",
            description:
                "Apply sunscreen daily to protect against UV damage and premature aging",
            tips: "Use 0.25-0.5 teaspoons for face and neck, reapply throughout the day",
        },
    ];

    // Active content sections
    let activeSection = "overview";
    let selectedSkinType = "allSkinTypes";

    // Navigation function
    function setActiveSection(section) {
        activeSection = section;
    }

    // Skin type labels
    const skinTypeLabels = {
        allSkinTypes: "All Skin Types",
        oilySkin: "Oily & Acne-Prone Skin",
        drySkin: "Dry Skin",
        agingSkin: "Aging Skin",
    };
</script>

<section class="skincare-guide-page">
    <!-- Breadcrumb Navigation -->
    <nav class="breadcrumb">
        <a href="/">Home</a>
        <span class="separator">/</span>
        <a href="/articles">Articles</a>
        <span class="separator">/</span>
        <span class="current">
            Korean Skin Care and 10-Step Skin Care Routine: Your Guide to
            Glowing Skin
        </span>
    </nav>

    <!-- Page Header -->
    <div class="header-section">
        <h1>Korean Skincare Guide</h1>
        <p class="subtitle">
            Your Complete Guide to the 10-Step Korean Skincare Routine and
            Glowing Skin
        </p>
    </div>

    <!-- Navigation Tabs -->
    <div class="guide-navigation">
        <button
            class="nav-tab {activeSection === 'overview' ? 'active' : ''}"
            on:click={() => setActiveSection("overview")}
        >
            Overview
        </button>
        <button
            class="nav-tab {activeSection === 'steps' ? 'active' : ''}"
            on:click={() => setActiveSection("steps")}
        >
            10-Step Routine
        </button>
        <button
            class="nav-tab {activeSection === 'simple' ? 'active' : ''}"
            on:click={() => setActiveSection("simple")}
        >
            Simple Routine
        </button>
        <button
            class="nav-tab {activeSection === 'products' ? 'active' : ''}"
            on:click={() => setActiveSection("products")}
        >
            Product Recommendations
        </button>
        <button
            class="nav-tab {activeSection === 'tips' ? 'active' : ''}"
            on:click={() => setActiveSection("tips")}
        >
            Tips & Techniques
        </button>
    </div>

    <!-- Content Sections -->
    <div class="guide-content">
        {#if activeSection === "overview"}
            <div class="content-section">
                <h2>What is Korean Skincare?</h2>
                <div class="intro-text">
                    <p>
                        Korean skincare is renowned worldwide for its emphasis
                        on prevention, hydration, and achieving healthy, glowing
                        skin. The famous 10-step routine might seem
                        overwhelming, but you can easily customize it to fit
                        your needs and lifestyle.
                    </p>
                    <p>
                        The key principle behind Korean skincare is treating
                        your skin gently with multiple layers of lightweight,
                        nourishing products rather than using harsh, aggressive
                        treatments. This approach helps maintain your skin's
                        natural barrier while addressing specific concerns.
                    </p>
                </div>

                <div class="key-principles">
                    <h3>Core Principles of Korean Skincare</h3>
                    <div class="principles-grid">
                        <div class="principle-card">
                            <h4>Prevention Over Treatment</h4>
                            <p>
                                Focus on maintaining healthy skin rather than
                                fixing problems after they occur.
                            </p>
                        </div>
                        <div class="principle-card">
                            <h4>Gentle Approach</h4>
                            <p>
                                Use mild, nourishing products that work with
                                your skin's natural processes.
                            </p>
                        </div>
                        <div class="principle-card">
                            <h4>Hydration is Key</h4>
                            <p>
                                Every skin type benefits from proper hydration,
                                even oily and acne-prone skin.
                            </p>
                        </div>
                        <div class="principle-card">
                            <h4>Customizable Routine</h4>
                            <p>
                                Adapt the routine to your skin's specific needs
                                and your lifestyle.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        {/if}

        {#if activeSection === "steps"}
            <div class="content-section">
                <h2>The Complete 10-Step Korean Skincare Routine</h2>
                <p class="section-intro">
                    Remember: You don't need to do all these steps every day!
                    Start with the basics and gradually add steps as needed.
                    Some steps are optional or can be done 2-3 times per week.
                </p>

                <div class="steps-container">
                    {#each tenStepRoutine as routineStep}
                        <div class="step-card">
                            <div class="step-number">{routineStep.step}</div>
                            <div class="step-content">
                                <h3>{routineStep.title}</h3>
                                <p>{routineStep.description}</p>
                            </div>
                        </div>
                    {/each}
                </div>

                <div class="routine-note">
                    <h3>Important Notes:</h3>
                    <ul>
                        <li>
                            Steps 3 (exfoliation) should only be done 2-3 times
                            per week
                        </li>
                        <li>Step 9 (night mask) is for evening routine only</li>
                        <li>Step 10 (sunscreen) is for morning routine only</li>
                        <li>
                            You can skip steps that don't suit your skin or
                            lifestyle
                        </li>
                    </ul>
                </div>
            </div>
        {/if}

        {#if activeSection === "simple"}
            <div class="content-section">
                <h2>Easy 3-Step Korean Skincare Routine</h2>
                <p class="section-intro">
                    New to Korean skincare? Start with these three essential
                    steps that form the foundation of any good skincare routine.
                </p>

                <div class="simple-steps">
                    {#each simpleRoutine as step, index}
                        <div class="simple-step-card">
                            <div class="simple-step-number">{index + 1}</div>
                            <div class="simple-step-content">
                                <h3>{step.title}</h3>
                                <p class="step-description">
                                    {step.description}
                                </p>
                                <div class="step-tips">
                                    <strong>Pro Tip:</strong>
                                    {step.tips}
                                </div>
                            </div>
                        </div>
                    {/each}
                </div>

                <div class="upgrade-note">
                    <h3>Ready for More?</h3>
                    <p>
                        Once you're comfortable with these three steps, you can
                        gradually add more products like serums, essences, or
                        masks to target specific skin concerns. The key is to
                        introduce new products one at a time to see how your
                        skin responds.
                    </p>
                </div>
            </div>
        {/if}

        {#if activeSection === "products"}
            <div class="content-section">
                <h2>Product Recommendations by Skin Type</h2>
                <p class="section-intro">
                    Choose products that match your skin type for the best
                    results. Remember, everyone's skin is unique, so what works
                    for others might not work for you.
                </p>

                <!-- Skin Type Selector -->
                <div class="skin-type-selector">
                    {#each Object.entries(skinTypeLabels) as [key, label]}
                        <button
                            class="skin-type-btn {selectedSkinType === key
                                ? 'active'
                                : ''}"
                            on:click={() => (selectedSkinType = key)}
                        >
                            {label}
                        </button>
                    {/each}
                </div>

                <!-- Product Recommendations -->
                <div class="product-recommendations">
                    <h3>
                        Recommended Products for {skinTypeLabels[
                            selectedSkinType
                        ]}
                    </h3>
                    <div class="products-grid">
                        {#each productRecommendations[selectedSkinType] as product}
                            <div class="product-card">
                                <div class="product-category">
                                    {product.category}
                                </div>
                                <h4>{product.name}</h4>
                            </div>
                        {/each}
                    </div>
                </div>

                <div class="disclaimer">
                    <p>
                        <strong>Note:</strong> These are general recommendations.
                        No product is guaranteed to work for everyone, even with
                        the same skin type. Always patch test new products and introduce
                        them gradually into your routine.
                    </p>
                </div>
            </div>
        {/if}

        {#if activeSection === "tips"}
            <div class="content-section">
                <h2>Korean Skincare Tips & Techniques</h2>

                <div class="tips-sections">
                    <div class="tip-section">
                        <h3>Double Cleansing Technique</h3>
                        <p>
                            Double cleansing is essential for removing all
                            traces of makeup, sunscreen, and daily buildup.
                            Start with an oil-based cleanser to dissolve makeup
                            and sunscreen, then follow with a water-based
                            cleanser to remove any remaining impurities.
                        </p>
                    </div>

                    <div class="tip-section">
                        <h3>The 7-Skin Method</h3>
                        <p>
                            This technique involves applying multiple thin
                            layers of toner (usually 3-7 layers) to deeply
                            hydrate the skin. Pat each layer gently into the
                            skin and wait for it to absorb before applying the
                            next. Perfect for dry or dehydrated skin.
                        </p>
                    </div>

                    <div class="tip-section">
                        <h3>Product Application Order</h3>
                        <p>
                            Always apply products from thinnest to thickest
                            consistency: toner → essence → serum → ampoule →
                            emulsion → moisturizer → oil → sunscreen. This
                            ensures proper absorption of all products.
                        </p>
                    </div>

                    <div class="tip-section">
                        <h3>Sunscreen Application</h3>
                        <p>
                            Use about 0.25-0.5 teaspoons of sunscreen for your
                            face and neck (about a two-finger length squeeze).
                            Apply sunscreen as the last step of your morning
                            routine, and reapply every 2 hours when outdoors.
                        </p>
                    </div>

                    <div class="tip-section">
                        <h3>Toner vs. Essence vs. Serum vs. Ampoule</h3>
                        <ul>
                            <li>
                                <strong>Toner:</strong> First step of hydration,
                                prepares skin for other products
                            </li>
                            <li>
                                <strong>Essence:</strong> Lightweight treatment with
                                active ingredients, more concentrated than toner
                            </li>
                            <li>
                                <strong>Serum:</strong> High concentration of active
                                ingredients for specific skin concerns
                            </li>
                            <li>
                                <strong>Ampoule:</strong> Most concentrated treatment,
                                often single-ingredient focused
                            </li>
                        </ul>
                    </div>

                    <div class="tip-section">
                        <h3>Using Face Masks</h3>
                        <p>
                            You can use masks daily if desired, but 2-3 times
                            per week is sufficient for most people. Choose
                            between wash-off masks for deep cleansing or sheet
                            masks for hydration and convenience.
                        </p>
                    </div>

                    <div class="tip-section">
                        <h3>Exfoliation Guidelines</h3>
                        <p>
                            All skin types benefit from gentle exfoliation, but
                            moderation is key. Start with once a week and
                            gradually increase to 2-3 times per week if your
                            skin tolerates it well. Over-exfoliation can damage
                            your skin barrier.
                        </p>
                    </div>
                </div>
            </div>
        {/if}
    </div>
</section>

<style lang="scss">
    .skincare-guide-page {
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
            margin: 0 auto 3rem;
            text-align: center;

            h1 {
                font-size: 2.5rem;
                // margin-bottom: 1rem;
                color: #1f2937;
            }

            .subtitle {
                font-size: 1.2rem;
                color: #6b7280;
                margin: 0;
            }
        }

        .guide-navigation {
            max-width: 1000px;
            margin: 0 auto 3rem;
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            justify-content: center;
            border-bottom: 2px solid #e5e7eb;
            padding-bottom: 1rem;

            .nav-tab {
                padding: 0.75rem 1.5rem;
                background: transparent;
                border: 2px solid #e5e7eb;
                border-radius: 0.5rem;
                color: #6b7280;
                font-weight: 500;
                cursor: pointer;
                transition: all 0.3s;

                &:hover {
                    border-color: #314438;
                    color: #314438;
                }

                &.active {
                    background-color: #314438;
                    border-color: #314438;
                    color: white;
                }
            }
        }

        .guide-content {
            max-width: 1000px;
            margin: 0 auto;

            .content-section {
                h2 {
                    font-size: 2rem;
                    margin-bottom: 1.5rem;
                    color: #1f2937;
                    text-align: center;
                }

                .section-intro {
                    font-size: 1.1rem;
                    color: #4b5563;
                    margin-bottom: 2rem;
                    text-align: center;
                    line-height: 1.6;
                }

                .intro-text {
                    margin-bottom: 3rem;

                    p {
                        margin-bottom: 1rem;
                        line-height: 1.6;
                        color: #374151;
                        font-size: 1.1rem;
                    }
                }

                .key-principles {
                    h3 {
                        font-size: 1.5rem;
                        margin-bottom: 1.5rem;
                        color: #1f2937;
                        text-align: center;
                    }

                    .principles-grid {
                        display: grid;
                        grid-template-columns: repeat(
                            auto-fit,
                            minmax(250px, 1fr)
                        );
                        gap: 1.5rem;

                        .principle-card {
                            background: white;
                            padding: 1.5rem;
                            border-radius: 0.5rem;
                            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);

                            h4 {
                                color: #314438;
                                margin-bottom: 0.5rem;
                                font-size: 1.1rem;
                            }

                            p {
                                color: #6b7280;
                                line-height: 1.5;
                                margin: 0;
                            }
                        }
                    }
                }

                .steps-container {
                    display: grid;
                    gap: 1rem;
                    margin-bottom: 2rem;

                    .step-card {
                        display: flex;
                        align-items: center;
                        background: white;
                        padding: 1.5rem;
                        border-radius: 0.5rem;
                        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);

                        .step-number {
                            width: 3rem;
                            height: 3rem;
                            background-color: #314438;
                            color: white;
                            border-radius: 50%;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            font-weight: bold;
                            font-size: 1.2rem;
                            margin-right: 1.5rem;
                            flex-shrink: 0;
                        }

                        .step-content {
                            h3 {
                                color: #1f2937;
                                margin-bottom: 0.5rem;
                                font-size: 1.2rem;
                            }

                            p {
                                color: #6b7280;
                                line-height: 1.5;
                                margin: 0;
                            }
                        }
                    }
                }

                .routine-note {
                    background: #fef3c7;
                    padding: 1.5rem;
                    border-radius: 0.5rem;
                    border-left: 4px solid #f59e0b;

                    h3 {
                        color: #92400e;
                        margin-bottom: 1rem;
                    }

                    ul {
                        color: #92400e;
                        margin: 0;

                        li {
                            margin-bottom: 0.5rem;
                        }
                    }
                }

                .simple-steps {
                    display: grid;
                    gap: 2rem;
                    margin-bottom: 2rem;

                    .simple-step-card {
                        background: white;
                        padding: 2rem;
                        border-radius: 0.75rem;
                        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);

                        .simple-step-number {
                            width: 4rem;
                            height: 4rem;
                            // background: linear-gradient(
                            //     135deg,
                            //     #314438,
                            //     #4ade80
                            // );
                            background: #314438;
                            color: white;
                            border-radius: 50%;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            font-weight: bold;
                            font-size: 1.5rem;
                            margin-bottom: 1rem;
                        }

                        .simple-step-content {
                            h3 {
                                color: #1f2937;
                                margin-bottom: 1rem;
                                font-size: 1.5rem;
                            }

                            .step-description {
                                color: #4b5563;
                                margin-bottom: 1rem;
                                line-height: 1.6;
                                font-size: 1.1rem;
                            }

                            .step-tips {
                                background: #f0fdf4;
                                padding: 1rem;
                                border-radius: 0.5rem;
                                border-left: 4px solid #22c55e;
                                color: #15803d;
                            }
                        }
                    }
                }

                .upgrade-note {
                    background: #ede9fe;
                    padding: 1.5rem;
                    border-radius: 0.5rem;
                    border-left: 4px solid #8b5cf6;

                    h3 {
                        color: #6b21a8;
                        margin-bottom: 1rem;
                    }

                    p {
                        color: #6b21a8;
                        line-height: 1.6;
                        margin: 0;
                    }
                }

                .skin-type-selector {
                    display: flex;
                    flex-wrap: wrap;
                    gap: 0.75rem;
                    justify-content: center;
                    margin-bottom: 2rem;

                    .skin-type-btn {
                        padding: 0.75rem 1.5rem;
                        background: white;
                        border: 2px solid #e5e7eb;
                        border-radius: 2rem;
                        color: #6b7280;
                        font-weight: 500;
                        cursor: pointer;
                        transition: all 0.3s;

                        &:hover {
                            border-color: #314438;
                            color: #314438;
                        }

                        &.active {
                            background-color: #314438;
                            border-color: #314438;
                            color: white;
                        }
                    }
                }

                .product-recommendations {
                    h3 {
                        text-align: center;
                        margin-bottom: 1.5rem;
                        color: #1f2937;
                    }

                    .products-grid {
                        display: grid;
                        grid-template-columns: repeat(
                            auto-fit,
                            minmax(280px, 1fr)
                        );
                        gap: 1rem;
                        margin-bottom: 2rem;

                        .product-card {
                            background: white;
                            padding: 1.5rem;
                            border-radius: 0.5rem;
                            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
                            border-left: 4px solid #314438;

                            .product-category {
                                background: #f3f4f6;
                                color: #6b7280;
                                padding: 0.25rem 0.75rem;
                                border-radius: 1rem;
                                font-size: 0.8rem;
                                font-weight: 500;
                                display: inline-block;
                                margin-bottom: 0.75rem;
                            }

                            h4 {
                                color: #1f2937;
                                margin: 0;
                                line-height: 1.4;
                            }
                        }
                    }
                }

                .disclaimer {
                    background: #fef2f2;
                    padding: 1.5rem;
                    border-radius: 0.5rem;
                    border-left: 4px solid #ef4444;

                    p {
                        color: #dc2626;
                        margin: 0;
                        line-height: 1.6;
                    }
                }

                .tips-sections {
                    display: grid;
                    gap: 2rem;

                    .tip-section {
                        background: white;
                        padding: 2rem;
                        border-radius: 0.75rem;
                        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);

                        h3 {
                            color: #314438;
                            margin-bottom: 1rem;
                            font-size: 1.3rem;
                        }

                        p {
                            color: #4b5563;
                            line-height: 1.6;
                            margin: 0;
                        }

                        ul {
                            color: #4b5563;
                            line-height: 1.6;
                            margin: 0;
                            padding-left: 1.5rem;

                            li {
                                margin-bottom: 0.5rem;

                                strong {
                                    color: #314438;
                                }
                            }
                        }
                    }
                }
            }
        }

        @media (max-width: 768px) {
            padding: 5rem 1rem;

            .header-section h1 {
                font-size: 2rem;
            }

            .guide-navigation {
                justify-content: flex-start;
                overflow-x: auto;
                padding-bottom: 1rem;

                .nav-tab {
                    white-space: nowrap;
                    min-width: fit-content;
                }
            }

            .content-section {
                .principles-grid {
                    grid-template-columns: 1fr;
                }

                .step-card {
                    flex-direction: column;
                    text-align: center;

                    .step-number {
                        margin-right: 0;
                        margin-bottom: 1rem;
                    }
                }

                .products-grid {
                    grid-template-columns: 1fr;
                }

                .skin-type-selector {
                    justify-content: flex-start;
                    overflow-x: auto;
                }
            }
        }
    }
</style>
