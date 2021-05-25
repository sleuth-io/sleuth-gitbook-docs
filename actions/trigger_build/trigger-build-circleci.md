# CircleCI

## Usage

This example triggers a deployment in CircleCI when code is deployed to the "Staging" environment for more than 4 hours and is healthy:

```text
rules:
  - run-deploy:
      conditions:
        - environment='Staging'
        - deployed_for>'4h'
        - health='Healthy'
      actions:
        - trigger_build:
            parameters:
              run_deploy: true
              environment: production
```

It passes several parameters to be used by CircleCI: `run_deploy` and `environment`. For more information about how to declare parameters and filter workflows in CircleCI, see the [CircleCI documentation](https://circleci.com/docs/2.0/pipeline-variables/#pipeline-parameters-in-configuration).

This is an example of the CircleCI configuration that uses the `run_deploy` parameter to selectively execute a workflow, while the `environment` parameter is used within the job to perform the deployment:

```text
parameters:
  run_deploy:
    default: false
    type: boolean
  environment:
    type: string
    default: staging

jobs:
  run-deploy:
    docker:
      - image: circleci/python:3.8.6
    steps:
      - run:
          command: |
            echo "Deploying to <<pipeline.parameters.environment>>"


workflows:
  deploy:
    when: << pipeline.parameters.run_deploy >>
    jobs:
      - run-deploy
```

