<script>
  /** @type {{ title: string, subtitle?: string, pdfPath: string, icon: any, chapters: Array<{id: string, title: string, description: string}> }} */
  let { title, subtitle = '', pdfPath, icon, chapters = [] } = $props();

  import { FileText, Download, ExternalLink } from '@lucide/svelte';
</script>

<div class="notes-list">
  {#if chapters.length > 0}
    <div class="chapters-grid">
      {#each chapters as chapter, i}
        <div class="chapter-card animate-fade-in-up stagger-{i + 1}">
          <div class="chapter-number">{String(i + 1).padStart(2, '0')}</div>
          <div class="chapter-info">
            <h3 class="chapter-title">{chapter.title}</h3>
            <p class="chapter-desc">{chapter.description}</p>
          </div>
          <div class="chapter-status">
            <span class="status-badge">Segera hadir</span>
          </div>
        </div>
      {/each}
    </div>
  {:else}
    <div class="empty-state animate-fade-in">
      <div class="empty-icon">
        <FileText size={40} strokeWidth={1.2} />
      </div>
      <h3 class="empty-title">Belum ada catatan</h3>
      <p class="empty-desc">
        Catatan PDF untuk topik ini sedang dalam persiapan. Silakan cek kembali nanti.
      </p>
    </div>
  {/if}
</div>

<style>
  .notes-list {
    margin-top: 0.5rem;
  }

  .chapters-grid {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .chapter-card {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.25rem;
    background: var(--color-surface-secondary);
    border: 1px solid var(--color-border-default);
    border-radius: 12px;
    transition: all 0.25s var(--ease-out-expo);
  }

  .chapter-card:hover {
    border-color: var(--color-border-accent);
    background: var(--color-surface-elevated);
  }

  .chapter-number {
    font-family: var(--font-mono);
    font-size: 0.75rem;
    font-weight: 600;
    color: var(--color-text-tertiary);
    width: 28px;
    flex-shrink: 0;
  }

  .chapter-info {
    flex: 1;
    min-width: 0;
  }

  .chapter-title {
    font-size: 0.9rem;
    font-weight: 550;
    margin: 0 0 0.15rem;
  }

  .chapter-desc {
    font-size: 0.78rem;
    color: var(--color-text-tertiary);
    margin: 0;
  }

  .status-badge {
    font-size: 0.7rem;
    font-weight: 500;
    color: var(--color-text-tertiary);
    background: var(--color-surface-tertiary);
    padding: 0.25rem 0.6rem;
    border-radius: 20px;
    white-space: nowrap;
  }

  /* Empty State */
  .empty-state {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 4rem 2rem;
    border: 1px dashed var(--color-border-default);
    border-radius: 16px;
    background: var(--color-surface-secondary);
  }

  .empty-icon {
    color: var(--color-text-tertiary);
    opacity: 0.4;
    margin-bottom: 1rem;
  }

  .empty-title {
    font-size: 1.1rem;
    font-weight: 600;
    margin: 0 0 0.4rem;
    color: var(--color-text-secondary);
  }

  .empty-desc {
    font-size: 0.85rem;
    color: var(--color-text-tertiary);
    margin: 0;
    max-width: 360px;
  }
</style>
