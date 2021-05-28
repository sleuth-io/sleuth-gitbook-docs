# Jenkins

## Usage

The only **required parameter** for Sleuth is the **name of the Jenkins job** . Sleuth will pass any additional specified parameters to Jenkins when triggering the job in case you are using parameterised builds. See [Jenkins documentation](https://www.jenkins.io/doc/book/using/remote-access-api/) for additional informations.

This example triggers a `deploy-prod` job in Jenkins when code is deployed to the "Staging" environment for more than 4 hours and is healthy:

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

