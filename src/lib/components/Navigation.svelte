<script>
  import { page } from '$app/state';
  import { Menu, X } from '@lucide/svelte';

  let mobileOpen = $state(false);

  const navItems = [
    { href: '/', label: 'Beranda' },
    { href: '/music', label: 'Music' },
    { href: '/physics', label: 'Physics' },
    { href: '/chemistry', label: 'Chemistry' },
    { href: '/cs', label: 'Computer Science' },
    { href: '/music-language', label: 'Music Language' },
    { href: '/arts', label: 'Arts' }
  ];

  function isActive(href) {
    if (href === '/') return page.url.pathname === '/';
    return page.url.pathname.startsWith(href);
  }

  function closeMobile() {
    mobileOpen = false;
  }
</script>

<header class="topbar">
  <div class="topbar-inner">
    <!-- Logo -->
    <a href="/" class="nav-logo" onclick={closeMobile}>
      <img src="/logo.jpg" alt="WilsonNotes" class="logo-img" />
      <span class="logo-text">WilsonNotes</span>
    </a>

    <!-- Desktop Nav Links -->
    <nav class="nav-links-desktop" aria-label="Main navigation">
      {#each navItems as item}
        <a
          href={item.href}
          class="nav-link"
          class:active={isActive(item.href)}
        >
          {item.label}
        </a>
      {/each}
    </nav>

    <!-- Right side: GitHub + Mobile Toggle -->
    <div class="nav-right">
      <a
        href="https://github.com/MrWilsonA/WilsonNotes"
        target="_blank"
        rel="noopener noreferrer"
        class="github-link"
        aria-label="GitHub"
      >
        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
      </a>

      <button
        class="mobile-toggle"
        onclick={() => (mobileOpen = !mobileOpen)}
        aria-label="Toggle navigation"
      >
        {#if mobileOpen}
          <X size={20} />
        {:else}
          <Menu size={20} />
        {/if}
      </button>
    </div>
  </div>

  <!-- Mobile dropdown -->
  {#if mobileOpen}
    <nav class="mobile-dropdown" aria-label="Mobile navigation">
      {#each navItems as item}
        <a
          href={item.href}
          class="mobile-link"
          class:active={isActive(item.href)}
          onclick={closeMobile}
        >
          {item.label}
        </a>
      {/each}
    </nav>
  {/if}
</header>

<style>
  .topbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 50;
    background: var(--color-surface-primary);
    border-bottom: 1px solid var(--color-border-default);
    backdrop-filter: blur(12px);
  }

  .topbar-inner {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1.5rem;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
  }

  /* Logo */
  .nav-logo {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    text-decoration: none;
    color: var(--color-text-primary);
    flex-shrink: 0;
  }

  .logo-img {
    width: 32px;
    height: 32px;
    border-radius: 8px;
    object-fit: cover;
  }

  .logo-text {
    font-weight: 700;
    font-size: 1.05rem;
    letter-spacing: -0.02em;
  }

  /* Desktop Nav */
  .nav-links-desktop {
    display: flex;
    align-items: center;
    gap: 0.25rem;
    flex: 1;
    justify-content: center;
  }

  .nav-link {
    padding: 0.4rem 0.75rem;
    border-radius: 6px;
    text-decoration: none;
    color: var(--color-text-tertiary);
    font-size: 0.82rem;
    font-weight: 450;
    transition: all 0.2s ease;
    white-space: nowrap;
  }

  .nav-link:hover {
    color: var(--color-text-primary);
    background: var(--color-surface-secondary);
  }

  .nav-link.active {
    color: var(--color-accent-500);
    background: var(--color-surface-secondary);
  }

  /* Right side */
  .nav-right {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    flex-shrink: 0;
  }

  .github-link {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border-radius: 8px;
    color: var(--color-text-tertiary);
    transition: all 0.2s ease;
  }

  .github-link:hover {
    color: var(--color-text-primary);
    background: var(--color-surface-secondary);
  }

  /* Mobile toggle */
  .mobile-toggle {
    display: none;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border-radius: 8px;
    border: none;
    background: transparent;
    color: var(--color-text-primary);
    cursor: pointer;
    transition: background 0.2s ease;
  }

  .mobile-toggle:hover {
    background: var(--color-surface-secondary);
  }

  /* Mobile dropdown */
  .mobile-dropdown {
    display: none;
    flex-direction: column;
    padding: 0.5rem 1rem 1rem;
    border-top: 1px solid var(--color-border-default);
    animation: dropdown 0.2s ease;
  }

  @keyframes dropdown {
    from { opacity: 0; transform: translateY(-8px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .mobile-link {
    padding: 0.65rem 0.75rem;
    border-radius: 8px;
    text-decoration: none;
    color: var(--color-text-secondary);
    font-size: 0.9rem;
    font-weight: 450;
    transition: all 0.2s ease;
  }

  .mobile-link:hover {
    background: var(--color-surface-secondary);
    color: var(--color-text-primary);
  }

  .mobile-link.active {
    color: var(--color-accent-500);
    background: var(--color-surface-secondary);
  }

  @media (max-width: 768px) {
    .nav-links-desktop {
      display: none;
    }

    .mobile-toggle {
      display: flex;
    }

    .mobile-dropdown {
      display: flex;
    }
  }
</style>
