<script>
  import PageHeader from '$lib/components/PageHeader.svelte';
  import NotesList from '$lib/components/NotesList.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import { Music } from '@lucide/svelte';

  const chapters = [
    {
      id: 'fundamentals',
      title: 'Fundamentals of Music Theory',
      description: 'Notasi dasar, interval, skala, dan modes.'
    },
    {
      id: 'harmonic-analysis',
      title: 'Harmonic Analysis',
      description: 'Analisis harmoni, progresi akord, dan voice leading.'
    }
  ];
</script>

<svelte:head>
  <title>Music Theory — WilsonNotes</title>
  <meta name="description" content="Catatan teori musik berbasis LaTeX: notasi, interval, harmonic analysis." />
</svelte:head>

<div class="page-container">
  <PageHeader
    title="Music Theory"
    description="Teori musik, notasi formal, dan harmonic analysis. Dokumen dikompilasi dari sumber LaTeX."
  />

  <NotesList
    title="Music Theory"
    pdfPath="/pdf/music/"
    icon={Music}
    {chapters}
  />

  <Footer />
</div>

<style>
  .page-container {
    padding: 2rem 2rem 0;
    max-width: 900px;
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  @media (max-width: 768px) {
    .page-container {
      padding: 5rem 1.25rem 0;
    }
  }
</style>
