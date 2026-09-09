<script>
  import PageHeader from '$lib/components/PageHeader.svelte';
  import NotesList from '$lib/components/NotesList.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import { Atom } from '@lucide/svelte';

  const chapters = [
    {
      id: 'classical-mechanics',
      title: 'Classical Mechanics',
      description: 'Hukum Newton, energi, momentum, dan dinamika rotasi.'
    },
    {
      id: 'electromagnetism',
      title: 'Electromagnetism',
      description: 'Medan listrik, medan magnet, dan persamaan Maxwell.'
    }
  ];
</script>

<svelte:head>
  <title>Physics — WilsonNotes</title>
  <meta name="description" content="Catatan fisika: mekanika klasik, elektromagnetisme, dan fisika modern." />
</svelte:head>

<div class="page-container">
  <PageHeader
    title="Physics"
    description="Mekanika klasik, elektromagnetisme, dan fisika modern. Dokumen dikompilasi dari sumber LaTeX."
  />

  <NotesList
    title="Physics"
    pdfPath="/pdf/physics/"
    icon={Atom}
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
