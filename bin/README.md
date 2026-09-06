# bin/ — site tooling

Small stdlib-only Ruby/bash helpers for running and updating the site.

| Script | What it does |
|---|---|
| `bin/serve` | Preview locally with drafts shown. Uses `bundle exec jekyll` when the bundle works, otherwise the system `jekyll` gem (moves `Gemfile` aside temporarily, restores on exit). |
| `bin/new-post "Title" [opts]` | Scaffold a post/draft with standard front matter. |
| `bin/videos-to-posts [opts]` | Generate one **draft** post per YouTube video from the transcripts in the second-brain repo. Idempotent. |
| `bin/publish-draft <file> \| --all` | Move a reviewed draft into `_posts/<year>/`, dated from its front matter. |

Commit + push publishes — GitHub Pages builds automatically. `_drafts/` is git-ignored.

## Local preview

```bash
bin/serve            # http://127.0.0.1:4000 , drafts visible, auto-rebuild on save
```

The machine's system Ruby (2.6) can't compile some native gems, so `bundle install`
currently fails. `bin/serve` works around it. For the full toolchain (livereload,
`bundle`), install a modern Ruby — `brew install ruby` or `rbenv install 3.3.x` —
then `bundle install`.

## New written post

```bash
bin/new-post "Splunking Widgets" --subtitle "A short guide" \
  --category General --tags Splunk,HowTo --draft
bin/serve                      # review at /
bin/publish-draft _drafts/2026-09-05-splunking-widgets.md
git add -A && git commit -m "New post: Splunking Widgets" && git push
```

Drop `--draft` to write straight to `_posts/<year>/`.

## YouTube videos → posts

Content source: the cleaned transcripts in the **second-brain** repo
(`~/Documents/second-brain/raw/yt-*.md`), which are read-only here.

```bash
bin/videos-to-posts --limit 3        # try a few
bin/videos-to-posts --limit 3        # again — reports "skip" for each (idempotent)
bin/videos-to-posts                  # full backfill (~one draft per video)
```

Each draft gets: `layout: post`, `categories: [Videos]`, auto-derived `tags:`, the
YouTube thumbnail, `video-id`, a blank `subtitle:` for you to fill, the video
description as a lead-in, a `{% raw %}{% include youtube.html %}{% endraw %}` embed, and the full transcript
under `## Transcript`.

Idempotency: a video is skipped if its ID already appears in any `_posts/**` file
or `_drafts/` file. Re-run any time you add new transcripts. `--force` regenerates.

Options: `--source DIR`, `--out DIR`, `--limit N`, `--only <id-or-slug>`,
`--force`, `--dry-run`.

### Review & publish workflow

1. `bin/videos-to-posts`
2. `bin/serve`, skim the drafts at `/`, delete any you don't want, set `subtitle:`
   and `featured:` where useful.
3. `bin/publish-draft --all` (keeps each video's original date) — or publish
   selectively by passing individual files.
4. Commit + push.

New video later: add its transcript to the second-brain repo, re-run
`bin/videos-to-posts`, publish the one new draft.
