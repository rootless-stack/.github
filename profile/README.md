# rootless-stack

Hardened, rootless self-hosting with Podman Quadlets and systemd.

Mail, identity, cloud and web stacks, each running as its own unprivileged
Linux user, with no root daemon and no orchestrator in between.  All you
need is `podman`, `skopeo` and `systemd`.

## Principles

- **One user per stack.**  Every stack has its own uid, its own Podman
  storage and its own user namespace.
- **Least privilege by default.**  Every container drops all capabilities,
  runs on a read-only root filesystem with a seccomp profile and
  `NoNewPrivileges`, and adds back only what a daemon needs.
- **Unix sockets across stacks.**  Stacks talk to each other over sockets
  gated by directory ACLs, not over a shared container network.
- **Signed images.**  Images are built in public CI and signed with
  Cosign; hosts pull only signed digests.
- **Plain systemd.**  A Quadlet unit per container, healthchecks gate
  readiness, and drop-ins hold everything site-specific.

## Status

Early.  Stacks are published one at a time as they are separated from a
production deployment.

## License

[Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0), unless a
repository states otherwise.  Bundled upstream software keeps its own
license.
