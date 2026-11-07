# jlgm.me

Single static page. No build step. The only external dependency is the Anonymous Pro font from Google Fonts.

The layout is a two-column hero: bio and projects on the left, three terminal windows on the right that type out the resume (`whoami`/`pwd`, `work.log`, `education.log`). Clicking a terminal skips the typing. On phones the terminals come right after the bio, then projects, then the links.

## Deploy (GitHub Pages)

1. Push this folder to a GitHub repo (e.g. `jlgm/jlgm.me`).
2. Repo → Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/`.
3. In GoDaddy DNS for jlgm.me:
   - `A` records for `@` → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
   - `CNAME` record for `www` → `<your-github-username>.github.io`
4. Back in GitHub Pages settings, set custom domain to `jlgm.me` and enable "Enforce HTTPS" once the DNS check passes.

The `CNAME` file in this repo tells GitHub Pages which domain to serve.

## Colors

The palette is the `:root` block at the top of `index.html`: violet-black background with a purple glow at the top, lavender text and muted labels, terminal green (`--accent`) for the prompt, current job and caret glow, and magenta (`--link`) for links and icon hovers. The terminal windows have their own `--term-*` variables.

## Editing the resume

The terminal contents live in the `scripts` object at the bottom of `index.html`. Each window is a list of steps: `prompt` prints the prompt, `type` types a command, `out` prints HTML output instantly. The `row()` helper builds a year / role / company line.

## Preview

```
python3 -m http.server 8765
```
