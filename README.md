# Teaching Notes Site

Static site — no build step. Home / Subjects / Subject pages read everything from `data/subjects.json`.

## Add a new unit to an existing subject

1. Drop the PDF into `pdfs/<subject-id>/`, e.g. `pdfs/computer-organization/unit-6.pdf`.
2. Open `data/subjects.json`, find the subject, add a new entry to its `topics` array:

```json
{
  "id": "unit-6",
  "title": "Unit 6 — Your Title",
  "summary": "One-line description shown under the title.",
  "pdf": "pdfs/computer-organization/unit-6.pdf"
}
```

3. Commit and push. Netlify redeploys automatically.

## Add a whole new subject

1. Create a folder: `pdfs/<new-subject-id>/`, add its PDFs.
2. Add a new object to the `subjects` array in `data/subjects.json`:

```json
{
  "id": "daa",
  "name": "Design and Analysis of Algorithms",
  "code": "MCA1110",
  "description": "One-line subject description.",
  "topics": [
    { "id": "unit-1", "title": "Unit 1 — Title", "summary": "...", "pdf": "pdfs/daa/unit-1.pdf" }
  ]
}
```

3. Commit and push — it appears automatically on the Subjects page. No code changes needed.

## Converting PPTX to PDF before adding

If your source file is a `.pptx`, convert it to PDF first (LibreOffice, or "Save As PDF" from PowerPoint), then follow the steps above.

## Deploying on Netlify

1. Push this folder to a GitHub repo.
2. On [netlify.com](https://app.netlify.com) → **Add new site** → **Import an existing project** → pick your GitHub repo.
3. Build command: leave blank. Publish directory: `/` (repo root, since this is already static).
4. Deploy. Every future `git push` auto-redeploys.
