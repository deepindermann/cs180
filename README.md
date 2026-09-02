# CS180 Project Site

Static site for CS180 (Fall 2026) project write-ups. No build step — plain HTML + one stylesheet.

```
index.html            landing page linking to each project
assets/css/style.css  shared styles for every page
assets/proj0/         published images for Project 0 (web-sized JPEG/GIF)
proj0/ … proj4/       one folder per project, each with an index.html
                      (only proj0 is linked from the landing page for now)
dev-assets/           working originals — gitignored, local only
```

## Local preview

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Adding content to a project

Put web-sized photos in `assets/<project>/` and swap the placeholder blocks:

```html
<div class="placeholder">image</div>
```

for a real image:

```html
<img src="../assets/proj0/your-photo.jpg" alt="Describe the photo">
```

Originals (HEIC, full-resolution) stay in `dev-assets/`, which git ignores. Export to
JPEG for the site:

```sh
sips -s format jpeg -s formatOptions 82 -Z 1600 dev-assets/IMG_1234.HEIC \
  --out assets/proj0/name.jpg
```

## Adding another project

Skeletons for `proj1/`–`proj4/` already exist but are not linked yet. When a project is
ready, add its `<li>` to the list in `index.html`. For a sixth project, copy `proj4/` to
`proj5/` and do the same.

## Publishing to GitHub Pages

1. Push this folder to a GitHub repo.
2. Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.
3. Site goes live at `https://<username>.github.io/<repo>/`.

## PDF for Gradescope

Open the project page, print to PDF, and enable "Headers and footers" in the browser print
dialog so the URL appears on the page.
