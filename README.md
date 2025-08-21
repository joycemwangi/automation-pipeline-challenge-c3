# **Automation Pipeline Challenge C3**

<p align="center">
  <a href="https://github.com/joycemwangi/automation-pipeline-challenge-c3/actions/workflows/lint.yml">
    <img src="https://github.com/joycemwangi/automation-pipeline-challenge-c3/actions/workflows/lint.yml/badge.svg" alt="Lint status (GitHub Actions)">
  </a>
  &nbsp;
  <a href="https://codesandbox.io/p/github/joycemwangi/automation-pipeline-challenge-c3/main" target="_blank">
    <img src="https://img.shields.io/badge/Open%20in-CodeSandbox-blue?logo=codesandbox" alt="Open project in CodeSandbox">
  </a>
  &nbsp;
  <a href="https://kncqz4-8080.csb.app/healthz" target="_blank">
    <img src="https://img.shields.io/badge/Live%20Demo-OK-green" alt="Live Demo Health Check">
  </a>
</p>

<p align="center">
  <a href="https://www.ansible.com/">
    <img src="https://img.shields.io/badge/Ansible-2.14+-blue" alt="Ansible version 2.14 or higher">
  </a>
  &nbsp;
  <a href="https://www.python.org/">
    <img src="https://img.shields.io/badge/Python-3.11+-blue" alt="Python version 3.11 or higher">
  </a>
  &nbsp;
  <a href="https://kubernetes.io/">
    <img src="https://img.shields.io/badge/Kubernetes-1.27+-informational?logo=kubernetes" alt="Kubernetes version 1.27 or higher">
  </a>
  &nbsp;
  <a href="https://helm.sh/">
    <img src="https://img.shields.io/badge/Helm-3.12+-informational?logo=helm" alt="Helm version 3.12 or higher">
  </a>
  &nbsp;
  <a href="https://about.gitlab.com/stages-devops-lifecycle/continuous-integration/">
    <img src="https://img.shields.io/badge/GitLab-CI/CD-orange" alt="GitLab Continuous Integration and Deployment">
  </a>
</p>

<p align="center">
  <a href="https://github.com/joycemwangi/automation-pipeline-challenge-c3/blob/main/docs/submission.pdf">
    <img src="https://img.shields.io/badge/Submission-PDF-informational" alt="View project submission PDF">
  </a>
</p>

---

## **Overview**
This repository contains the solution for the **Automation Pipeline Challenge C3**, which involves designing and implementing an infrastructure solution for a scalable, secure, and observable client-facing media search and download API service.  
It reflects a transition toward a modern, containerized environment with automation, reliability, and operational excellence as priorities.

---

## 🔧 Tech Stack
- **Infrastructure as Code & Automation**: Ansible, Python, Bash  
- **Containerization & Orchestration**: Kubernetes, Helm, Docker  
- **Monitoring & Observability**: Zabbix Agent (system health and alerting)  
- **CI/CD Pipeline**: GitLab CI/CD for validation, build, deploy, smoke testing, and rollback  
- **Web & API Services**: Nginx (HTTPS, SSL certs), Node.js demo API  
- **Version Control & Collaboration**: GitHub, GitLab, Git  

---

## 🌟 Key Features
- **End-to-End Automation** – Infrastructure provisioning, configuration management, and CI/CD pipeline in one workflow.  
- **Secure by Design** – Automated HTTPS, SSL certificate handling, and hardened configurations.  
- **Proactive Monitoring** – Integrated Zabbix Agent for real-time health checks and alerting.  
- **Kubernetes-Ready** – Helm charts and Kubernetes deployments for scalability across environments.  
- **Resilient Deployments** – GitLab pipeline enables validation, smoke testing, gated promotions, and rollback.  
- **Operational Efficiency** – Automated OS patching, reboot workflows, and repeatable deployments reduce manual effort.  

---

