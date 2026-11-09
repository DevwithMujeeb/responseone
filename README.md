# ResponseOne

An automated DevSecOps pipeline that scans a web application for vulnerabilities on every run, using OWASP ZAP, Docker, and GitHub Actions on a self-hosted runner.

Built as part of a team project during Expadox Lab Cohort 3, working toward full SOAR (Security Orchestration, Automation and Response) automation.

## What it does

1. A target web application runs in Docker (OWASP Juice Shop, a deliberately vulnerable app, used as the scan target).
2. A GitHub Actions workflow, triggered on push, runs an OWASP ZAP baseline scan against the target.
3. The scan report is saved as a build artifact.
4. A break gate fails the pipeline if the scan finds medium or higher severity issues, so vulnerable code cannot pass the security gate.
5. Scan findings are sent to a Shuffle SOAR workflow for further automation.

## Why it fails on purpose

A pipeline that only reports findings is easy to ignore. This one enforces a gate: if ZAP finds 2 or more medium or higher severity issues, the build fails. That forces vulnerabilities to be looked at before anything ships.

## Stack

- Docker
- OWASP ZAP (baseline scan)
- OWASP Juice Shop (scan target)
- GitHub Actions, self-hosted runner
- Shuffle (SOAR automation)

## Status

Core scanning pipeline and break gate are working. SOAR automation with Shuffle is in progress.

## Role

Built the self-hosted runner infrastructure, the ZAP scanning workflow, and the break gate logic, as part of a team working on broader SOAR automation.
