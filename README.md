# GitLab Runner Smoke Test

This repository is a minimal GitLab CI project used to verify that the local
GitLab runner can pick up jobs tagged `local` and run the custom runner test
image successfully.

## What It Checks

The pipeline runs one job:

- Job: `verify-tools`
- Runner tag: `local`
- Image: the immutable developer image configured as the runner default
- Command: `/usr/local/bin/verify-tools.sh`

A passing pipeline confirms that:

- GitLab can schedule jobs onto the runner tagged `local`.
- The runner can pull the local registry image.
- The image contains and can execute `/usr/local/bin/verify-tools.sh`.

## Prerequisites

- A reachable GitLab instance for this project.
- A registered runner with the `local` tag.
- The runner's configured developer image published and pullable from the
  runner environment.

## Running The Smoke Test

Push a commit to the default branch or manually retry the pipeline in GitLab.
The repository is intentionally small, so most failures should be investigated
in the runner, executor environment, registry, or image build rather than in
application code.

## Project Files

- `README.md`: project purpose, smoke-test behavior, and troubleshooting notes.
- `.gitlab-ci.yml`: the GitLab CI smoke-test job definition.
- `CHANGELOG.md`: notable project and documentation changes.
- `LICENSE`: Apache License 2.0 terms.

## Troubleshooting

- `stuck` job: confirm the runner is online and registered with the `local`
  tag.
- Image pull failure: confirm the local registry is reachable from the runner
  pod or executor environment.
- Script failure: rebuild or inspect the runner image and verify that
  `/usr/local/bin/verify-tools.sh` exists and is executable.
- DNS tool failure: confirm the image contains both `dig` and `nslookup`.

## Documentation History

- 2026-07-09: Added Apache License 2.0 licensing and a changelog.
- 2026-07-09: Updated the documented runner tag from `k8s` to `local`.
- 2026-07-09: Expanded the README from a placeholder into project purpose, CI
  behavior, prerequisites, troubleshooting, and documentation history.
- 2026-07-07: Initial README created with the project title.
