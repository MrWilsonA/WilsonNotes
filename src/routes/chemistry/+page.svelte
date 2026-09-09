<script>
  import PageHeader from '$lib/components/PageHeader.svelte';
  import NotesList from '$lib/components/NotesList.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import { FlaskConical } from '@lucide/svelte';

  const chapters = [
    {
      id: 'thermodynamics',
      title: 'Thermodynamics',
      description: 'Hukum termodinamika, entropi, dan kesetimbangan kimia.'
    },
    {
      id: 'molecular-structure',
      title: 'Molecular Structure',
      description: 'Ikatan kimia, geometri molekul, dan orbital.'
    }
  ];
</script>

<svelte:head>
  <title>Chemistry — WilsonNotes</title>
  <meta name="description" content="Catatan kimia: termodinamika, struktur molekul, dan kimia analitik." />
</svelte:head>

<div class="page-container">
  <PageHeader
    title="Chemistry"
    description="Termodinamika, struktur molekul, dan kimia analitik. Dokumen dikompilasi dari sumber LaTeX."
  />

  <NotesList
    title="Chemistry"
    pdfPath="/pdf/chemistry/"
    icon={FlaskConical}
    {chapters}
  />

  <Footer />
</div>

<style>
  .page-container {
    padding: 2rem 2rem 0;
    max-width: 960px;
    margin: 0 auto;
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  @media (max-width: 768px) {
    .page-container {
      padding: 1.5rem 1.25rem 0;
    }
  }
</style>
