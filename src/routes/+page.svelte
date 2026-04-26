<script>

import Project from "$lib/components/Project.svelte";

    // Filter options
    const filters = [
        { label: 'overview', value: 'overview' },
        { label: '2026-2024', value: '2026-2024' },
        { label: '2023-2022', value: '2023-2022' }
    ];

    // 图片分组
        const images = [
            { src: '/images/project/2026-2024/001.jpg', group: '2026-2024', number: '001', year: '2026' },
            { src: '/images/project/2026-2024/002.jpg', group: '2026-2024', number: '002', year: '2026' },
            { src: '/images/project/2026-2024/003.jpg', group: '2026-2024', number: '003', year: '2026' },
            { src: '/images/project/2026-2024/004.jpg', group: '2026-2024', number: '004', year: '2026' },
            { src: '/images/project/2026-2024/005.jpg', group: '2026-2024', number: '005', year: '2025' },
            { src: '/images/project/2026-2024/006.jpg', group: '2026-2024', number: '006', year: '2024' },
            { src: '/images/project/2023-2022/007.jpg', group: '2023-2022', number: '007', year: '2023' },
            { src: '/images/project/2023-2022/008.JPG', group: '2023-2022', number: '008', year: '2022' },
            { src: '/images/project/2023-2022/009.JPG', group: '2023-2022', number: '009', year: '2022' },
            { src: '/images/project/2023-2022/010.JPG', group: '2023-2022', number: '010', year: '2022' },
            { src: '/images/project/2023-2022/011.jpg', group: '2023-2022', number: '011', year: '2022' },
            { src: '/images/project/2023-2022/012.jpg', group: '2023-2022', number: '012', year: '2022' }
        ];

    let currentFilter = $state('overview');

    // 过滤图片
    let filteredImages = $derived.by(() => {
        if (currentFilter === 'overview') return images;
        return images.filter(img => img.group === currentFilter);
    });
</script>

<section class="header">
    <p class="hero-text">
        This archive collects photos I've taken over the years, capturing what I've seen and felt, all with a compact camera my father gave me when I was twelve.
    </p>
</section>

<section class="desktop-page-content-filter">
    <div class="desktop-tab-navigation">
        <div class="tab-navigation">
            {#each filters as filter}
                <button
                    class="filter"
                    class:active={currentFilter === filter.value}
                    on:click={() => (currentFilter = filter.value)}
                >
                    <p class="filter-text">{filter.label}</p>
                </button>
            {/each}
        </div>
    </div>

   <div class="card-grid">
        {#each filteredImages as img}
            <Project 
                src={img.src} 
                number={img.number} 
                year={img.year} 
            />
        {/each}
    </div>
</section>

<style>
    .header {
        height: 590px;
        display: flex;
        align-items: center;
        padding: var(--spacing-11) var(--spacing-10);
    }

    .hero-text {
        font-family: var(--font-primary);
        font-weight: 700;
        font-size: 40px;
        line-height: normal;
        color: var(--color-content-primary);
        width: 1008px;
        margin: 0;
    }

    .desktop-page-content-filter {
        display: flex;
        flex-direction: column;
        gap: var(--spacing-7);
    }

    .desktop-tab-navigation {
        height: 48px;
        position: relative;
    }

    .tab-navigation {
        display: flex;
        gap: var(--spacing-7);
        align-items: center;
        position: absolute;
        left: 0;
        top: 0;
        padding-left: var(--spacing-10);
        width: 1512px;
    }

    .filter {
        background: none;
        border: none;
        padding: var(--spacing-2) var(--spacing-4);
        border-radius: var(--radius-full);
        cursor: pointer;
        font: inherit;
    }

    .filter.active {
        background: var(--color-filter-background-selected);
    }

    .filter-text {
        font-family: var(--font-secondary);
        font-size: 24px;
        color: var(--color-content-primary);
        margin: 0;
    }

    .filter.active .filter-text {
        color: var(--color-filter-content-selected);
    }

.card-grid {
        display: grid;
        grid-template-columns: repeat(2, fit-content(100%));
        gap: 24px 24px;
        padding: 0 var(--spacing-10);
    }

    .text-content {
        display: flex;
        font-family: var(--font-primary);
        font-weight: 700;
        font-size: 24px;
        line-height: normal;
        gap: var(--spacing-2);
    }

    .primary {
        color: var(--color-content-primary);
    }

    .secondary {
        color: var(--color-content-secondary);
    }

    @media (max-width: 744px) {
        .header {
            height: auto;
            padding: var(--spacing-7) var(--spacing-5);
        }

        .hero-text {
            font-size: var(--size-7); /* 40px on tablet per Figma */
            width: 100%;
        }

        .desktop-tab-navigation {
            height: auto;
        }

        .tab-navigation {
            position: static;
            width: 100%;
            padding: 0 var(--spacing-5);
            gap: var(--spacing-4);
            flex-wrap: wrap;
        }

        .filter {
            padding: var(--spacing-3) var(--spacing-4);
        }

        .filter-text {
            font-size: 20px;
        }

        .card-grid {
            grid-template-columns: 1fr;
            gap: var(--spacing-6);
            padding: 0 var(--spacing-5);
            justify-items: stretch;
        }
    }

    @media (max-width: 402px) {
        .header {
            padding: var(--spacing-5) var(--spacing-4);
        }

        .hero-text {
            font-size: 24px;
        }

        .tab-navigation {
            padding: 0 var(--spacing-4);
            gap: var(--spacing-3);
        }

        .filter {
            padding: var(--spacing-2) var(--spacing-3);
        }

        .filter-text {
            font-size: 18px;
        }

        .card-grid {
            gap: var(--spacing-5);
            padding: 0 var(--spacing-4);
        }
    }
</style>