## **Implementation Details**
- **Infrastructure as Code**: Ansible playbooks and roles to provision and configure a load balancer, application servers, and monitoring agents.  
- **Role-Based Configuration Management**: Modular roles for Nginx, Zabbix Agent, and maintenance tasks enable reusability and easier maintenance.  
- **Security & HTTPS Support**: Automated SSL certificate creation and integration with Nginx for secure API access.  
- **Observability**: Zabbix Agent deployment and configuration for real-time monitoring and system health tracking.  
- **Automated Maintenance**: Playbooks to apply the latest OS patches and reboot servers automatically.  
- **CI/CD Integration**: GitLab pipeline with validation, Kubernetes deployment, smoke testing, promotion between environments, and rollback.  
- **Multi-Environment Support**: Flexible inventory and variable structure for dev, staging, and production without code changes.  

---

## **Extended Description**
This project demonstrates an end-to-end automation workflow for deploying and managing Linux-based infrastructure and application services.  

The solution emphasizes:  
- **Automation** – Ansible playbooks and roles provide consistent provisioning, configuration, and maintenance.  
- **Security & Reliability** – HTTPS setup, SSL certificates, and hardened system configurations.  
- **Observability** – Integration of Zabbix Agent for real-time health and performance tracking.  
- **Scalability** – Kubernetes + Helm enable repeatable deployments across dev, staging, and production.  
- **CI/CD Excellence** – GitLab pipeline automates validation, builds, deployments, smoke tests, promotions, and rollbacks.  

This design reflects a shift toward **modern, containerized infrastructure** with automation, observability, and operational resilience as core principles.  

---

## Automation Pipeline Diagram

<p align="center">
  <a href="docs/automation-pipeline.png" target="_blank">
    <img src="docs/automation-pipeline.png" alt="Automation Pipeline" width="500">
  </a>
</p>

---
## Repository Structure
```text
automation-pipeline-challenge-c3/
├── ansible/
│   ├── inventories/
│   │   └── hosts.ini
│   ├── group_vars/
│   │   └── all.yml
│   ├── roles/
│   │   ├── nginx/
│   │   │   ├── tasks/main.yml
│   │   │   └── templates/
│   │   │       ├── nginx.conf.j2
│   │   │       └── site.conf.j2
│   │   ├── zabbix_agent/
│   │   │   ├── tasks/main.yml
│   │   │   └── templates/zabbix_agentd.conf.j2
│   │   └── maintenance/
│   │       └── tasks/main.yml
│   ├── playbooks/
│   │   ├── site.yml
│   │   ├── maintenance.yml
│   │   └── certs_create.yml
│   └── ansible.cfg
├── demo-api/
│   ├── Dockerfile
│   ├── package.json
│   ├── server.js
│   └── helm/
│       └── demo-media-api/
│           ├── README.md
│           └── templates/_helpers.tpl
├── .gitlab-ci.yml
├── README.md
└── docs/
    ├── automation-pipeline.png
    └── submission.pdf
```

## **How the Roles Work**

| Role             | Purpose                               | Key Tasks                                                                 |
|------------------|---------------------------------------|---------------------------------------------------------------------------|
| **nginx**        | Configure and deploy NGINX web server with HTTPS support | Install NGINX, deploy `nginx.conf` & `site.conf` templates, configure SSL certificates, start and enable service |
| **zabbix_agent** | Deploy monitoring agent for observability | Install Zabbix agent, configure `zabbix_agentd.conf`, enable active checks, start and enable service |
| **maintenance**  | Automate system maintenance tasks     | Apply latest OS patches, reboot if required, clean up logs, rotate files |


## **Prerequisites**
- **Ansible** >= 2.14
- **Python** >= 3.11
- Git installed locally
- SSH access to target hosts

---
## **Setup & Usage**

**Clone the repository:**
```bash
git clone https://github.com/joycemwangi/automation-pipeline-challenge-c3.git
cd automation-pipeline-challenge-c3
```

**Run the main playbook:**
```bash
ansible-playbook -i ansible/inventories/hosts.ini ansible/playbooks/site.yml
```

**Run maintenance tasks:**
```bash
ansible-playbook -i ansible/inventories/hosts.ini ansible/playbooks/maintenance.yml
```

**Generate or manage certificates:**
```bash
ansible-playbook -i ansible/inventories/hosts.ini ansible/playbooks/certs_create.yml
```

---

## **Contributing**

We welcome contributions to improve this project.

