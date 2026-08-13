# Repository Guide

This repository maintains the `markdownlint` library, built-in rules, parsers, configuration schemas, documentation, and browser artifacts.

## Architecture

* `lib/`: library implementation, built-in rules, parser integration, exports, and checked-in declarations.
* `helpers/`: public and internal helper package.
* `style/`: reusable rule configurations.
* `scripts/`: shared repository build utilities.

## Workflow

**NOTICE**: Generated artifacts should not be edited directly. Modify their source files, then run the corresponding build command.

### Rule

* `lib/mdNNN.mjs`: built-in rule implementations.
* `lib/rules.mjs`: built-in rule registration and ordering.
* `lib/constants.mjs`: fixable and deprecated rule metadata.
* `doc-build/mdNNN.md`: canonical rule documentation.
* `doc/mdNNN.md`: generated documentation for individual rules.
* `doc/Rules.md`: generated documentation for all rules.
* `schema/build-config-schema.mjs`: rule option schemas and defaults.
* `test/*.md`: scenario fixtures that use `{MD###}` to mark expected results.

Keep rules as decoupled as possible. A rule's configuration and behavior should
not affect how other rules parse or report the document.

When modifying a built-in rule, update the implementation, registration or metadata, canonical documentation, and option schema as applicable.

### Parser and Core

* `lib/markdownlint.mjs`: lint orchestration and inline configuration handling.
* `lib/micromark-parse.mjs`: Micromark extensions and token conversion.
* `lib/markdownit.cjs`: markdown-it compatibility support.
* `lib/cache.mjs`: parser and rule data caches.
* `lib/exports*.mjs`: asynchronous, promise, synchronous, and default public entry points.
* `lib/node-imports-*.mjs`: Node.js and browser environment boundaries.

When modifying the parser or core behavior, preserve behavior in both Node.js and browsers.

### Generated Artifact

* `npm run build-config`: run after changing rule configuration metadata or schema generation.
* `npm run build-docs`: run after changing `doc-build/`, rule metadata, or rule documentation inputs.
* `npm run build-declaration`: run after changing the public API or declaration inputs.
* `npm run build-demo`: run after changing browser demo sources or browser-facing exports.

### Test

**NOTICE**: Match testing effort to the risk of the change. Do not repeatedly run the full test suite after every small edit.

* `npm run test-webpack`: run after changing browser module resolution or bundling behavior.
* `npm run test-declaration`: run after changing public types or entry points.
* `npm run update-snapshots`: run only when expected output intentionally changes.
* `npm run ci`: run only when full CI or release verification is explicitly requested.

## Convention

<!-- markdownlint-configure-file { "line-length": false, "ul-style": { "style": "asterisk" }, "ul-indent": { "indent": 4 } } -->
