# SRE Foundations

[course link](https://cloudacademy.com/course/site-reliability-engineering-sre-foundation-introduction-1044)

## SRE Principles and Practices

### What is Site Reliability Engineering

- Created at Google around 2003 and publicized via the [SRE Book](https://learning.oreilly.com/librry/view/-/9781491929117/) and the [SRE Workbook](https://learning.oreilly.com/library/view/-/9781492029496/) and [Seeking SRE](https://learning.oreilly.com/library/view/seeking-sre/9781491978856/)
- SRE is a discipline that incorporates **aspects of software engineering** and applies them to **infrastructure** and **operations problems**.
- [Google resources](https://landing.google.com/sre)
- The goal is to create ultra-scalable and highly reliable distributed software system.
- SRE's spend 50% of their time doing ops related work such as issue resolution, on-call and manual interventions.
- SRE's spend 50% of their time on development tasks such as new features, scaling or automation.
- Monitoring and alerting are key to SRE.

SRE is now spread well beyond Google and many organizations are adopting SRE principles.

[SRE Weekly](https://sreweekly.com/)

## SRE and DevOps, What's the Difference?

- DevOps is a set of practices, guidelines and culture designed to breakdown silos in IT development and operations, architecture, network and security.
- SRE is a set of practices that Google has developed to manage services at scale.

### DevOps 5 Key Pillars of Success

1. Reduce organizational silos
2. Accept failure as normal
3. Implement gradual changes
4. Leverage tooling and automation
5. Measure everything

### SRE Principles and Practices

1. Operations is a software problem
   1. The basic tenet of SRE is that doing operations well is a software problem.
   2. SRE should therefor use software engineering approaches to solve that problem.
   3. Software engineering as a discipline focuses on designing and building rather than operating and maintaining.
2. Service Levels
   1. SLO(Service Level Objectives) is an availability target for a product or service(this is **never** 100%).
   2. SRE services are managed by SLOs.
   3. SLI(Service Level Indicators) are the metrics that are used to measure the service.
   4. SLA(Service Level Agreement) specifies a target level of service for the reliability of your service.
   5. SLO(Service Level Agreement) business contract that comes into effect when your users are so unhappy you have to compensate them in some fashion.
3. Toil
   1. Any and all manual, mandated operational task is bad
   2. If a task can be automated, it should be automated.
   3. Tasks can provide the "wisdom of production" that will inform better system design and behavior
   4. SREs must have time to make tomorrow better than today.
4. Automation
   1. Automate what is currently done manually
   2. Decide what to automate and how to automate it
   3. Take an engineering-based approach to automation and tasks rather than just toiling at them over and over.
   4. This should dominate what an SRE does.