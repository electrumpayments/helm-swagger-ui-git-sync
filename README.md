# Swagger UI + git-sync Helm chart

This chart deploys a [Swagger UI frontend](https://hub.docker.com/r/swaggerapi/swagger-ui) with a
[git-sync sidecar](https://github.com/kubernetes/git-sync/) that continually pulls from a git repo, thus allowing
swagger-ui to always serve the latest version of an OpenAPI spec stored in git.

The chart can be configured to pull from a public repo, or private repo via SSH. Note that this chart does not create
secrets - if using SSH you must create the relevant secret by external means.

## Parameters
