# Quarto Data Science Portfolio Template

A streamlined Quarto website using the Bootswatch Spacelab theme, with navigation narrowed to Home (about + photo), Projects, Books, and Research. Includes contact icons for LinkedIn, X (Twitter), and GitHub. Fresh start from `quarto create project website`.

## Why this template?
- Solves image and R Markdown issues from Jekyll.
- Python-focused with Quarto's excellent notebook/rendering support.
- Clean, professional design with Spacelab theme (muted blues, responsive).
- Easy to customize and deploy to GitHub Pages.

## Getting Started

1. **Install Quarto**: https://quarto.org/docs/get-started/ or `brew install quarto`.

2. **Install Python dependencies** (for executing Python cells):
   ```bash
   pip install jupyter pyyaml
   ```

3. **Preview**:
   ```bash
   cd quarto-portfolio
   quarto preview
   ```

4. **Build**:
   ```bash
   quarto render
   ```
   Output in `docs/` for GitHub Pages.

5. **Customize**:
   - Update `_quarto.yml` navbar links/icons.
   - Edit `index.qmd` for your about content.
   - Add projects to `projects/*.qmd`.
   - Port books/reviews to `books.qmd`.
   - Expand `research.qmd` with full bibliography from `_bibliography/papers.bib`.

## Structure
```
quarto-portfolio/
├── _quarto.yml          # Config (Spacelab theme, navbar: Home/Projects/Books/Research)
├── index.qmd            # Home with about, photo, links
├── projects.qmd         # Project grid listing
├── books.qmd            # Book reviews/shelf
├── research.qmd         # Publications/research with bibliography
├── projects/
│   └── attrition.qmd    # Sample Python project
├── styles/
│   └── custom.scss      # Minor overrides for cards/typography
├── images/              # Profile and project images
├── references.bib       # Bibliography
└── docs/                # Built site
```

Run `quarto preview` to see the narrowed navigation and Spacelab theme. Contact icons in navbar right. Ready for your data science content.