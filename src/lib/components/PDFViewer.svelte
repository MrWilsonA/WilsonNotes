<script>
  /** @type {{ src: string, title?: string }} */
  let { src, title = 'PDF Document' } = $props();

  let loading = $state(true);

  function handleLoad() {
    loading = false;
  }
</script>

<div class="pdf-viewer-container">
  {#if loading}
    <div class="pdf-loading">
      <div class="pdf-loading-icon">
        <div class="spinner"></div>
      </div>
      <p class="pdf-loading-text">Memuat dokumen...</p>
    </div>
  {/if}

  <iframe
    {src}
    {title}
    class="pdf-frame"
    class:loaded={!loading}
    onload={handleLoad}
    allow="autoplay"
    sandbox="allow-same-origin allow-scripts allow-popups"
  ></iframe>
</div>

<style>
  .pdf-viewer-container {
    position: relative;
    width: 100%;
    height: calc(100dvh - 200px);
    min-height: 500px;
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid var(--color-border-default);
    background: var(--color-surface-secondary);
  }

  .pdf-frame {
    width: 100%;
    height: 100%;
    border: none;
    opacity: 0;
    transition: opacity 0.4s var(--ease-out-expo);
  }

  .pdf-frame.loaded {
    opacity: 1;
  }

  .pdf-loading {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
  }

  .spinner {
    width: 32px;
    height: 32px;
    border: 3px solid var(--color-border-default);
    border-top-color: var(--color-accent-500);
    border-radius: 50%;
    animation: spin 0.8s linear infinite;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  .pdf-loading-text {
    color: var(--color-text-tertiary);
    font-size: 0.875rem;
  }
</style>
