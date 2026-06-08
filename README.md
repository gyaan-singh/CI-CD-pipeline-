# GitHub Pages Deployment

This repository automatically deploys to GitHub Pages whenever changes are pushed to the `main` branch.

Create the file `.github/workflows/deploy.yml` with the following content:

```yaml
name: Deploy Website

on:
  push:
    branches:
      - main

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Upload Artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: .

      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```

After committing and pushing this workflow, GitHub Actions will automatically deploy the website to GitHub Pages.
