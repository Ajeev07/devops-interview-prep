# 01_CICD_Bamboo Notes

Bamboo – Topic 1: CI/CD Concepts Refresher
1️⃣ CI/CD Basics (Interview Perspective)
Continuous Integration (CI) →
Merging code frequently into a shared branch, running automated builds/tests to detect problems early.
Example: Every time you push a commit to develop, Bamboo builds the app, runs unit tests, and publishes artifacts.

Continuous Delivery (CD) →
Code is always in a deployable state; deployments can be triggered on demand.
Example: Bamboo pushes successful build artifacts to Nexus/XLD for staging deployment.

Continuous Deployment →
Fully automated deployment to production after passing tests (no manual approval).
Example: A successful build automatically deploys to prod via Bamboo + XLD without human intervention.

2️⃣ Bamboo Core Architecture
Server: Central app managing builds, plans, agents.

Agent: Executes build jobs. Can be local or remote.

Plan: Main build configuration — made up of Stages → Jobs → Tasks.

Stage: Sequential execution step in the pipeline.

Job: Groups related tasks that run on a single agent.

Task: Individual action — e.g., compile code, run tests, deploy.

3️⃣ Interview Trick Questions
Q: What’s the difference between a Bamboo job and a stage?
A: Stages run sequentially; jobs inside a stage run in parallel on available agents.

Q: How would you optimize Bamboo build time?
A: Use parallel jobs, caching, artifact sharing, and split long-running tests.

Q: Can Bamboo do deployment approvals?
A: Yes — via deployment projects with manual stages/approval gates.


Topic 2 – Bamboo Advanced Concepts
1️⃣ Variables in Bamboo
Global variables → Available to all plans across Bamboo.

Plan variables → Specific to a single plan; override global if same name.

Environment variables → Set per environment in deployment projects.

Use case:

{{env}} variable in your build can select dev/staging/prod config files automatically.

Interview tip:

Q: How do you manage secrets in Bamboo?

A: Use Bamboo secure variables, encrypted and masked in logs.

2️⃣ Artifacts
Definition → Files produced by a job that you want to share with other jobs/plans.

Types → Shared vs Linked artifacts.

Use case: Build JAR → share to next stage → deploy using XLD.

Interview tip:

Q: How do artifacts help in multi-stage pipelines?

A: Avoids rebuilding code, improves efficiency, and ensures consistency between stages.

3️⃣ Triggers
Manual → Run build manually

VCS Trigger → Run build on code commit (push)

Scheduled → Cron-like scheduled builds

Remote trigger → API call triggers a build

Interview tip:

Q: How do you ensure CI triggers only when relevant changes occur?

A: Configure VCS triggers with path filters, or branch-specific triggers.

4️⃣ Build Plan Best Practices
Keep stages small and modular → easier troubleshooting

Use parallel jobs where possible → faster builds

Maintain clean working directories → prevent artifacts from previous builds affecting current runs

Add unit tests + static analysis in early stages → catch errors before deploy

5️⃣ Real-World Bamboo Scenario (Interview Example)
Scenario:

You have a build plan with dev, staging, and prod stages.

Dev and staging deploy automatically. Prod requires manual approval.

Suddenly, staging deployment fails.

Questions to Answer:

How do you troubleshoot the failure?

What actions prevent prod deployment of broken code?

Sample Answer:

Check Bamboo job logs, artifacts, and agent output

Investigate failing tests or deployment scripts

Use manual approval gates on prod to prevent automatic deployment
