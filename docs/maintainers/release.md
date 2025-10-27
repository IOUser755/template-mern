# Release Process

This document explains how to cut a release for the template-mern project.

## Overview

We use [Release Drafter](https://github.com/release-drafter/release-drafter) to automatically generate release notes based on pull request labels.

## Labels

The following labels are used to categorize changes:

### Type Labels
- **type:feature** - New features or enhancements (minor version bump)
- **type:fix** - Bug fixes (patch version bump)
- **type:docs** - Documentation changes (patch version bump)

### Priority Labels
- **prio:high** - High priority items

### Area Labels
- **area:client** - Frontend/client-side code
- **area:server** - Backend/server-side code

## Setting Up Labels (One-Time)

If labels haven't been created yet, run these commands using the GitHub CLI:

```bash
gh label create "type:feature" --color "0E8A16" --description "New feature or enhancement"
gh label create "type:fix" --color "D93F0B" --description "Bug fix"
gh label create "type:docs" --color "0075CA" --description "Documentation changes"
gh label create "prio:high" --color "B60205" --description "High priority"
gh label create "area:client" --color "FBCA04" --description "Frontend/client-side code"
gh label create "area:server" --color "FEF2C0" --description "Backend/server-side code"
```

## How to Cut a Release

### 1. Review the Draft Release

Release Drafter automatically creates and updates a draft release as pull requests are merged:

1. Navigate to [Releases](../../releases)
2. Find the latest draft release
3. Review the automatically generated changelog
4. Verify that PRs are categorized correctly based on their labels

### 2. Edit Release Notes (Optional)

- Add any additional context or breaking changes
- Highlight important features or fixes
- Add upgrade instructions if needed

### 3. Determine Version Number

Version bumps are determined by labels:
- **Minor** (0.x.0): PRs with `type:feature` label
- **Patch** (0.0.x): PRs with `type:fix` or `type:docs` labels
- **Major** (x.0.0): PRs with `major` label (use sparingly for breaking changes)

### 4. Publish the Release

1. Update the version number if needed (format: `vX.Y.Z`)
2. Update the tag to match the version
3. Click **Publish release**

### 5. Post-Release

- Verify the release appears in the [Releases page](../../releases)
- Check that the tag was created
- Update any deployment pipelines or documentation as needed

## Best Practices

- Always label PRs appropriately before merging
- Review draft releases regularly
- Keep release notes clear and user-focused
- Document breaking changes prominently
- Follow [Semantic Versioning](https://semver.org/)

## Troubleshooting

### Release Drafter not updating?

- Check the [Actions](../../actions) tab for workflow runs
- Ensure the Release Drafter workflow has the necessary permissions
- Verify the configuration in `.github/release-drafter-config.yml`

### PRs not appearing in release notes?

- Ensure PRs have appropriate type labels (`type:feature`, `type:fix`, etc.)
- Check that PRs were merged to the main branch
- Manually add missing items to the release notes if needed
