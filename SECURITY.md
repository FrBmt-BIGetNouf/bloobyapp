# Security Policy

## Supported versions

Only the latest released version of Blooby receives security fixes. Blooby
updates itself automatically, so the fastest remediation is almost always to let
the in-app updater run.

## Reporting a vulnerability

**Please do not open a public issue for a security problem.**

Report it privately instead, through GitHub's
[private vulnerability reporting](https://github.com/FrBmt-BIGetNouf/bloobyapp/security/advisories/new):
the Security tab of this repository, then "Report a vulnerability". Only you and
the maintainers can see the report.

Please include:

- what you found and why it is a problem,
- the Blooby version and your operating system,
- the steps to reproduce it,
- anything the report depends on (a specific configuration, another tool
  installed alongside).

You will get an acknowledgement within a few days. Blooby is maintained by a very
small team, so please allow reasonable time for a fix before disclosing publicly.

## Scope

Blooby runs a **local HTTP listener** so that a coding agent's hooks can tell it what
each session is doing, and it **edits that agent's own settings** to install those
hooks. Findings around either of those are especially welcome: the local listener
accepting something it should not, or the hook installation writing somewhere it
should not.

Out of scope: vulnerabilities in the agents themselves (report those to their makers),
and issues that require an attacker to already have full control of your machine.
