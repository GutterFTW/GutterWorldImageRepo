# Gutter World Image Repository

This repository hosts club artwork as ordinary Git-tracked image files. Its
original title was **Patreon Supporter-Images**, described as "A place to host
club icons." The tracked collection also includes dated poster images and logos.

Start with the [asset catalog](ASSET-CATALOG.md) to find an exact filename,
dimensions, and file size. Use the [maintenance guide](MAINTENANCE.md) when adding,
replacing, investigating, or retiring an image. Agents should also read
[AGENTS.md](AGENTS.md).

## What is in the repository

```text
Nest1/         One tracked PNG: Official_Wyvern_Logo.png
TSL-Images/    Dated artwork, emission-named images, and logo PNGs
README.md      Entry point and image URL usage
ASSET-CATALOG.md
MAINTENANCE.md
AGENTS.md      Agent workflow and managed Graphify instructions
.gitattributes Automatic text line-ending normalization
```

The measured artwork snapshot contains **16 PNG files**, totaling **11,137,808
bytes**. Those figures describe the catalog's recorded revision, not an upload
limit. The repository has no tracked application code, dependency manifest,
image-processing script, Unity project, consumer URL list, or automated test/CI
configuration. There is no build or package-install step for serving the tracked
files through their GitHub raw URLs.

Folder names, filename dates, `Emission`, and `logo` are existing labels. They do
not define a parser, update schedule, texture role, or enforced naming schema.
Preserve their spelling and capitalization when referring to an existing asset.

## Get an image URL

For a human-readable file page, open the file on GitHub. For a client that needs
the image bytes, use that page's **Raw** link. GitHub documents the difference in
[Viewing raw file content](https://docs.github.com/en/repositories/working-with-files/using-files/viewing-and-understanding-files#viewing-or-copying-the-raw-file-content).

For example, this tracked image has a mutable URL that follows `main`:

```text
https://raw.githubusercontent.com/GutterFTW/GutterWorldImageRepo/main/TSL-Images/2025_10.14_Emission.png
```

A commit ID selects the version of the file at that revision:

```text
https://raw.githubusercontent.com/GutterFTW/GutterWorldImageRepo/ae3644fbe37fb935241f18f867efed9a5458fef0/TSL-Images/2025_10.14_Emission.png
```

Choose the reference to match the consumer's requirements: a branch reference
can pick up later replacements, while a commit reference identifies a particular
version. A pinned URL will continue referring to that version after `main`
changes. See GitHub's [permanent-link guidance](https://docs.github.com/en/repositories/working-with-files/using-files/getting-permanent-links-to-files).

Copy the URL from the actual file rather than reconstructing names from dates.
Keep exact path case and URL-encode characters when a client requires it. A
GitHub `/blob/` page is an HTML page; it is not the raw PNG endpoint. Existing
tracked filenames currently contain no spaces.

The two example raw URLs returned **HTTP 200**, `Content-Type: image/png`, and
`Content-Length: 35113` in HEAD checks on **2026-10-31**. That is a dated HTTP
observation, not a hosting uptime or cache-freshness guarantee.

## Use an image in another project

The consumer owns the configuration that points to these files. No world,
website, bot, image downloader, refresh timer, fallback image, or URL allowlist is
tracked here. Record the consuming project and the exact configured URL in the
change description when they are known; do not assume that merging an image
changes a consumer configured with a different filename or a pinned revision.

For a consumer such as a Unity/VRChat world, validate the URL, its downloader
settings, display aspect ratio, color/transparency handling, supported target
platform, failure UI, and refresh behavior in that consuming project. This
repository alone cannot establish those runtime results or the installed
Unity/SDK versions. No consumer integration was run for the documentation audit.

If an image looks stale, compare the configured URL and reference with the
intended file first. A commit-pinned URL intentionally selects older bytes.
For a branch URL, determine whether the request reached the intended revision
and investigate the consumer or intermediary cache before changing artwork.
There is no cache-purge mechanism or fixed cache lifetime defined by this repo.

## Make a change

1. Inspect the current branch, Git status, and the tracked tree. Use an isolated
   task branch or checkout when another task owns the working copy.
2. Find the current asset in the [catalog](ASSET-CATALOG.md) and identify its
   consumers. Follow the [add/replace/retire workflow](MAINTENANCE.md#change-workflows).
3. Inspect the actual image: verify its dimensions, format, transparency, artwork,
   and rights. A `.png` suffix does not prove a valid or suitable image.
4. Update the catalog if a tracked asset's path, dimensions, size, or encoding
   changes. Include URL compatibility and validation evidence in the PR.
5. Complete the applicable checks in the maintenance guide. Review in a PR;
   remote publication and consumer updates are separate actions.

## Rights and decisions still needed

No license file or per-image permission/attribution manifest is tracked in the
recorded revision. Repository visibility and the historical Patreon title do
not establish permission to reuse artwork or any paid-access entitlement.
Confirm the intended use and required credit with the asset rights holder.

The owner still needs to establish the consumer inventory, artwork permissions,
replacement/retention policy, and any required technical constraints. The
[maintenance guide](MAINTENANCE.md#unresolved-owner-decisions) lists these gaps;
this documentation does not choose product policy on the owner's behalf.
