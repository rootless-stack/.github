# Contributing to rootless-stack

Thanks for helping.  These rules apply to every repository in the
organization unless a repository has its own `CONTRIBUTING.md`.

## Before you start

- **Security issues** never go into a public issue or pull request.  See
  [SECURITY.md](SECURITY.md).
- For anything larger than a small fix, open an issue first, so we can
  agree on the approach before you spend time on it.

## Pull requests

- **Signed commits are required.**  `main` accepts only commits with a
  verified signature, so GitHub blocks a pull request containing an
  unsigned commit.  SSH signing is the quickest setup:

  ```sh
  git config --global gpg.format ssh
  git config --global user.signingkey ~/.ssh/id_ed25519.pub
  git config --global commit.gpgsign true
  ```

  Then add the same key on GitHub as a **signing** key
  (Settings → SSH and GPG keys).  To sign commits you already made:
  `git rebase --exec 'git commit --amend --no-edit -S' origin/main`, then
  force-push.
- **One logical change per pull request.**
- **Commit messages** follow
  [Conventional Commits](https://www.conventionalcommits.org/):
  `type(scope): description`, for example `fix(mail): reload postfix on
  cert change`.
- **The quality gate must pass.**  Run `prek run --all-files` before
  pushing; CI runs the same checks.

## Hardening rules

Changes to containers keep the baseline every unit shares:

- `DropCapability=ALL`; any `AddCapability=` needs a comment saying why.
- `ReadOnly=true`; runtime state goes to a sized `Tmpfs=` or a mount.
- `NoNewPrivileges=true` and the shared seccomp profile.
- No secrets in environment variables or command lines; mount them as
  files.
- Every upstream image is fully qualified and pinned to a digest.

## License

By contributing, you agree that your contribution is licensed under the
repository's license (Apache License 2.0, section 5).  No separate
contributor agreement is needed.
