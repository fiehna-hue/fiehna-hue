# Hi, I'm Fiehna 

I broke my own AWS pipeline 8 times on purpose to learn from it, and wrote every failure down.

Over the past few weeks I built a small AWS platform entirely in Terraform, and shipped it through a pull-request pipeline:

- Pull requests run terraform plan with a read-only role and post the plan as a comment
- Merging to main runs terraform apply with a separate write role
- GitHub Actions authenticates to AWS with OIDC, so there are no stored access keys
- The stack: VPC with isolated subnets, RDS Postgres with a managed password, private ECS Fargate tasks behind a load balancer, and VPC endpoints instead of a NAT gateway

The part I learned the most from was the failures: a trust policy that did not match GitHub's new OIDC subject (found in CloudTrail), an IAM permission missing at apply time that the read-only plan could not catch, and a text editor that silently corrupted a workflow file. Each one is in the incident log with symptom, diagnosis, cause, fix and lesson.

I built it, tested it end to end, and destroyed it through the same pipeline. The whole build cost well under a dollar.

Code, diagrams, IAM policies and the incident log:
https://github.com/fiehna-hue/aws-platform-as-code

I am looking for remote cloud and DevOps roles. If your team hires for that, I would love to hear from you.

#AWS #Terraform #DevOps #GitHubActions #CloudEngineering

## Projects

| Project | What it shows |
|---|---|
| [aws-platform-as-code](https://github.com/fiehna-hue/aws-platform-as-code) | Flagship project: Terraform modules (VPC, RDS, interface endpoints, ECS Fargate behind an ALB) shipped through a reviewed pipeline with OIDC, least-privilege IAM, a protected main branch, 8 documented incidents and design decisions |
| [inventory-infra](https://github.com/fiehna-hue/inventory-infra) | Production-style ECS Fargate stack in Terraform: ALB across two AZs, RDS in isolated subnets, Secrets Manager, autoscaling, CloudWatch alarm, and documented incident write-ups |
| [inventory-app](https://github.com/fiehna-hue/inventory-app) | Flask and Postgres API with Docker Compose, multi-stage non-root image, and a GitHub Actions pipeline that scans with Trivy and pushes to ECR using OIDC with no stored AWS keys |
| [cloud-labs](https://github.com/fiehna-hue/cloud-labs) | Smaller labs: Lambda container images and an ECS Fargate quickstart |
| [terraform-aws-lab](https://github.com/fiehna-hue/terraform-aws-lab) | Terraform AWS lab |

## Skills

AWS (EC2, VPC, IAM, S3, CloudWatch, ECS, ECR, RDS) · Terraform · CloudFormation · Docker · GitHub Actions · Linux and Windows · Active Directory and Entra ID · Microsoft 365 and Intune · ServiceNow

## How I work

Every lab ends with a verified teardown to keep costs near zero, and I write up what broke, how I diagnosed it, and the fix.

## Connect

[LinkedIn](https://www.linkedin.com/in/fiehna-njo-392170444)
