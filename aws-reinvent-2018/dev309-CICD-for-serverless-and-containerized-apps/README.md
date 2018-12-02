## DEV309 CI/CD For Serverless and Containerized Applications

Approchaes Modern app


## Two platfomrs
- Lambda
- Fargate - containers specific

## Release process stages
Source -> Build -> test -> Prod
CI: source + build
CD: CI + test + prod

source:
- check-in
- Peer review new code

Build
compile, unitests, style cehckers, create contianers and function deployment packages

Test
- Integration tets, load test, UI test, security testing

Production
- Deploy to prod, monitor code and detect errors

## Effects of CI/CD
- devops report
- deployemnt frequency: weekly - month to hoursly - daily
- lead time: 1 - 6 months to 1-7 days (Lead time: code checkin to customer use the new feature)
- change failure rates: 46-60% to 0-15%
48% of teams in the industy able to achieve the above results

## 3 pillars
CI, CD, Infra as code

## CI
- source + build automated
CI goals:
- Automatic
- Build and tsst in a consistent repeatable env
- Contnually have an artifact ready for deploy
- Continually close feedback loop when build fails
(AWS codepipeline)

  CodePipelne
    - support docker image tags now
    - support webhooks

  Codebuild
    -Lambda buildspec

## CD
- source + build + test + prod deploy
Goals:
- Auto deploy new changes to staging env for testing
- deploy to prod safely without impacting customers
- Deliver to customers faster
Tools:
- AWS CodeDeploy

Codedeploy-lmabda deployemnt
- shifts traffic
- choose canary ("shift 10% of traffic")
- validatio hooks enable testing at each stage
- Fast rollback in secons if case of hook failure
- Monitor deployment status and history via console, api, sns notifications

Virtual lambda deploy
API gateway -> all traffic toes to v1 code
v2 code spin up, all traffic still goes to v1
shift 10% traffic to v2 code
wait 10 mins
After 10 mins, if no alarms, shift the rest of 90%

blue-green
- provistion some contianers as green (new contianer)
- Flip traffic at LB level, from blue (old) to green
- validation hooks enable testng at each stage of the deployment
- Fast rollback to "blue" in seconds if need
- MOnitor deployment status and history vida console, API, SNS and cloudwatch
- use codedeploy-ECS deploy action in codepipeline or "AWS ecs deploy" command in jenkins

ECS blue-green deploy
App LB server 100% traffic
add a test traffic listener and target group 2 which will be used for flip traffic
two 100% scale sets running in parallel
once group2 is stable, 100% test traffic will go to group2
once validation hook succeeds, traffic will flip and LB level
If error ocurs, it will rollback to blue
Once the wait period passed

Container deployment safty
- docker tagging, "latest" tag is for ppl, not for deployment
- use "latest" pr "prod" cam resilt in untested code in prod
- Use unique "immutable" tags
- Other wise during a scale out event, you might get into mixed fleet situation

Best practices:
- use SHA256 digest
- use build-id


## Infra as code
- Mkae infra changes repeatable and predictable
- Release infra changes using the same tools as code changes
- Replicate production env in a staging env to enable continuous testing

 valkdate an artifact at build stage
 - uni tests
 - static analysis
 - mocked dependencies and envs
 - vulnerability image sancs
 validate an env at test stages


 Example for release infra as code:
 source stage ->

 ## SAM
 - serverless application model
 - sam cli to package and deploy sam templates
 - Jenkins SAM cli plugin

 Cloud Development Kit
 - Opensource framework fo define cloud infrastructure in typesript

 chatbot as lambda function

