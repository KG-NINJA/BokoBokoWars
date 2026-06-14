# GitHub Pages Deployment

This folder is the complete static build of Crown Rescue March.

## Publish

1. Copy the contents of this folder to the root of a GitHub repository.
2. Open repository Settings > Pages.
3. Select Deploy from a branch.
4. Select the publishing branch and `/ (root)`.

No build command or server is required.

## Local Check

```bash
python3 -m http.server 8080 --directory github-pages
```

Open `http://localhost:8080`.
