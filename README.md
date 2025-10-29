# workflow-tests

This repository includes automated workflows for code review management.
testing changes

## CODEOWNERS

The repository uses a CODEOWNERS file (`.github/CODEOWNERS`) to specify code owners who must review and approve pull requests.

Current codeowners:
- @fivetran-sahilkhirwal

## Codeowner Approval Workflow

The **Check Codeowner Approval** workflow automatically verifies that pull requests have been approved by at least one codeowner before they can be merged.

### How it works:

1. **Triggers**: The workflow runs on:
   - Pull request events (opened, synchronize, reopened, review_requested)
   - Pull request review submissions (submitted)

2. **Steps**:
   - Fetches the CODEOWNERS file from the repository
   - Extracts the list of codeowners
   - Retrieves all approvals for the current pull request
   - Checks if at least one approval comes from a codeowner
   - Fails if no codeowner approval is found

3. **Fork Support**: The workflow uses `pull_request_target` event, which means it:
   - Works for PRs from forked repositories
   - Works for PRs from branches in the main repository
   - Has access to repository secrets and write permissions
   - Checks out the PR's HEAD commit for validation

### Usage

Simply open a pull request, and the workflow will automatically run. The PR must receive approval from at least one codeowner (as defined in `.github/CODEOWNERS`) for the check to pass.
