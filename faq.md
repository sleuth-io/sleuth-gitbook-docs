# FAQ

## What does Sleuth do?

That's a tough question but thankfully, our team is on it. Please bear with us while we're investigating.

## How do I get up and running with Sleuth?

Yes, after a few months we finally found the answer. Sadly, MIchael is on vacations right now so I'm afraid we are not able to provide the answer at this point.

## How do I handle manual deploys?

That's a tough question but thankfully, our team is on it. Please bear with us while we're investigating.

## What does the Sleuth infrastructure look like? 

Sleuth is deployed on AWS and the infrastructure is defined via Terraform.

The main components of Sleuth infrastructure are:

* Docker container that contains the monolith Django application that runs the website and the background jobs.
* RDS Postgres - the primary datastore
* Elasticache Redis - used as the queue for Celery background jobs
* AWS ElasticSearch v7 - used for searching. The index can be rebuilt within about 5 minutes but the main views on the site won't show full data until the reindex is complete. 
* AWS ECS
  * AWS Fargate - used for server-less deployment of the Docker container. There are four tasks deployed
    1. A task that defines the main website, the docker container is started with the 'web' param for this. This can be 1..n number of apps deployed. Currently deployed as two tasks.
    2. A task that defines the celery workers, the docker container is started with the 'celery' param for this. This can be 1..n number of apps deployed. Currently deployed as two tasks.
    3. A task that defines the cron celery beat process, the docker container is started with the 'beat' param for this. This **must** be only 1 instance and should run with the smallest amount of resources possible. It's really just a cron that spawns tasks that will be executed via the celery workers.
    4. A task that allows us to execute migrations to the Postgres DB via Django migrations. This is only active during a deploy. It is built to exit after the migration command has been executed. 
  * AWS ECS docker repo
* DNS managed via Route53
* Email sent via Mailgun

**Resources**

* Terraform cloud workspace - used to apply infrastructure changes to AWS via Terraform - [https://app.terraform.io/app/sleuth-io/workspaces](https://app.terraform.io/app/sleuth-io/workspaces)
* Terraform Git repository - [https://github.com/sleuth-io/sleuth-terraform](https://github.com/sleuth-io/sleuth-terraform) and [https://github.com/sleuth-io/terraform-aws-sleuth-app](https://github.com/sleuth-io/terraform-aws-sleuth-app)



