# PuzzleFear Web deployment

This repository currently contains a **pre-exported Godot Web build** in the root.

## Automated deployment

The workflow at `.github/workflows/puzzlefear-web.yml` deploys to **GitHub Pages** on each push to `main`, and can also be started manually.

1. In GitHub repository **Settings → Pages**, set **Build and deployment → Source** to **GitHub Actions**.
2. In **Actions**, run **Build and deploy PuzzleFear Web** (or merge this PR into main).
3. Wait for a successful deployment and use the URL shown in the workflow's `github-pages` environment.

**Important:** This does not automatically update an existing Netlify URL. GitHub Pages availability for private repositories depends on the GitHub plan and repository settings.

## Godot source

Place the editable Godot project in `godot-source/` with:

- `godot-source/project.godot`
- `godot-source/export_presets.cfg` containing a Web preset named **Web**
- all scenes, scripts, images, sounds and other required source assets

Once this source is committed, the workflow automatically imports the project with Godot 4.7 and exports the Web build instead of copying the older root build.

Until then, the workflow **only republishes the existing exported build**; it does not regenerate the game. Keep the existing root Web files intact.

For Godot 4 Web export, ensure the Web preset is configured for browser compatibility, and check the Actions logs if the export fails. Large binary assets may require Git LFS or repository-size planning.

Do not upload signing credentials or tokens into the repository.
