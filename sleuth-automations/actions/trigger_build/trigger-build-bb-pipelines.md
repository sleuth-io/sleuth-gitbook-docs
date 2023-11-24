# Bitbucket Pipelines

## Usage

The only **required parameter** for Sleuth is the **name of the pipeline** specified in your`./bitbucket-pipelines.yml` file. Sleuth will pass any additional specified parameters to Bitbucket API when triggering the build in case your workflow requires additional input parameters. See [Bitbucket Pipelines documentation](https://developer.atlassian.com/bitbucket/api/2/reference/resource/repositories/%7Bworkspace%7D/%7Brepo_slug%7D/pipelines/) for additional informations.

This example triggers a `deploy-prod` pipeline in Bitbucket when code is deployed to the "Staging" environment for more than 4 hours and is healthy:

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
              name: 'deploy-prod'
              my-custom-non-required-param: 'we are going live'
```

