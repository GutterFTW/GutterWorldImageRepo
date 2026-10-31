# Image repository maintenance

Read [README.md](README.md) for purpose and URL usage, the
[asset catalog](ASSET-CATALOG.md) for exact tracked paths, and
[AGENTS.md](AGENTS.md) for agent navigation rules. This guide describes an
auditable maintenance workflow; unresolved artwork or product choices are
listed below instead of being inferred from filenames.

## Repository boundary

The repository is the image collection and its documentation. The measured
baseline has no application code, package manager, build command, automated
test suite, GitHub Actions workflow, Unity scene, `.meta` files, or dependency
lock. `.gitattributes` contains `* text=auto`; it does not configure Git LFS or an
image conversion step. The PNGs are ordinary Git blobs.

Do not add consumer projects, generated Unity import files, local editor caches,
credentials, or unrelated artwork as a side effect of a documentation change.
Existing local work and untracked files must be preserved. An asset change is
separate from changing a consuming world's configuration or publishing it.

## Inspect before editing

Run these commands from the image repository, not from a containing workspace:

```sh
git status --short
git branch --show-current
git remote get-url origin
git ls-tree -r --name-only HEAD
```

The remote should identify `GutterFTW/GutterWorldImageRepo`. Inspect any existing
diff before writing; keep the task on its own branch/check-out when another
session owns work. A sparse checkout may omit image files from disk even though
the Git tree lists them. Inspect `git sparse-checkout list` if sparse mode is
enabled, and materialize only the assets needed for the task. Do not interpret
an omitted working-tree folder as a deleted or untracked remote asset.

For a specific path's history or metadata:

```sh
git log --oneline -- TSL-Images/2025_10.14_Emission.png
git ls-tree HEAD -- TSL-Images/2025_10.14_Emission.png
```

The commands locate the tracked object without introducing a build or image
tool dependency. Open the actual PNG in a decoder/editor for visual review;
read its image properties to measure dimensions and alpha handling. Keep those
observations separate from the consuming application's rendering results.

## Change workflows

### Add an image

1. Establish the intended artwork, destination folder, filename, audience,
   permissions, and consumer. No repository-wide naming or dimension rule has
   been approved in the tracked docs.
2. Inspect the proposed PNG with an image decoder. Record pixel dimensions,
   file size, visible content, and transparency expectations. Confirm acceptable
   size and aspect ratio with the consumer rather than using another logo's
   dimensions as an assumed limit.
3. Add the intended file and its catalog row only. Inspect the staged paths so
   source-editor backups, private artwork, and incidental local files are not
   included.
4. Provide the exact future branch/raw URL or intended pinned revision to the
   consumer owner. A new file does not update any external URL automatically.
5. Run the applicable checks below, then submit the scoped change for review.

### Replace an image at the same path

First decide whether the path is meant to be a changing alias or whether the
consumer needs a new versioned filename. That choice affects existing URLs and
must come from the owner/consumer requirements; there is no tracked alias policy.

For an authorized same-path replacement, compare old and new dimensions, aspect
ratio, alpha, and artwork. Update its catalog row and describe which configured
URLs may see different bytes. Consumers pinned to an earlier commit still
select that earlier version. Branch URLs, request caches, and application caches
can have different refresh behavior; verify the observed behavior rather than
promising an immediate update or a cache-purge mechanism.

### Rename, move, or retire an image

Treat the exact path as a compatibility surface. Identify references before
removing it. No consumer inventory is stored here, so an empty search within
this repository cannot prove that a URL is unused. If the consumers or retention
decision are unknown, leave the existing file intact and record the missing
decision for the owner. A rename changes the path a consumer requests; Git's
rename detection does not define HTTP redirect behavior.

When a retirement or migration is authorized, record the old/new exact URLs,
the consumers that need updating, any agreed overlap period, and the checks
performed. Never infer that an old date or `temp` in a filename authorizes its
deletion.

### Recover an incorrect replacement

Use the file history to identify known-good bytes. Make a focused corrective
commit or a scoped Git revert through the normal branch/PR workflow; avoid
resetting shared history or force-pushing. Recheck URLs and the consumer after
the correction. A Git correction does not demonstrate that a running client's
cache has refreshed.

## Validation and evidence

There is no repository-defined automated image validator. The following checks
are a maintenance checklist, not a claim that an application test suite exists.

| Check | Method and expected evidence |
|---|---|
| Scope | Review `git status --short`, the staged path list, and `git diff --stat`; only intended files changed. |
| Text hygiene | `git diff --check` reports no whitespace errors. Review Markdown links and exact path case against the tracked tree. |
| File identity | The actual bytes decode as the stated format. Inspect the decoded image; a header or suffix alone is insufficient. |
| Catalog | The affected path, dimensions, bytes, and encoding match the proposed asset. Record the commit or blob ID used for comparison. |
| Appearance | Inspect at expected display size; check transparency edges, cropping, readable artwork, and aspect ratio. Record the viewer and result. |
| HTTP | After authorized publication, request the exact raw URL; record status and Content-Type. A HEAD success verifies the HTTP response metadata, not full decode or client rendering. |
| Consumer | In the actual consuming project, test the intended URL/reference, loading/failure behavior, aspect ratio, cache refresh, and relevant platforms. Record environment and result. |
| Compatibility | For replacements/retirement, record affected consumers and URLs, migration decisions, and any agreed retention. |

Record each check as **passed**, **failed**, or **not run**, with date, revision,
environment/tool, expected outcome, observed outcome, and evidence. For a
documentation-only change, do not claim newly executed asset-rendering or
consumer-runtime acceptance.

### Documentation audit evidence: 2026-10-31

The audit inspected the tree at `ae3644f` and initial documentation head
`daacdc5`. It compared 16 existing PNGs with their tracked Git blob hashes and
read their signatures/IHDR dimensions: **passed**. Asset count and sizes in the
catalog match the tracked tree: **passed**. A representative image's `main` and
commit-pinned raw URLs returned 200 / `image/png` / 35,113 bytes in HEAD requests:
**passed**. These checks did not change or re-encode any image.

Full image decode/visual acceptance, consuming-project inspection, cache
refresh, Unity/VRChat import, multi-client display, and platform acceptance were
**not run**. No consumer configuration or runtime is tracked here. The remaining
checks must be performed for an actual asset/integration change in its own
environment; this evidence does not certify them.

## Unresolved owner decisions

| Gap | Decision/evidence needed before work that depends on it |
|---|---|
| Consumer inventory | Which projects, worlds, pages, or other clients use each image; exact URLs, references, settings, and contacts/owners. |
| Artwork rights | Who holds rights to each image, authorized uses/audiences, required credit, and any restrictions. No license/permission manifest is tracked. |
| Technical constraints | Approved file formats, dimensions, aspect ratios, alpha/color expectations, and size budgets for each actual consumer. Current file properties are observations. |
| Replacement and retention | Which paths are mutable aliases, when new versioned paths are required, how consumers migrate, and when historical files can be retired. |
| Naming and grouping | Whether future files require a date format or folder taxonomy; mixed legacy names do not establish a rule. |
| Hosting requirements | Required availability, access restrictions, and update latency. The repository has no SLA, authenticated image service, entitlement logic, or cache control implementation. |

Keep new decisions with their author, date, scope, and source. Label proposals
as proposals until the owner approves them, and update the owning docs and
consumer references together when an approved decision changes the workflow.
