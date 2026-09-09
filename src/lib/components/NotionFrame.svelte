<script>
  /** @type {{ src: string, title?: string }} */
  let { src, title = 'Notion Page' } = $props();

  let loading = $state(true);

  function handleLoad() {
    loading = false;
  }
</script>

<div class="notion-container">
  {#if loading}
    <div class="notion-skeleton">
      <div class="skeleton-header">
        <div class="skeleton-bar wide"></div>
        <div class="skeleton-bar medium"></div>
      </div>
      <div class="skeleton-body">
        <div class="skeleton-bar full"></div>
        <div class="skeleton-bar full"></div>
        <div class="skeleton-bar short"></div>
        <div class="skeleton-bar full"></div>
        <div class="skeleton-bar medium"></div>
      </div>
    </div>
  {/if}

  <iframe
    {src}
    {title}
    class="notion-frame"
    class:loaded={!loading}
    onload={handleLoad}
    allow="autoplay"
    sandbox="allow-same-origin allow-scripts allow-popups allow-forms"
    loading="lazy"
  ></iframe>
</div>

<style>
  .notion-container {
    position: relative;
    width: 100%;
    height: calc(100dvh - 200px);
    min-height: 500px;
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid var(--color-border-default);
    background: var(--color-surface-secondary);
  }

  .notion-frame {
    width: 100%;
    height: 100%;
    border: none;
    opacity: 0;
    transition: opacity 0.5s var(--ease-out-expo);
  }

  .notion-frame.loaded {
    opacity: 1;
  }

  .notion-skeleton {
    position: absolute;
    inset: 0;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  .skeleton-header {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .skeleton-body {
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
  }

  .skeleton-bar {
    height: 14px;
    border-radius: 6px;
    background: linear-gradient(
      90deg,
      var(--color-surface-tertiary) 25%,
      var(--color-border-accent) 50%,
      var(--color-surface-tertiary) 75%
    );
    background-size: 200% 100%;
    animation: shimmer 1.5s infinite;
  }

  .skeleton-bar.wide { width: 60%; height: 22px; }
  .skeleton-bar.medium { width: 40%; }
  .skeleton-bar.short { width: 25%; }
  .skeleton-bar.full { width: 90%; }

  @keyframes shimmer {
    0% { background-position: -200% 0; }
    100% { background-position: 200% 0; }
  }
</style>
