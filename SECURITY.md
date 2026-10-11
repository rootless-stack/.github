# Security policy

## Reporting a vulnerability

Please **do not** open a public issue, discussion or pull request for a
security problem.

Report it privately through GitHub instead: open the affected repository's
**Security** tab and choose **Report a vulnerability**.  Include what is
affected (image, unit, config), how to reproduce it, and the impact you
expect.

This is a volunteer project.  Reports are handled on a best-effort basis,
and you will hear back once the report has been looked at.  Fixes are
released first and disclosed in a GitHub security advisory afterwards,
with credit unless you prefer otherwise.

## Supported versions

Only the latest release and `main` receive security fixes.

## Scope

In scope: the images, Quadlet units, configuration templates and tooling
in this organization's repositories, including weaker hardening than
documented (a missing capability drop, a writable root filesystem, a
secret exposed in an environment variable or argument).

Out of scope: vulnerabilities in the upstream software the images ship
(Postfix, Dovecot, Nextcloud, WordPress and so on).  Report those to the
upstream project.  If our images ship a vulnerable upstream version that
has a fix available, please do tell us.
