<script>
  import { PUBLIC_NOTION_ARTS_URL } from '$env/static/public';
  import PageHeader from '$lib/components/PageHeader.svelte';
  import NotionFrame from '$lib/components/NotionFrame.svelte';
  import Footer from '$lib/components/Footer.svelte';

  const notionUrl = PUBLIC_NOTION_ARTS_URL || '';
</script>

<svelte:head>
  <title>Arts — WilsonNotes</title>
  <meta name="description" content="Catatan seni visual, estetika, dan sejarah kesenian tersinkronisasi dari Notion." />
</svelte:head>

<div class="page-container">
  <PageHeader
    title="Arts"
    description="Seni visual, estetika, dan sejarah kesenian yang tersinkronisasi dari Notion."
  />

  {#if notionUrl}
    <NotionFrame src={notionUrl} title="Arts Notes" />
  {:else}
    <div class="notion-placeholder animate-fade-in">
      <div class="placeholder-icon">
        <svg width="48" height="48" viewBox="0 0 48 48" fill="none">
          <rect x="8" y="6" width="32" height="36" rx="4" stroke="currentColor" stroke-width="2"/>
          <line x1="16" y1="16" x2="32" y2="16" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          <line x1="16" y1="22" x2="28" y2="22" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
          <line x1="16" y1="28" x2="24" y2="28" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
        </svg>
      </div>
      <h3>Notion belum terhubung</h3>
      <p>Atur <code>PUBLIC_NOTION_ARTS_URL</code> pada file <code>.env</code> untuk menampilkan catatan dari Notion.</p>
    </div>
  {/if}

  <Footer />
</div>

<style>
  .page-container {
    padding: 2rem 2rem 0;
    max-width: 1100px;
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  .notion-placeholder {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 4rem 2rem;
    border: 1px dashed var(--color-border-default);
    border-radius: 16px;
    background: var(--color-surface-secondary);
    color: var(--color-text-secondary);
    gap: 0.75rem;
  }

  .placeholder-icon {
    color: var(--color-text-tertiary);
    opacity: 0.4;
  }

  .notion-placeholder h3 {
    font-size: 1.1rem;
    font-weight: 600;
    margin: 0;
  }

  .notion-placeholder p {
    font-size: 0.85rem;
    color: var(--color-text-tertiary);
    margin: 0;
    max-width: 400px;
  }

  .notion-placeholder code {
    font-family: var(--font-mono);
    font-size: 0.8rem;
    background: var(--color-surface-tertiary);
    padding: 0.15rem 0.4rem;
    border-radius: 4px;
  }

  @media (max-width: 768px) {
    .page-container {
      padding: 5rem 1.25rem 0;
    }
  }
</style>
