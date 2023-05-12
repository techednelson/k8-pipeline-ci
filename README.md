# k8-pipeline-ci
This repo contains a sample python flask application and a CI jenkins pipeline which triggers an extra job called `updatek8PipelineGitOps` and has as goal to update a kubernetes deployment file which triggers Argocd agent inside a kubernetes cluster to update any changes in the python application.
