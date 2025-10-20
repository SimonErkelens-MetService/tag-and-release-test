# Release/PR/Build demo workflow

This repository contains a minimal demo of using workflows in several ways.

Workflows:
1. Release workflow
    1. Only runs on a tag or release, if the branch is `main`
    1. Runs the build process first
    1. Downloads the Artifacts
    1. Publishes to the super-sophisticated "echo"
1. Pull Request workflow
    1. Runs on every pull request (open or draft)
    1. Calls the "build" workflow, and optionally does something after.
1. Build workflow
    1. Contains the build logic
    1. Can be run manually
    1. Uploads artifacts to GitHub Artifacts

## Caveats

There are two ways to re-use workflows in GitHub:

### GitHub Workflows

- Can only be called as an entire job
    ```yml
    jobs:
        job_name:
            uses: ./.github/workflows/my-reuseable-workflow.yml
            with:
                VARIABLE_1: var
                1_ELBAIRAV: rav
    ```
    - **Required** The re-useable workflow must have `workflow_call` as an `on`

## GitHub Actions

- Can be used as a separate step in multiple steps of a job
    ```yml
    jobs:
        job_name:
            steps:
                - name: step 1
                  uses: actions/checkout
                - name: step 2
                  uses: ./.github/actions/my-custom-action.yml
                  with:
                    VARIABLE_1: var
                    1_ELBAIRAV: rav
    ```
