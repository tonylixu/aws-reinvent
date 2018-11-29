## DEV427: Deploy Serverless Apps With Python: AWS Chalice Deep Dive

Chalice
  - serverless microframework for AWS
  - quicly cretae and delpoy
  - AWS integrations

To install  
pip install chalice

Behind the scene
- Create app
- Deploy App (AWS reouce for pythoj to geenrate resource)
- Create a deployment package
- chalice will call create a lambda function
- run the lambda function

Don't need to worry about the AWS resources, chalice will manage that for you


genereate IAM role and policy automatically
Chalice can use cloudformation template
chalice can run locally
chalice will package all the requirements
handle heavy load (huge data from s3), you can config the default resource

Key features:
- App packaing
- IAM policy generation auto
- Lamdba event sources

Packaging:
- chalice will hands package dependency
- lib dir can allow you to break your app into mutiple files
- chalice will read the requirements and package it for you, env free, no need virtual env

Doesn't support green and blue deployment

Deplyent:
- zip file in .chalice
- deployment goes to .charlice/deployments

whl is precomipled packages

chalice doesn't have any hooks to docker, we want to make sure you don't need docker by default.

policy generation:
Role and policy attache to that rolw=e for the lambdot to be runing
lambda does include boto3 at run time
  - permission for cludwatch
  - describe regisons
  - Load the app.py, depends on the function it will auto match it with the corrisponding policy
  - wildcard "*" by default for auto-generated policy

Specify custom policy:
  - config.json file
  - Broke up by stages
  - policy.json file for custom polocies. "policy"+"stage".json
  
Lambda event sources:
  - s3 event source with chalice
  - cloudwatch event
  - REST API
  - SNS messages
  - SQS messages

Testing chalice code:
  - normal uni testing
  - chalice local mode

can't create resources yet


