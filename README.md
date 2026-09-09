# WilsonNotes

Arsip digital publik terpusat untuk catatan akademik, riset perkuliahan, teori musik berbasis LaTeX, dan integrasi repositori pengetahuan eksternal.

## Tech Stack

| Kategori | Teknologi |
|:---|:---|
| Framework UI | SvelteKit (Static Adapter) |
| Styling | Tailwind CSS v4 |
| Icons | Lucide (@lucide/svelte) |
| Deployment | Static SSG |

## Subjects

- **Music Theory** — Teori musik, notasi formal, harmonic analysis (PDF/LaTeX)
- **Physics** — Mekanika klasik, elektromagnetisme (PDF/LaTeX)
- **Chemistry** — Termodinamika, struktur molekul (PDF/LaTeX)
- **Computer Science** — Catatan CS tersinkronisasi dari Notion
- **Music Language** — Bahasa musik & terminologi dari Notion
- **Arts** — Seni visual & estetika dari Notion

## Setup

```bash
# Clone
git clone https://github.com/MrWilsonA/WilsonNotes.git
cd WilsonNotes

# Install dependencies
npm install

# Setup environment
cp .env.example .env
# Edit .env with your Notion public page URLs

# Development
npm run dev

# Build
npm run build
```

## Environment Variables

Copy `.env.example` to `.env` and fill in your Notion public page URLs:

```env
PUBLIC_NOTION_CS_URL="https://your-workspace.notion.site/..."
PUBLIC_NOTION_MUSIC_LANG_URL="https://your-workspace.notion.site/..."
PUBLIC_NOTION_ARTS_URL="https://your-workspace.notion.site/..."
```

## License

Open-access academic compendium. © WilsonNotes.
