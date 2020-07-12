# ecs-deploy-install

## About

orbs to install ecs-deploy.

* https://circleci.com/orbs/registry/orb/inokappa/ecs-deploy-install

## Example

```yaml
---
version: 2.1

orbs:
  aws-cli: circleci/aws-cli@x.y
  ecs-deploy: inokappa/ecs-deploy-install@x.y

jobs:
  build:
    docker:
      - image: cimg/base:2020.01
    steps:
      - aws-cli/install
      - ecs-deploy/install:
          latest: true
      - run:
          name: Get ecs-deploy version
          command: |
            ecs-deploy --version
```

## Development

### Publish

```sh
$ circleci config pack --skip-update-check src > orb.yml
$ circleci orb publish orb.yml inokappa/ecs-deploy-install@x.y.z
```

`x.y.z` cannot be overwritten, so always specify a new version.
