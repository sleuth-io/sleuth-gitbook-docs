# Github Actions

## Usage

By default Github Actions can not be triggered  via the API. To enable Sleuth to trigger the workflow, you need to add `workflow_dispatch` option in `on` section:

```text
# Controls when the action will run. 
on:
  # Triggers the workflow on push or pull request events
  # but only for the master branch
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

  # Allows Sleuth to triggered the workflow through API
  workflow_dispatch:
```

The only **required parameter** for Sleuth is the **name of the workflow file** located in your repository `./github/workflows/` folder. Sleuth will pass any additional specified parameters to Github Actions API when triggering the build in case your workflow requires additional input parameters. See [Github Actions documentation](https://docs.github.com/en/actions) for additional informations.

This example triggers a `deploy-prod` workflow in Github when code is deployed to the "Staging" environment for more than 4 hours and is healthy:

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
              name: 'deploy-prod.yml'
              my-custom-non-required-param: 'we are going live'
```

