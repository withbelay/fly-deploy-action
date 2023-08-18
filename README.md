```
on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - uses: actions/checkout@v3
      - id: deploy-mktproxy
        uses: withbelay/fly-deploy-action@v1
        with:
          env: staging
          app: mktproxy
      - id: deploy-belay-api
        uses: withbelay/fly-deploy-action@v1
        with:
          env: staging
          app: api
          deploy_args: "--build-arg RELEASE_NAME=belay_staging"

```
