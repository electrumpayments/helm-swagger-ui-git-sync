# Swagger UI + git-sync Helm chart

This chart deploys a [Swagger UI frontend](https://hub.docker.com/r/swaggerapi/swagger-ui) with a
[git-sync sidecar](https://github.com/kubernetes/git-sync/) that periodically polls a git repo for changes, thus 
allowing swagger-ui to always serve the latest version of an OpenAPI spec stored in git.

The chart can be configured to pull from a public repo, or private repo via SSH. Note that this chart does not create
secrets - if using SSH you must create the relevant secret by external means.

## Installation

//TODO update once public

## Parameters

### Git-sync

| Name                                | Description                                                                                                                  | Value                                      |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| `git_sync.repo_url`                 | (required) SSH or HTTPS url of the repo to clone                                                                             | `nil`                                      |
| `git_sync.ref`                      | branch or tag to check out                                                                                                   | `main`                                     |
| `git_sync.refresh_period`           | how frequently to poll for changes                                                                                           | `60s`                                      |
| `git_sync.swagger_path`             | repo-relative path to the target swagger file (OpenAPI spec)                                                                 | `swagger/swagger.yaml`                     |
| `git_sync.ssh.existing_secret_name` | if set, configure git-sync to use SSH. This secret should contain a private SSH key and should be created outside this chart | `nil`                                      |
| `git_sync.ssh.existing_secret_key`  | The key of the secret that contains the private SSH key                                                                      | `nil`                                      |
| `git_sync.image`                    | The git-sync image to use                                                                                                    | `registry.k8s.io/git-sync/git-sync:v4.0.0` |

### Swagger UI

| Name               | Description                                                                                                                                               | Value                            |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| `swagger_ui.env`   | Additional [environment variables](https://github.com/swagger-api/swagger-ui/blob/master/docs/usage/configuration.md) to add to the swagger-ui container. | `[]`                             |
| `swagger_ui.image` | The swagger-ui image to use                                                                                                                               | `swaggerapi/swagger-ui:v5.17.14` |


## Changelog

- [release-notes.md](release-notes.md)
