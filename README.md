# Tasks

Omarchy widget `io.github.dexterhere.tasks`: open task count, tasks due today and a short list of task titles. A **spec widget**: three JSON files, no code, no network, no files, no programs.

## Status

Pre-release (0.1.0). Spec only.

- There is no code in this repository, only `manifest.json`, `widget.json` and `layout.json`.
- The `tasks.list` topic (`open`, `dueToday`, `titles`) is in the website's provider catalog (class `personal`, auth `none`), but no tasks provider exists yet. Status is **planned**: the widget cannot show real data until one ships. This repository does not say where task data will come from, because the catalog does not say.
- The desktop renderer does not exist yet either. The layout schema is DRAFT v0 and may change.

## Privacy

Task titles can be private (names, projects, errands). The `titles` field is shown on your screen by the `list`, `minimal` and `detailed` variants, so anyone who can see your desktop or a screenshot can read them. The `count`, `due` and `chip` variants show numbers only and never read `titles`.

## Variants

Variant names are in `widget.json`, trees in `layout.json`. The default (`root`) is `detailed`.

| Variant    | Shows                                  | Reads                        | Size class |
| ---------- | -------------------------------------- | ---------------------------- | ---------- |
| `list`     | header and up to 5 titles              | `titles`                     | compact    |
| `count`    | open count                             | `open`                       | compact    |
| `due`      | due-today count                        | `dueToday`                   | compact    |
| `chip`     | check icon and open count, for the bar | `open`                       | chip       |
| `minimal`  | up to 3 titles, nothing else           | `titles`                     | compact    |
| `detailed` | open and due counts, divider, titles   | `open`, `dueToday`, `titles` | wide       |

There is no ring or bar variant: those need a 0 to 100 style number, and the catalog has only counts and titles, so a ring of a count would be misleading.

## Settings

None. A layout is plain data with no expressions, so it cannot honour a setting such as an item limit. `settings` is empty on purpose; the list limits are fixed in the layout.

## Access

Reads `tasks.list` (`open`, `dueToday`, `titles`) only. Network, files, programs: none. No secrets.

## Install and removal

Not installable yet (no renderer, no tasks provider). When the tooling exists, install from the Omarchy widget registry listing and remove it the same way.

## Licence

MIT, see `LICENSE`.
