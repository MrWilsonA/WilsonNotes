<script>
  import { page } from '$app/state';
  import {
    BookOpen,
    Music,
    Atom,
    FlaskConical,
    Monitor,
    Languages,
    Palette,
    Menu,
    X,
    ExternalLink
  } from '@lucide/svelte';

  let mobileOpen = $state(false);

  const navItems = [
    { href: '/', label: 'Beranda', icon: BookOpen },
    { href: '/music', label: 'Music', icon: Music },
    { href: '/physics', label: 'Physics', icon: Atom },
    { href: '/chemistry', label: 'Chemistry', icon: FlaskConical },
    { href: '/cs', label: 'Computer Science', icon: Monitor },
    { href: '/music-language', label: 'Music Language', icon: Languages },
    { href: '/arts', label: 'Arts', icon: Palette }
  ];

  function isActive(href) {
    if (href === '/') return page.url.pathname === '/';
    return page.url.pathname.startsWith(href);
  }

  function closeMobile() {
    mobileOpen = false;
  }
</script>

<!-- Desktop Sidebar -->
<nav class="nav-sidebar" aria-label="Main navigation">
  <div class="nav-header">
    <a href="/" class="nav-logo" onclick={closeMobile}>
      <span class="logo-icon">W</span>
      <span class="logo-text">WilsonNotes</span>
    </a>
  </div>

  <div class="nav-links">
    {#each navItems as item}
      <a
        href={item.href}
        class="nav-link"
        class:active={isActive(item.href)}
        onclick={closeMobile}
      >
        <item.icon size={18} strokeWidth={1.8} />
        <span>{item.label}</span>
      </a>
    {/each}
  </div>

  <div class="nav-footer">
    <a
      href="https://github.com/MrWilsonA/WilsonNotes"
      target="_blank"
      rel="noopener noreferrer"
      class="nav-link github-link"
    >
      <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
      <span>GitHub</span>
    </a>
  </div>
</nav>

<!-- Mobile Toggle Button -->
<button
  class="mobile-toggle"
  onclick={() => (mobileOpen = !mobileOpen)}
  aria-label="Toggle navigation"
>
  {#if mobileOpen}
    <X size={22} />
  {:else}
    <Menu size={22} />
  {/if}
</button>

<!-- Mobile Overlay -->
{#if mobileOpen}
  <!-- svelte-ignore a11y_no_static_element_interactions -->
  <div
    class="mobile-overlay"
    onclick={closeMobile}
    onkeydown={(e) => e.key === 'Escape' && closeMobile()}
    role="presentation"
  ></div>

  <nav class="mobile-nav" aria-label="Mobile navigation">
    <div class="nav-header">
      <a href="/" class="nav-logo" onclick={closeMobile}>
        <span class="logo-icon">W</span>
        <span class="logo-text">WilsonNotes</span>
      </a>
    </div>

    <div class="nav-links">
      {#each navItems as item}
        <a
          href={item.href}
          class="nav-link"
          class:active={isActive(item.href)}
          onclick={closeMobile}
        >
          <item.icon size={18} strokeWidth={1.8} />
          <span>{item.label}</span>
        </a>
      {/each}
    </div>

    <div class="nav-footer">
      <a
        href="https://github.com/MrWilsonA/WilsonNotes"
        target="_blank"
        rel="noopener noreferrer"
        class="nav-link github-link"
      >
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
        <span>GitHub</span>
      </a>
    </div>
  </nav>
{/if}

<style>
  .nav-sidebar {
    position: fixed;
    left: 0;
    top: 0;
    bottom: 0;
    width: 260px;
    background: var(--color-surface-secondary);
    border-right: 1px solid var(--color-border-default);
    display: flex;
    flex-direction: column;
    z-index: 40;
    overflow-y: auto;
    transition: transform 0.3s var(--ease-out-expo);
  }

  .nav-header {
    padding: 1.5rem 1.25rem 1rem;
    border-bottom: 1px solid var(--color-border-subtle);
  }

  .nav-logo {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    text-decoration: none;
    color: var(--color-text-primary);
  }

  .logo-icon {
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, var(--color-accent-500), var(--color-accent-600));
    border-radius: 10px;
    font-family: var(--font-mono);
    font-weight: 700;
    font-size: 1.1rem;
    color: white;
    flex-shrink: 0;
  }

  .logo-text {
    font-weight: 700;
    font-size: 1.1rem;
    letter-spacing: -0.02em;
  }

  .nav-links {
    flex: 1;
    padding: 0.75rem 0.75rem;
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .nav-link {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.6rem 0.75rem;
    border-radius: 8px;
    text-decoration: none;
    color: var(--color-text-secondary);
    font-size: 0.875rem;
    font-weight: 450;
    transition: all 0.2s var(--ease-out-expo);
    position: relative;
  }

  .nav-link:hover {
    color: var(--color-text-primary);
    background: var(--color-surface-tertiary);
  }

  .nav-link.active {
    color: var(--color-text-primary);
    background: var(--color-surface-tertiary);
  }

  .nav-link.active::before {
    content: '';
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    width: 3px;
    height: 60%;
    border-radius: 0 3px 3px 0;
    background: var(--color-accent-500);
  }

  .nav-footer {
    padding: 0.75rem;
    border-top: 1px solid var(--color-border-subtle);
  }

  .github-link {
    opacity: 0.6;
  }

  .github-link:hover {
    opacity: 1;
  }

  /* Mobile */
  .mobile-toggle {
    display: none;
    position: fixed;
    top: 1rem;
    right: 1rem;
    z-index: 50;
    width: 44px;
    height: 44px;
    border-radius: 12px;
    border: 1px solid var(--color-border-default);
    background: var(--color-surface-secondary);
    color: var(--color-text-primary);
    cursor: pointer;
    align-items: center;
    justify-content: center;
    transition: all 0.2s ease;
    backdrop-filter: blur(12px);
  }

  .mobile-toggle:hover {
    background: var(--color-surface-tertiary);
  }

  .mobile-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.6);
    backdrop-filter: blur(4px);
    z-index: 41;
  }

  .mobile-nav {
    display: none;
    position: fixed;
    left: 0;
    top: 0;
    bottom: 0;
    width: 280px;
    background: var(--color-surface-secondary);
    border-right: 1px solid var(--color-border-default);
    flex-direction: column;
    z-index: 42;
    overflow-y: auto;
    animation: slide-in 0.3s var(--ease-out-expo);
  }

  @keyframes slide-in {
    from { transform: translateX(-100%); }
    to { transform: translateX(0); }
  }

  @media (max-width: 768px) {
    .nav-sidebar {
      display: none;
    }

    .mobile-toggle {
      display: flex;
    }

    .mobile-overlay {
      display: block;
    }

    .mobile-nav {
      display: flex;
    }
  }
</style>
