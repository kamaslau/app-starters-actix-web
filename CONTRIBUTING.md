# Contributing

This repository is one starter of the app-starters family: Rust on [Actix Web](https://actix.rs/), one manifest that compiles and three routes.

Default port: 8080, bound to `127.0.0.1` in `src/main.rs`. The bind address is a constant in that file; there is no `.env` here yet, and adding one is a change worth arguing for rather than assuming.

## The shape a change has to keep

A starter, not a framework: `cargo run` works on a clean checkout, the whole service fits in one file, and the dependency list is short enough to read.

The test for any change: could someone who has never seen this repository have it answering on port 8080 from the README alone?

## Pull requests

- **The dependency list stays short.** Actix Web pulls enough of the ecosystem already; a starter that arrives with logging, tracing, database and auth configured is a project nobody can unbundle later.
- **`Cargo.toml` keeps the package name and the binary name in step.** They are the deployment identifier; renaming one without the other produces an image that starts the wrong binary.
- **The README is English.** Chinese belongs only under a *Notes for deployments in China* section, when there is something true to write there.
- **`Verify` has to keep proving something.** Any change in behaviour updates the command in that section.
- **`Cargo.lock` is committed.** This is a binary, not a library: the lock file is what makes `cargo build` reproducible on the client's machine.
- **Commits**: imperative subject, one concern per commit. `fix: bind 0.0.0.0 so the container is reachable` is the shape. `update` is not.

## Adding a starter

Open an issue on [infra-blocks](https://github.com/kamaslau/infra-blocks) before writing anything — the family is meant to stay small, and two starters for the same framework is a maintenance cost rather than a choice.

If it is accepted:

1. Repository named `app-starters-<framework>`, MIT license, description in the form *what it is + what it gives you*.
2. README with the sections used across the family: title and one-line purpose, Run, What it gives you, Verify, Why this shape, Use this template.
3. `is_template` enabled, and a row in the index under *Not in this list*.

## Reporting a problem

Open an issue with four things: the command you ran, what you expected, what happened, and the output of `cargo run`. Without the last one, most reports turn into guesswork.

---

Part of the app-starters family · MIT
