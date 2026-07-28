# Merge Queue Demo

This project was made for demoing GitHub Merge Queue. Go run the Actions to create pull requests that will pass or fail checks in the merge queue.

## Actions

### Open Bad PRs
Opens X number of PRs that will pass checks but fail checks in the merge queue.

### Open Good PRs
Opens X number of PRs that will pass checks and pass checks in the merge queue.

### Merge Conflict PRs
Opens 2 PRs that will pass checks but conflict with each other in the merge queue.

## Required CI test

The `build` job in `.github/workflows/ci.yml` runs a 30-second test via `test.sh`.
Pull requests can only be merged when this check passes.

## Merge queue setup

To require the CI check in the merge queue:

1. Go to **Settings → Branches**.
2. Add or edit a branch protection rule for `main`.
3. Enable **Require a pull request before merging**.
4. Enable **Require status checks to pass before merging**.
   - Search for and select `build`.
5. Enable **Require merge queue**.
6. Save the rule.

The workflow already triggers on `merge_group`, so it will run on the temporary merge queue branch.

## Resources
* [Managing a merge queue](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue)
* [Merging a pull request with a merge queue](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/merging-a-pull-request-with-a-merge-queue)
