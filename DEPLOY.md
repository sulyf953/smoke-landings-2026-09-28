# GitHub Pages flip (Offer Lab)

Repo content is the four smoke landings under `/shelfops` `/cutoverproof` `/heardly` `/file-cleanup`.

Once `gh` is authenticated on the box:

```bash
cd /workspace/offer-lab/smokes/gh-pages
git init -b main
git add -A
git -c user.email="noreply@local" -c user.name="Offer Lab" commit -m "smoke landings A/B/C/D"
# create private or public repo — Pages needs public OR GitHub Pro for private
gh repo create smoke-landings-2026-09-28 --public --source=. --remote=origin --push
gh api -X POST "repos/$(gh api user -q .login)/smoke-landings-2026-09-28/pages" \
  -f build_type=workflow -f source[branch]=main -f source[path]=/
# Or enable Pages in settings → Deploy from branch main / root
```

Public URLs (after Pages live):
- https://<user>.github.io/smoke-landings-2026-09-28/shelfops/
- https://<user>.github.io/smoke-landings-2026-09-28/cutoverproof/
- https://<user>.github.io/smoke-landings-2026-09-28/heardly/
- https://<user>.github.io/smoke-landings-2026-09-28/file-cleanup/
