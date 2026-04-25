<script>
    import Link from "$lib/components/Link.svelte";
</script>

<header class="top-bar">
    <div class="link">
        <Link title="siyu’s album" ref="/" />
    </div>

    <div class="content-right">
        <div class="link">
            <Link title="about" ref="/" />
        </div>
        <div class="link">
            <Link
            title="@1tt3r03d"
            ref="/"
            />
        </div>
    </div>
</header>

<style>
    .top-bar {
        height: 86px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: var(--spacing-6) var(--spacing-10);
    }

    .link {
        font-family: var(--font-secondary);
        font-size: 24px;
        line-height: 22px;
        color: var(--color-content-primary);
        text-decoration: none;
    }

    .content-right {
        display: flex;
        gap: var(--spacing-6);
        align-items: center;
    }
</style>