<script>
    import Icon from "./Icon.svelte";
    let { src, number, year } = $props();
</script>

<div class="card">
    <div class="img-container">
        <div class="veil"></div>
        <img {src} alt="Project image" />
    </div>

    <div class="text-row">
        <div class="text-content">
            <span class="primary">{number}</span>
            <span class="secondary">/ {year}</span>
        </div>
        
        <div class="icon-wrapper">
            <Icon name="arrow-up-right" />
        </div>
    </div>
</div>

<style>
    .card {
        display: flex;
        flex-direction: column;
        gap: var(--spacing-2);
        width: 664px;
    }

    .img-container {
        position: relative;
        aspect-ratio: 664 / 400;
        overflow: hidden;
    }

    .veil {
        position: absolute;
        inset: 0;
        background-color: var(--color-link);
        mix-blend-mode: soft-light;
        opacity: 0;
        transition: opacity 0.4s ease;
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    /* 新的布局：让文字和图标水平分布 */
    .text-row {
        display: flex;
        justify-content: space-between; /* 关键：文字在左，图标在右 */
        align-items: center;
    }

    .text-content {
        display: flex;
        gap: 8px;
        font-family: var(--font-primary);
        font-weight: 700;
        font-size: 24px;
    }

    .primary { color: var(--color-content-primary); }
    .secondary { color: var(--color-content-secondary); }

    /* 图标动画 */
    .icon-wrapper {
        font-size: 24px; /* 调整图标大小 */
        color: var(--color-content-primary);
        opacity: 0;
        transform: translateY(10px); /* 初始位置偏下 */
        transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
    }

    @media (max-width: 744px) {
        .card {
            display: flex;
            width: min(664px, 100%);
            flex-direction: column;
            align-items: flex-start;
            gap: var(--spacing-2, 8px);
        }

        .img-container {
            aspect-ratio: 664 / 400;
        }

        .text-content {
            gap: 6px;
            font-size: 20px;
        }

        .icon-wrapper {
            font-size: 20px;
        }
    }

    @media (max-width: 402px) {
        .card {
            width: 100%;
        }

        .img-container {
            aspect-ratio: 1 / 0.75;
        }

        .text-content {
            font-size: 18px;
        }

        .icon-wrapper {
            font-size: 18px;
        }
    }

    /* Hover 触发整体联动 */
    .card:hover .veil {
        opacity: 1;
    }

    .card:hover .icon-wrapper {
        opacity: 1;
        transform: translateY(0); /* 向上滑动并显示 */
    }
</style>