# Swagger UI + git-sync Helm chart

This chart deploys a [Swagger UI frontend](https://hub.docker.com/r/swaggerapi/swagger-ui) with a
[git-sync sidecar](https://github.com/kubernetes/git-sync/) that continually pulls from a git repo, thus allowing
swagger-ui to always serve the latest version of an OpenAPI spec stored in git.

The chart can be configured to pull from a public repo, or private repo via SSH. Note that this chart does not create
secrets - if using SSH you must create the relevant secret by external means.

## Parameters

### Git

| Name                           | Description                                                                                                                  | Value |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- | ----- |
| `git.repo_url`                 | SSH or HTTPS url to the repo to clone                                                                                        | `""`  |
| `git.ref`                      | branch or tag to check out                                                                                                   | `""`  |
| `git.refresh_period`           | how frequently to poll for changes                                                                                           | `""`  |
| `git.swagger_path`             | repo-relative path to the target swagger file (OpenAPI spec)                                                                 | `""`  |
| `git.ssh.existing_secret_name` | if set, configure git-sync to use SSH. This secret should contain a private SSH key and should be created outside this chart | `nil` |
| `git.ssh.existing_secret_key`  | The key of the secret that contains the private SSH key                                                                      | `nil` |

### Images

| Name                | Description                 | Value |
| ------------------- | --------------------------- | ----- |
| `images.swagger_ui` | The swagger-ui image to use | `""`  |
| `images.git_sync`   | The git-sync image to use   | `""`  |
