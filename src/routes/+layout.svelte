<script>
  import './layout.css';
  import Navigation from '$lib/components/Navigation.svelte';

  let { children } = $props();
</script>

<svelte:head>
  <title>WilsonNotes — Arsip Akademik Digital</title>
  <meta name="description" content="Arsip digital publik terpusat untuk catatan akademik, riset perkuliahan, dan teori musik berbasis LaTeX." />
  <link rel="icon" href="/logo.jpg" />
</svelte:head>

<div class="app-layout">
  <Navigation />

  <main class="main-content">
    {@render children()}
  </main>
</div>

<style>
  .app-layout {
    min-height: 100dvh;
    display: flex;
    flex-direction: column;
  }

  .main-content {
    flex: 1;
    margin-top: 60px;
    display: flex;
    flex-direction: column;
  }
</style>
