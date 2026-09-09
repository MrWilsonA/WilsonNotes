<script>
  /** @type {{ title: string, description?: string, backHref?: string, backLabel?: string }} */
  let { title, description = '', backHref = '/', backLabel = 'Kembali' } = $props();

  import { ArrowLeft } from '@lucide/svelte';
</script>

<div class="page-header animate-fade-in">
  <a href={backHref} class="back-button">
    <ArrowLeft size={16} strokeWidth={2} />
    <span>{backLabel}</span>
  </a>

  <h1 class="page-title">{title}</h1>

  {#if description}
    <p class="page-description">{description}</p>
  {/if}
</div>

<style>
  .page-header {
    margin-bottom: 2rem;
  }

  .back-button {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    font-size: 0.8rem;
    color: var(--color-text-tertiary);
    text-decoration: none;
    margin-bottom: 1.25rem;
    transition: color 0.2s ease;
    padding: 0.35rem 0;
  }

  .back-button:hover {
    color: var(--color-text-primary);
  }

  .page-title {
    font-size: 1.75rem;
    font-weight: 700;
    letter-spacing: -0.03em;
    margin: 0 0 0.5rem;
    line-height: 1.2;
  }

  .page-description {
    font-size: 0.9rem;
    color: var(--color-text-secondary);
    margin: 0;
    max-width: 600px;
    line-height: 1.6;
  }
</style>
