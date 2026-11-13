# app-starters-actix-web

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Repository size](https://img.shields.io/github/repo-size/kamaslau/app-starters-actix-web?color=56BEB8)

Rust app starter with [Actix Web](https://actix.rs/): one route, a manifest that compiles, room for the rest.

## Run

```bash
cargo run
```

`cargo install --path .` puts the binary on your `PATH` if you want it outside the project directory.

## What it gives you

One route in `src/main.rs`, and `actix-web = "4"` pinned in `Cargo.toml`.

The crate is named `app-starters-actix-web`, and the binary name follows it. Rename the package in
`Cargo.toml` before your first commit — doing it later means touching the deployment scripts too.

## Verify

```bash
cargo run
```

In another terminal:

```bash
curl -s http://127.0.0.1:8080/
# Hello world!

curl -s http://127.0.0.1:8080/hey
# Hey there!

curl -s -X POST --data 'ping' http://127.0.0.1:8080/echo
# ping
```

Three routes, two verbs, and the body echoed back: handlers are registered on the `App`, not discovered. Actix logs nothing by default, so the first proof the server is up is the `curl` that answers — if `cargo run` exits instead, the failure is the manifest or the toolchain and the compiler will have said which.

## Why this shape

Binding `127.0.0.1` rather than `0.0.0.0` is the safer default for a starter nobody has deployed yet: nothing on the local network can reach it until the developer changes one constant. It is also the thing to change first when this goes into a container, where a loopback bind means a port that never answers.

`/echo` exists because a `POST` handler that reads a request body is where a new Actix project usually stalls — extractors, response types, and the difference between `String` and `web::Bytes` are not obvious from the docs' first example. One working line is worth more than an explanation.

No `Dockerfile`, no configuration file, no `.env`. Every one of them is a decision about how the service will be deployed, and this repository stops at "it runs". The deployment half is a different question with its own answers, and [infra-blocks](https://github.com/kamaslau/infra-blocks) is where those answers live.

## Use this template

*Use this template* gives you a repository you own, with no history and no link back here — the right shape for
the first commit of a real service. Clone it instead when you want to follow changes to the starter itself;
a repository created from the template never receives them.

## License

MIT — see [LICENSE](./LICENSE). Take what is useful.
