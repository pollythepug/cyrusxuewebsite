# Cyrus Xue site: Cloudflare Pages deployment

A static site: no build step, no dependencies. Everything to publish is in `public/`.

```
public/
  index.html      the whole site (4 tabs)
  _headers        Cloudflare cache and security headers
  assets/         images and animation clips
  docs/           PDFs (embedded) plus original .pptx / .docx (download links)
wrangler.toml     Pages project settings
```

## Option A: drag and drop (easiest)
1. Cloudflare dashboard > Workers & Pages > Create > Pages > Upload assets.
2. Name the project, then drag in the **`public`** folder (or a zip of its contents).
3. Click Deploy. You get a `*.pages.dev` address.

## Option B: Wrangler CLI
```
npm install -g wrangler
wrangler login
wrangler pages deploy public --project-name cyrus-xue-site
```

## Option C: Git
Push this folder to GitHub, then in Cloudflare choose Connect to Git and set:
- Framework preset: None
- Build command: (leave empty)
- Build output directory: `public`

## Custom domain
In the Pages project open Custom domains > Set up a domain.

## Editing
- Colors (cream, forest green, orange, matching MotionLab) live in the `:root` block at the top of `public/index.html` (`--bg`, `--accent`, and so on).
- Replace a PDF in `public/docs/` with the same file name to update an embed.
- To change the music video, edit the YouTube ID `pZMkKNXLwQ4` in `index.html`.
