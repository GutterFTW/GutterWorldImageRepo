## Repository work

This is a static PNG image collection, not an application or Unity project.
Read [README.md](README.md), [ASSET-CATALOG.md](ASSET-CATALOG.md), and
[MAINTENANCE.md](MAINTENANCE.md) before making changes. The catalog records
measured asset properties; the maintenance guide owns change/verification
procedures and unresolved owner decisions. Preserve existing exact paths and
case until a consumer migration or retirement is explicitly resolved.

Use Graphify for indexed context and the Git tree for the exact tracked file
inventory. A sparse checkout can omit assets from disk; do not treat that as
absence from the repository. Inspect actual binary properties and affected
consumer configuration for image changes. Do not invent consumers, rights,
dimension rules, naming rules, cache behavior, or runtime acceptance.

Keep documentation consistent with verified artwork/source evidence. Record
human decisions with their source and date; distinguish proposals from approved
policy. Preserve dirty work, stage only assigned files, use a scoped branch/PR,
and report validation actually run. Do not add image-processing dependencies,
application features, generated Unity files, or asset changes as a documentation
side effect. No build, CI, or runtime test suite is defined in the recorded tree.

<!-- graphify-rules-start (managed by `graphify init`) -->
## Use Graphify before grep

This repository is indexed by Graphify: a code graph over its call, dependency, and test structure, exposed through a connected Graphify MCP server. Before reaching for grep or reading files, use the Graphify tools your MCP client lists (their exact names and descriptions are in the server's tool list) for what the graph knows and a text search does not:

- find where a symbol, function, or class is defined (instead of grepping for it)
- understand how something works, or where a behavior is handled
- find who calls a function, or what it calls
- see what a change affects (its blast radius) and which tests cover it
- map a file's dependencies and dependents

Fall back to grep or file reads only for what the graph does not model: literal string or comment matches, non-indexed files, or reading a file you have already located. If no Graphify tools are listed, check the MCP server connection.
<!-- graphify-rules-end -->
