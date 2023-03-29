# docker-github-actions-runner

This is a workaround to run cypress within a self-hosted github action runner, as long a docker-in-docker is not natively supported in the github actions docker image.

## related issues

- https://github.com/actions/runner/issues/406
- https://github.com/actions/runner/issues/367

## credits

- using cypress as base image from https://github.com/cypress-io/cypress-docker-images/tree/5f5272a44c233d5f584d05f86fd041149ad214cc/browsers/node18.12.0-chrome107
- using action runner from https://github.com/actions/runner/blob/caec043085990710070108f375cd0aeab45e1017/images/Dockerfile
- using entrypoint.sh, token.sh and app_token.sh from https://github.com/myoung34/docker-github-actions-runner/tree/45574ba8bbef6113f0598b9b6cb5019da3e37fc4


## start runner

- `cp docker-compose.template.yml docker-compose.yml`
- replace `<secret>` in docker-compose.yml
- `docker-compose up --detach` or `docker-compose up --detach --build --force-recreate`
