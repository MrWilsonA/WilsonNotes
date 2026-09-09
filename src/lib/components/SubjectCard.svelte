<script>
  /** @type {{ href: string, label: string, description: string, icon: any, color?: string, index?: number }} */
  let { href, label, description, icon, color = 'var(--color-accent-500)', index = 0 } = $props();
</script>

<a {href} class="subject-card animate-fade-in-up stagger-{index + 1}" style="--card-accent: {color};">
  <div class="card-icon-wrapper">
    {#if icon}
      {@const Icon = icon}
      <Icon size={28} strokeWidth={1.6} />
    {/if}
  </div>

  <div class="card-content">
    <h3 class="card-title">{label}</h3>
    <p class="card-description">{description}</p>
  </div>

  <div class="card-arrow">
    <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
      <path d="M6 3L11 8L6 13" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  </div>

  <div class="card-glow"></div>
</a>

<style>
  .subject-card {
    position: relative;
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1.25rem 1.5rem;
    background: var(--color-surface-secondary);
    border: 1px solid var(--color-border-default);
    border-radius: 14px;
    text-decoration: none;
    color: var(--color-text-primary);
    transition: all 0.35s var(--ease-out-expo);
    overflow: hidden;
  }

  .subject-card:hover {
    border-color: var(--color-border-accent);
    transform: translateY(-3px);
    box-shadow: var(--shadow-card-hover);
  }

  .subject-card:hover .card-glow {
    opacity: 1;
  }

  .subject-card:hover .card-icon-wrapper {
    background: var(--card-accent);
    color: white;
    transform: scale(1.05);
  }

  .subject-card:hover .card-arrow {
    opacity: 1;
    transform: translateX(0);
  }

  .card-icon-wrapper {
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--color-surface-tertiary);
    border-radius: 12px;
    color: var(--card-accent);
    flex-shrink: 0;
    transition: all 0.35s var(--ease-out-expo);
  }

  .card-content {
    flex: 1;
    min-width: 0;
  }

  .card-title {
    font-size: 0.95rem;
    font-weight: 600;
    letter-spacing: -0.01em;
    margin: 0 0 0.2rem;
  }

  .card-description {
    font-size: 0.8rem;
    color: var(--color-text-tertiary);
    margin: 0;
    line-height: 1.4;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }

  .card-arrow {
    opacity: 0;
    transform: translateX(-4px);
    color: var(--color-text-tertiary);
    transition: all 0.3s var(--ease-out-expo);
    flex-shrink: 0;
  }

  .card-glow {
    position: absolute;
    inset: 0;
    background: radial-gradient(
      circle at 20% 50%,
      color-mix(in srgb, var(--card-accent) 5%, transparent) 0%,
      transparent 60%
    );
    opacity: 0;
    transition: opacity 0.4s ease;
    pointer-events: none;
  }
</style>