**Steps**
1. **Fork the repository** on GitHub.
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature
   ```
3. **Commit changes**
   ```bash
   git commit -m "Add feature"
   ```
4. **Push to your branch**
   ```bash
   git push origin feature/your-feature
   ```
5. **Open a pull request** for review.

**Guidelines**
- Follow the repository’s coding style and directory structure.
- Update documentation for any changes affecting usage.
- Ensure playbooks pass syntax and lint checks before submission.

## **Local Validation (No Servers Required)**

This repository includes a localhost inventory and a render-only playbook so you can validate roles and templates without access to the challenge infrastructure.

**Goals**
- Validate Jinja2 templates and Ansible variables without touching real servers
- Ensure NGINX and Zabbix configurations compile cleanly
- Keep generated files out of version control

**Steps**
```bash
# From the repo root
ansible-playbook -i ansible/inventories/localhost.ini ansible/playbooks/render_templates.yml
ls -l ansible/temp/
```

**Expected Output**
```text
site-lb.conf
site-web.conf
zabbix_agentd.conf
```

**Files Involved**
- `ansible/inventories/localhost.ini` — localhost-only inventory
- `ansible/playbooks/render_templates.yml` — renders templates to `ansible/temp/`
- `ansible/temp/` — output workspace (ignored by Git except for `.gitkeep`)

`ansible/temp/` is intentionally in `.gitignore` so generated files don’t get committed.

## **CI/CD Pipeline (GitLab)**

Automates testing, build, deployment, and rollback for the API on Kubernetes.
The complete pipeline definition is available in [`.gitlab-ci.yml`](./.gitlab-ci.yml).

**Goals**
- Enforce quality through YAML linting, Ansible lint, and syntax checking.
- Build API container and push to GitLab Container Registry.
- Deploy to Kubernetes (Dev → Staging → Prod) using Helm or `kubectl`.
- Run smoke tests after each deployment.
- Enable one-click rollback via Helm.

**Stages**
- **validate** – Run `yamllint`, `ansible-lint`, Ansible syntax check, and render templates locally.
- **build** – Build and push API image (tags: `latest` + commit SHA).
- **deploy** – Helm upgrade/install to target namespace with new image tag.
- **smoke** – Test `/healthz` endpoint in Kubernetes service.
- **promote** – Manual approvals for staging → prod promotion.
- **rollback** – Manual Helm rollback to previous release.

**Secrets & Config**
- Store secrets as masked GitLab CI/CD variables:
  `KUBE_CONFIG`, `HELM_REPO_AUTH`, `ANSIBLE_VAULT_PASSWORD`
- Use Kubernetes Secrets or GitLab Vault for sensitive values.
- Environment configs:
  - Separate Helm values files (`values-dev.yaml`, `values-staging.yaml`, `values-prod.yaml`)
  - Or use GitLab environment variables.

**Rollback Strategy**
- **Helm**: `helm rollback` to a previous release.
- **Image pinning**: Redeploy last-known-good image tag.

This pipeline covers automated validation, Kubernetes deployments with gated promotions, and rapid rollback, aligned to a modern containerized infrastructure.

## **Executable Demo**

<p align="center">
  <a href="https://codesandbox.io/p/github/joycemwangi/automation-pipeline-challenge-c3/main" target="_blank">
    <img src="https://img.shields.io/badge/Open%20in-CodeSandbox-blue?logo=codesandbox" alt="Open in CodeSandbox">
  </a>
</p>

### **Local Run (WSL)**

1. **Open a terminal** and go to the `demo-api` folder:
   ```bash
   cd ~/automation-pipeline-challenge-c3/demo-api

2. **Install dependencies:**

         npm install

3. **Start the API (runs on port 8080):**

         npm start

     You should see:

         Demo Media API listening on :8080

4. **Test the endpoints from a second terminal:**

    Health check

          curl -fsSL http://localhost:8080/healthz
    Output:

          ok

    Example search

         curl -fsSL "http://localhost:8080/search?q=sunset"

    Output:

         {"query":"sunset","count":1,"results":[{"id":"img_001","title":"Sunset over dunes","type":"image"}]}

  Note: This mock API is provided for demonstration purposes only and does not connect to real Elasticsearch or storage backends.

## **License**
This project is licensed under the MIT License.
# trigger linguist refresh

Note: Local validation works without extra setup.

<!-- lint demo -->
