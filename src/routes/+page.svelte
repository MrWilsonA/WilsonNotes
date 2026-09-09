<script>
  import SubjectCard from '$lib/components/SubjectCard.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import {
    Music,
    Atom,
    FlaskConical,
    Monitor,
    Languages,
    Palette
  } from '@lucide/svelte';

  const subjects = [
    {
      href: '/music',
      label: 'Music Theory',
      description: 'Teori musik, notasi, dan harmonic analysis berbasis LaTeX.',
      icon: Music,
      color: '#ec4899'
    },
    {
      href: '/physics',
      label: 'Physics',
      description: 'Mekanika klasik, elektromagnetisme, dan fisika modern.',
      icon: Atom,
      color: '#3b82f6'
    },
    {
      href: '/chemistry',
      label: 'Chemistry',
      description: 'Termodinamika, struktur molekul, dan kimia analitik.',
      icon: FlaskConical,
      color: '#10b981'
    },
    {
      href: '/cs',
      label: 'Computer Science',
      description: 'Catatan komprehensif CS tersinkronisasi dari Notion.',
      icon: Monitor,
      color: '#8b5cf6'
    },
    {
      href: '/music-language',
      label: 'Music Language',
      description: 'Bahasa musik, terminologi, dan interpretasi seni.',
      icon: Languages,
      color: '#f59e0b'
    },
    {
      href: '/arts',
      label: 'Arts',
      description: 'Seni visual, estetika, dan sejarah kesenian.',
      icon: Palette,
      color: '#ef4444'
    }
  ];
</script>

<svelte:head>
  <title>WilsonNotes — Arsip Akademik Digital</title>
</svelte:head>

<div class="homepage">
  <!-- Hero Section -->
  <section class="hero animate-fade-in">
    <div class="hero-badge">
      <span class="badge-dot"></span>
      <span>Open-Access Academic Compendium</span>
    </div>

    <h1 class="hero-title">
      <span class="title-line">Wilson</span><span class="title-accent">Notes</span>
    </h1>

    <p class="hero-subtitle">
      Arsip digital publik terpusat untuk catatan akademik, riset perkuliahan,
      teori musik berbasis LaTeX, dan integrasi repositori pengetahuan eksternal.
    </p>

    <div class="hero-stats">
      <div class="stat">
        <span class="stat-value">3</span>
        <span class="stat-label">PDF Subjects</span>
      </div>
      <div class="stat-divider"></div>
      <div class="stat">
        <span class="stat-value">3</span>
        <span class="stat-label">Notion Integrations</span>
      </div>
      <div class="stat-divider"></div>
      <div class="stat">
        <span class="stat-value">∞</span>
        <span class="stat-label">Knowledge</span>
      </div>
    </div>
  </section>

  <!-- Subjects Grid -->
  <section class="subjects-section">
    <h2 class="section-title animate-fade-in">Direktori Catatan</h2>
    <p class="section-desc animate-fade-in">Pilih subjek untuk menjelajahi catatan yang tersedia.</p>

    <div class="subjects-grid">
      {#each subjects as subject, i}
        <SubjectCard
          href={subject.href}
          label={subject.label}
          description={subject.description}
          icon={subject.icon}
          color={subject.color}
          index={i}
        />
      {/each}
    </div>
  </section>

  <!-- Tech Stack Section -->
  <section class="tech-section animate-fade-in">
    <h2 class="section-title">Arsitektur</h2>
    <div class="tech-grid">
      <div class="tech-item">
        <span class="tech-label">Framework</span>
        <span class="tech-value">SvelteKit</span>
      </div>
      <div class="tech-item">
        <span class="tech-label">Styling</span>
        <span class="tech-value">Tailwind CSS v4</span>
      </div>
      <div class="tech-item">
        <span class="tech-label">Deployment</span>
        <span class="tech-value">Static SSG</span>
      </div>
      <div class="tech-item">
        <span class="tech-label">PDF</span>
        <span class="tech-value">LaTeX → Browser</span>
      </div>
      <div class="tech-item">
        <span class="tech-label">Notes</span>
        <span class="tech-value">Notion Sync</span>
      </div>
      <div class="tech-item">
        <span class="tech-label">Icons</span>
        <span class="tech-value">Lucide</span>
      </div>
    </div>
  </section>

  <Footer />
</div>

<style>
  .homepage {
    padding: 2rem 2rem 0;
    max-width: 900px;
  }

  /* Hero */
  .hero {
    padding: 2.5rem 0 3rem;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.35rem 0.85rem;
    background: var(--color-surface-secondary);
    border: 1px solid var(--color-border-default);
    border-radius: 999px;
    font-size: 0.75rem;
    font-weight: 500;
    color: var(--color-text-secondary);
    margin-bottom: 1.5rem;
  }

  .badge-dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--color-accent-500);
    animation: pulse-subtle 2s ease infinite;
  }

  .hero-title {
    font-size: clamp(2.5rem, 6vw, 3.5rem);
    font-weight: 800;
    letter-spacing: -0.04em;
    line-height: 1.1;
    margin: 0 0 1rem;
  }

  .title-line {
    color: var(--color-text-primary);
  }

  .title-accent {
    background: linear-gradient(135deg, var(--color-accent-400), var(--color-accent-600));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-subtitle {
    font-size: 1rem;
    color: var(--color-text-secondary);
    max-width: 560px;
    line-height: 1.7;
    margin: 0 0 2rem;
  }

  .hero-stats {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    padding: 1rem 1.5rem;
    background: var(--color-surface-secondary);
    border: 1px solid var(--color-border-default);
    border-radius: 12px;
    width: fit-content;
  }

  .stat {
    display: flex;
    flex-direction: column;
    gap: 0.15rem;
  }

  .stat-value {
    font-family: var(--font-mono);
    font-size: 1.25rem;
    font-weight: 700;
    color: var(--color-text-primary);
  }

  .stat-label {
    font-size: 0.7rem;
    color: var(--color-text-tertiary);
    text-transform: uppercase;
    letter-spacing: 0.05em;
    font-weight: 500;
  }

  .stat-divider {
    width: 1px;
    height: 32px;
    background: var(--color-border-default);
  }

  /* Sections */
  .subjects-section {
    padding: 2rem 0;
  }

  .section-title {
    font-size: 1.25rem;
    font-weight: 700;
    letter-spacing: -0.02em;
    margin: 0 0 0.25rem;
  }

  .section-desc {
    font-size: 0.875rem;
    color: var(--color-text-tertiary);
    margin: 0 0 1.5rem;
  }

  .subjects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 0.75rem;
  }

  /* Tech Stack */
  .tech-section {
    padding: 2.5rem 0;
    border-top: 1px solid var(--color-border-subtle);
    margin-top: 1rem;
  }

  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 0.5rem;
    margin-top: 1rem;
  }

  .tech-item {
    padding: 0.85rem 1rem;
    background: var(--color-surface-secondary);
    border: 1px solid var(--color-border-default);
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
  }

  .tech-label {
    font-size: 0.68rem;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: var(--color-text-tertiary);
    font-weight: 500;
  }

  .tech-value {
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--color-text-primary);
  }

  @media (max-width: 768px) {
    .homepage {
      padding: 1.5rem 1.25rem 0;
    }

    .hero {
      padding-top: 4rem;
    }

    .subjects-grid {
      grid-template-columns: 1fr;
    }

    .hero-stats {
      flex-wrap: wrap;
      width: 100%;
    }
  }
</style>
