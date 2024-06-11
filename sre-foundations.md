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

### SRE and its Principles

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
   5. Do not automate a bad process - Fix the process first.
   6. Sometimes in SRE we talk about, "automating ourselves out of a job" - this is a good thing.
5. Reduce cost of failure
   1. Late problems (defect) discovery is expensive so SRE looks for ways to avoid this
   2. Look to improve MTTR(Mean Time to Recovery) and MTBF(Mean Time Between Failures)
   3. Smaller Changes = Smaller Failures
   4. Canaries and Blue-Green deployments are ways to reduce the cost of failure.
6. Shared Ownership
   1. SREs share skill sets with product development teams
   2. Boundaries between "application development" and "production"(Dev & Ops) should be removed.
   3. SREs "shift left" and provide "wisdom of production" to development teams.
   4. In SRE we encourage **more** engineers to have experience of production deployments, **not less**
   5. No one team or individual should become the ops team.

> 💡 "Shift left" is a practice in software development that involves integrating important development practices, such as testing, quality assurance (QA), and security measures, earlier in the software development lifecycle (SDLC). The phrase is also known as "Start Left" and is a central pillar of DevOps and DevSecOps.

## SRE Service Level Objectives and Error Budgets

### What is a SLO?

- A Service Level Objective is a goal for how well a product or service should operate
- SLOs are tightly linked to user experience
  - If the SLOs are being met then the user will be happy
- Setting and measuring service level objective is a key aspect of the SRE role
- The most widely tracked SLO is availability
- Products and services could and should have multiple SLOs
- We use SLIs to measure if we are meeting our SLOs
- Monitoring tool or service will provide the data used for checking compliance against the SLOs
- 99.9% of web requests should be successful
  - If there are 1 million requests, 1000 can fail and this is an **error budget**
- Failure to hit an SLO must have consequences. If more than 1000 requests fail in a month the some remedial action must be taken. And this is an **error budget policy**

> 💡 SLO's are the most important component of SRE. They are the key to understanding how well a service is performing and how well it is meeting the needs of its users.

According to the [2023 Catchpoint](./docs/catchpoint.pdf) the things that teams are monitoring or measuring are:

1. Availability/Uptime: 78%
2. Performance/Response Times: 71%
3. Latency: 64%
4. Error Rates: 64%
5. Throughput(MBs or requests per second): 48%
6. Unauthorized Requests: 29%
7. Saturation: 25%

Availability is the same thing as uptime, e.g. does a service respond to a request?

Response time is the total time it takes from when a user makes a request until they receive a response.

Latency is the delay incurred in communicating a message(the time a message takes to travel from the sender to the receiver).

## SRE Error Budgets

> 💡 100% is the wrong reliability target for basically everything.

[Risk and Error Budgets](https://dominiquehallan-links.com/risk-and-error-budgets)

### Error Budgets: Good and Bad

- **Bad**
  - We have error budgets in SRE as
going over budget usually means
someone somewhere will have to
work over-time or respond to
out-of-hours issues
Not hitting 99.9% of HTTP
requests in a month usually
means scalability issues so "ops"
need to do something
- **Good**
  - On the other hand SRE practices
encourage you to strategically burn
the budget to zero every month,
whether it's for feature launches or
architectural changes
This way you know you are running
as fast as you can (velocity) without
compromising availability

### Error Budgets: Fixed?

The negotiation to relax the SLO error budget bridges the gap and improves communication and understanding between Dev and Ops and the business. Watch out for high-risk deployments or large big-bang changes because they have a likelihood of issues and therefore more chance to blow the error budget.

This should encourage the lean preference for small, incremental changes. In some cases the error budget may need to change to accommodate complex releases but this needs to be agreed upon by Dev and Ops and the business

### Error Budget Policies

Missed SLO's have noticeable consequences on business performance:

- Lost Revenue: 70%
- Drop in Employee productivity: 57%
- Lost Customers: 49%
- Social Media backlash: 36%

> There will be no new feature launches allowed. Sprint planning may only pull post-mortem action items from the backlog. Software engineering teams must meet with SRE team daily to outline their improvement plans.

- As an example HB could have a availability SLO of 99.9%
- Every month this allows for 43 minutes of outages
- New feature releases, patches, planned and un-planned downtime need to fit into this 43 minutes

| Number of Nines | Availability (%) | Downtime per Year               | Downtime per Month      | Downtime per Week       | Downtime per Day       |
|-----------------|------------------|---------------------------------|-------------------------|-------------------------|------------------------|
| 1               | 90.0             | 36 days, 12 hours               | 72 hours                | 16 hours, 48 minutes    | 2 hours, 24 minutes    |
| 2               | 99.0             | 3 days, 15 hours, 36 minutes    | 7 hours, 12 minutes     | 1 hour, 40 minutes      | 14 minutes, 24 seconds |
| 3               | 99.9             | 8 hours, 45 minutes, 36 seconds | 43 minutes, 12 seconds  | 10 minutes, 4.8 seconds | 1 minute, 26.4 seconds |
| 4               | 99.99            | 52 minutes, 33.6 seconds        | 4 minutes, 19.2 seconds | 1 minute, 0.48 seconds  | 8.64 seconds           |
| 5               | 99.999           | 5 minutes, 15.36 seconds        | 25.92 seconds           | 6.048 seconds           | 0.864 seconds          |

**Notes**:
- Downtime per Year is based on 365 days per year.
- Downtime per Month is based on 30 days per month.
- Downtime per Week is based on 7 days per week.
- Downtime per Day is based on 24 hours per day.

### Discussion: What error budget policies would you use to enforce an availability SLO?

1. Minimize deployment downtime
2. Minimize infrastructure outages
3. Address Scalability and performance issues

How could you achieve these?

- cloud automation
- cloud immutable infrastructure
- load balancing
- caching
- zero downtime deployments
- A/B deployments
- Canary deployments

## The VALET Dimension of SLO

| Dimension      | SLO                                                          | Budget                                                       | Policy                     |
|----------------|--------------------------------------------------------------|--------------------------------------------------------------|----------------------------|
| Volume/Traffic | Does the service handle the right volumes of data or traffic | Budget 99.99% of HTTP requests per month succeed with 200 OK | Address scalability issues |
| Availability   | Is the service available when needed                        | Budget 99.9% availability/uptime | Address downtime issues/outages, zero downtime deployments |
| Latency        | Does the service deliver in a user-acceptable period of time? | Payload of 90% of HTTP responses returned in under 300ms | Address performance issues, caching, load balancing |
| Errors | Is the service delivering the capabilities being requested? | 0.01% of HTTP requests return 4xx or 5xx status codes | Analyze and respond to main status codes, new functionality or infrastructure may be required |
| Tickets | Are  our support services efficient? | 75% of service tickets are automatically resolved | Automate more manual process|
