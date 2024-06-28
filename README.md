# changeset-autorelease

![Flow](./flow-dark.png#gh-dark-mode-only)
![Flow](./flow-light.png#gh-light-mode-only)

[Workflow file](.github/workflows/release.yaml)

This repository is a proof of concept how changeset can work on private repos, allowing automatic versioning when pushed to main branch.

My suggestion is to keep two branches:

- main
- develop

When `main` gets pushed (ideally from a PR), a workflow is triggered that will detect if has any versioned changes (through `npx changeset add`), if so, it'll continue the flow and create a Github Release.

For daily development, it's intended to push to `develop` branch and creating as many `changesets` as needed, when you feel comfortable to merge to production, just create a Pull Request and when merged, it'll automatically create the release.

For hot fixes, just develop in a branch from `main`, and create a Pull Request to `main`, again, every push to `main` will trigger the workflow for releasing. Then, you pull changes to `develop` to keep up to date to `main`.
