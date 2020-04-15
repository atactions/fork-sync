# Fork Sync
[![Build](https://github.com/tg908/fork-sync/workflows/PR%20Checks/badge.svg)](https://github.com/tg908/fork-sync/actions?workflow=PR%20Checks)
![Version](https://img.shields.io/github/v/release/tg908/fork-sync?style=flat-square)

Forked from TG908/fork-sync with additions of `allbranches` parameter to sync all branches of fork repo.

Github action to sync your Forks.
This action uses octokit and the GitHub API to automatically creates and merges a pull request with the head defined by `ownwer`:`head` into the base defined by `base`. If you create a PR in the same repository you can omit the `owner` parameter.

# Example Workflow

```yml
name: Sync Fork

on:
  schedule:
    - cron: '*/30 * * * *'

jobs:
  sync:

    runs-on: ubuntu-latest

    steps:
      - uses: atactions/fork-sync@v1.1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          owner: llvm #owner of origin repo 
          allbranches: true
          
```

# Parameters

|  name           |   Optional  |   Default              |   description                                       |
|---              |---          |---                     |---                                                  |
|   owner         | ✅          | $current_repo_owner    |   Owner of the forked repository                     |
|   github_token  | ❌          |                        |   Token  to access the Github API                    |
|   head          | ✅          | master                 |   Head branch                                        |
|   base          | ✅          | master                 |   Base branch                                        |
|   merge_method  | ✅          | merge                  |   merge, rebase or squash                            |
|   pr_title      | ✅          | Fork Sync              |   Title of the created pull request                  |
|   pr_message    | ✅          |                        |   Message of the created pull request                |
|   allbranches   | ✅          |    false               |   Wheather sync all branches               |

