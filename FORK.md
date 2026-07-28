# Fork notes (space-pirate-zero/mink)

This is a fork of [`drewpayment/mink`](https://github.com/drewpayment/mink).

## Package name is renamed on this fork

`package.json` `name` is **`@spacepiratezero/mink`** here, not the upstream
`@drewpayment/mink`.

**Why:** installing the fork by GitHub shorthand (`bun add -g space-pirate-zero/mink`)
resolves the package to whatever its `name` is. While it was named
`@drewpayment/mink` it collided with the published upstream package of the same
name and `bun` failed with a `DependencyLoop`. Renaming to a distinct name lets
the fork install cleanly:

```bash
bun add -g space-pirate-zero/mink        # installs @spacepiratezero/mink
# or, from a clone:  bun install && bun run build && npm link
```

The CLI binary is unchanged — it is still invoked as `mink`.

## ⚠️ Revert before opening any upstream PR

**Before opening or updating a PR against `drewpayment/mink`, change the name in
`package.json` back to `@drewpayment/mink`** (and drop this file from the PR).
The upstream package must keep its own name and its OIDC/npm publish identity.
The feature PRs already open upstream (drewpayment/mink #102–#109) were cut from
branches that still carry `@drewpayment/mink` and must stay that way.
