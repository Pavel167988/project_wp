
## Project report

**Project's reporter:** Pavel Kostenko

**Group number:** md-sa2-22-22

### Description of application for deployment

**- Name of application - Wordpress
- Which programming language is this application written in: PHP
- What kind of DB: MariaDB
- Link on git repository/site/package repository: https://github.com/Pavel167988/project_wp**

### Pipeline. High Level Design

_Scheme here_

### Technologies which were used in project

**Orchestration: K8s**

**Automation tools: Ansible, Github Actions, Argo-CD**

**Monitoring: Prometheus, Alertmanager, Grafana, Grafana Loki**

**Notification: Slack**

**CI description: 

The developer push the code to the repository in the master branch, github actions:
- Creates a new tag
- Install docker
- Build image and pushes that image with the tag that was originally generated
- Makes a backup of the database and puts it in a folder on the machine where the database is installed
- Changes lines in files(Values.yaml, Chart.yaml) to a new tag
- Helm build the package and pushes all the changes to the repository
- Devops receives a notification about the successful completion of the pipeline**

**Deployment flows short description:

After a commit in the repository, Argo-CD synchronizes with the repository, sees the changes in the file (index.y**aml), namely targetRevision and install new application in Kubernetes. If pod is down alertmanager send notification in Slack.**


**Rollback flow description and implementation:

ArgoCD can rollback apps in WebUI interface.** 

### Links

[Repository with pipeline and app](https://github.com/Pavel167988/project_wp)
[Images in Docker Hub](https://hub.docker.com/repository/docker/pavelogs/wordpress/general)
