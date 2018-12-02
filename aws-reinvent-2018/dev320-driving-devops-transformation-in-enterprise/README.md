## Notes

Youtube: https://www.youtube.com/watch?v=qlVdUMcjfBY

Why does DevOps matter?

DevOps Model

Key DevOps Practices

AWS OpsWorks
- chef automate
- puppet
- stacks: manage servers and model server with stacks and layers

OpsWorks is part of AWS management tools

Over the years:
- consume software in demand
- decentralized decision making
- Operations getting more complex
- Dev and Ops have different goals and needs
- Enterprise ships software with low velocity
- Low v -> unhappy customers
- Then you loose competitivity

Enterprise + DevOps = Enterprise with superpowers

Benefits of DevOps
- Speed: microservices and CD, reduce lead time between commit and deliver,
  even fixes
- Raoid delivery: CI+CD, automate software release process, increaing the
  deployment frequency
- Reliability: automation let issues goes down, monitoring and alerting
- Sacle: infra + config as codei
- Improved collaboration: issue tracking, slack, hangover time reduced
- Security: Infra + config as code allows apply compliance

Elite performers have:
- 46x frequent code deployments
- 2,555x times fster
- 7x lower

What is DevOps?
- As AWS< combination of three things: culture, practices and tools

In practice:
- Delivery pipeline
- Monitor allow fast feedback loop

DevOps Model:
- culture: change in culture and mindset, continuous learning, retro meetings,
  create feedback loop, blameless model
  - You build it, you run it
  - Brig developers in contact with ops, monitoring and logging
- Tools: pick quick, run quickly, like keep it, move on quickly
- Practices:
  - Microservices: decouple into small managable units
      - Isolate infra structure
  - Infra as code: benefit from versioning, try changes quickly, knowledge is shared
    between teams, more reliability, self-documented
      - Cloudformation template per env
      - Can be extended to config as code
      - Policy as code
  - Continuous delivery:
      - Time consuming part is the transition period
      - Continuous integration: practicse where devs periodicaaly merge code
        for testing
      - Automated testing: Find bugs quicker

AWS OpsWork:
  - You can spin up a chef automate server very easily
  - To bootstrap, you can create a config file
  - Launch configuration + autoscaling groups

CodePipeline:
  - Deliver configuration changes
  - CodeBuild will use chef utility to build
  - Package the cookbooks to s3 bucket
  - Once approved, retrieve the package from S3 and depackage
  - Upload to centralized chef server
  - Scheduled chef run will pickup the new cookbook and apply to new servers

Berksfile
  - Contains source and list of cookbooks

Monitoring and logging:
  - Cloudwatch

Questions:
  - Where are we in terms of culture, practice and tools?
  - How do we improve?
  - What's the 1 month, 2 month, quater goal?

