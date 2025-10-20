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
