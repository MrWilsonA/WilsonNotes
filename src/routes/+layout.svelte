<script>
  import './layout.css';
  import Navigation from '$lib/components/Navigation.svelte';
  import Footer from '$lib/components/Footer.svelte';

  let { children } = $props();
</script>

<svelte:head>
  <title>WilsonNotes — Arsip Akademik Digital</title>
  <meta name="description" content="Arsip digital publik terpusat untuk catatan akademik, riset perkuliahan, dan teori musik berbasis LaTeX." />
</svelte:head>

<div class="app-layout">
  <Navigation />

  <main class="main-content">
    {@render children()}
  </main>
</div>

<style>
  .app-layout {
    display: flex;
    min-height: 100dvh;
  }

  .main-content {
    flex: 1;
    margin-left: 260px;
    display: flex;
    flex-direction: column;
    min-height: 100dvh;
  }

  @media (max-width: 768px) {
    .main-content {
      margin-left: 0;
    }
  }
</style>
