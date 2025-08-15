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
