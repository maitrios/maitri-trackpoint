# Porting from upstream

maitri-trackpoint is a port of [ArtMoreno/omarchy-trackpoint](https://github.com/ArtMoreno/omarchy-trackpoint)
with paths and commands switched over to maitri. `.github/workflows/upstream-watch.yml` opens a `flare` issue
when upstream has commits newer than `reviewed` in `.maitri/upstream.toml`. A flare on the agent box works it.

## What to take

- Fixes and features for the widget, the middle button and the device handling.
- Rename on the way in: Omarchy commands, paths and plugin ids become maitri's (see the port commit
  `5eb4f59e` for the mapping). Keep upstream credit and the README's contributors section current.

## What to leave out

- Anything that only makes sense on Omarchy (its packages, its bar or menu paths).
- Changes already in this repo: check before porting, since the original port may have carried them.
- When unsure, leave it out and say why. A one-line reason for every skipped commit goes in the PR.

## Doing it

1. Port each upstream commit that applies as its own commit, keeping the upstream author.
2. Run the tests in `tests/` (`python3 -m pytest tests` or `python3 -m unittest`, whichever the suite
   uses) and say what you ran.
3. Set `reviewed` in `.maitri/upstream.toml` to the newest upstream commit you looked at, even if you took
   nothing.
4. Open the PR with the `upstream-sync` label and queue it with `gh pr merge --squash --auto`. Andrew's
   approval merges it. Users install from `main` (`maitri plugin add`), so merging is the release.
