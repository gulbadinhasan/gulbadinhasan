<!-- ═══════════════════════════════════════════════════════════════
     GULBADIN HASAN — GitHub Profile README
     Domain-targeted · SRE · DevOps · Cloud · Security
     Animation: Claude Code stream style
═══════════════════════════════════════════════════════════════ -->

<div align="center">

<!-- CLAUDE CODE STREAM — single purposeful line, not a skill carousel -->
<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=14&duration=1&pause=99999&color=FFFFFF&background=000000&center=true&vCenter=true&multiline=true&width=760&height=110&lines=%3E+Analysing+infrastructure+profile%3A+gulbadin-hasan+...;%E2%9C%94++sre_signal+++++++%E2%80%94+99.7%25+SLA+%C2%B7+MTTR+%E2%86%9340%25+%C2%B7+0+sev-1+post-migration;%E2%9C%94++cloud_savings++++%E2%80%94+%2430K%2Fmonth+recovered+%C2%B7+%24360K+annualised;%E2%9C%94++deploy_velocity+%E2%80%94+400%25+faster+%C2%B7+failure+rate+%E2%86%9333%25;%E2%9C%94++security_audit++%E2%80%94+PCIDSS+compliant+%C2%B7+0+critical+findings;%3E+%E2%96%88" alt="claude-code-stream" />
</a>

<br/>

<!-- IDENTITY — one line, no badge soup -->
```
gulbadin hasan  ·  lead devops engineer  ·  10+ years  ·  india
```

<!-- CONTACT — minimal, dark, monospace -->
<a href="mailto:gulbadinhasan1@gmail.com"><img src="https://img.shields.io/badge/mail-gulbadinhasan1%40gmail.com-000?style=flat-square&labelColor=000&color=fff&logo=protonmail&logoColor=fff" /></a>
&nbsp;
<a href="https://linkedin.com/in/gulbadin-hasan"><img src="https://img.shields.io/badge/linkedin-gulbadin--hasan-000?style=flat-square&labelColor=000&color=fff&logo=linkedin&logoColor=fff" /></a>
&nbsp;
<a href="https://gulbadin-hasan.dev"><img src="https://img.shields.io/badge/portfolio-gulbadin--hasan.dev-000?style=flat-square&labelColor=000&color=fff&logo=gnubash&logoColor=fff" /></a>
&nbsp;
<img src="https://komarev.com/ghpvc/?username=gulbadinhasan&style=flat-square&color=000&label=views" />

</div>

<br/>

---

## `> whoami`

```yaml
name        : Gulbadin Hasan
title       : Lead DevOps Engineer
experience  : 10+ years  (Jan 2014 – present)
location    : India
education   : B.E. Computer Science, Nagpur University

platforms   : AWS (primary) · Kubernetes · Terraform · ArgoCD
cicd        : GitHub Actions · Jenkins · GitOps
observ      : OpenTelemetry · Splunk · New Relic · Prometheus · Grafana
security    : PCIDSS · Zero-Trust · Vault · KMS · Security Hub
ai_tooling  : LangChain · Ollama · RAG · Vector-DBs · Embeddings

open_to     : Lead DevOps · Principal Engineer · Platform Eng · Cloud Arch
available   : Immediate  ·  Remote or Hybrid
response    : < 24 hours
```

---

<!--
════════════════════════════════════════════════════════
  SECTION 01 — SRE RECRUITER
  Format: Prometheus alerting rule + SLO burn report
  Signal: uptime, MTTR, error budget, incident hygiene
════════════════════════════════════════════════════════
-->

## `> promtool check rules sre_profile.yml`

```yaml
# ── SLO REPORT ── service: platform-production ────────────────────
groups:
  - name: gulbadin.sre.signals
    rules:

      - alert: SLOBreached
        expr: slo_achieved < 0.997
        for: 0m
        labels:
          severity: critical
        annotations:
          summary: "SLO target not met"

      # current evaluation ─────────────────────────────────────────
      - record: slo_target
        expr: 0.997                        # 99.7%

      - record: slo_achieved
        expr: 0.997                        # ✔  within budget

      - record: error_budget_remaining
        expr: 0.0018                       # 60% of budget intact

      - record: mttr_improvement
        expr: -0.40                        # ↓ 40%  (OpenTelemetry)

      - record: sev1_incidents_post_migration
        expr: 0                            # ✔  zero  (blue-green)

      - record: k8s_upgrade_downtime
        expr: 0                            # ✔  zero  (1.23 → 1.29)

# ── RESULT ───────────────────────────────────────────────────────
# SUCCESS  ·  0 alerts firing  ·  all SLOs within budget
```

---

<!--
════════════════════════════════════════════════════════
  SECTION 02 — DEVOPS RECRUITER
  Format: CI/CD pipeline run log
  Signal: deploy frequency, failure rate, lead time
════════════════════════════════════════════════════════
-->

## `> argocd app list --output=wide`

```
Pipeline: deploy-to-production                          [PASSED ✔]
───────────────────────────────────────────────────────────────────
Stage                    Duration   Status   Notes
───────────────────────────────────────────────────────────────────
checkout                     2s     ✔
lint + validate             14s     ✔
unit tests                  38s     ✔
security scan               11s     ✔        0 critical CVEs
build + push                42s     ✔
deploy (canary 10%)          2m     ✔        0 errors in canary
promote (canary 100%)        1m     ✔        0 rollbacks triggered
notify                       1s     ✔
───────────────────────────────────────────────────────────────────
Total                        ~5m    ✔ PASSED

before ArgoCD self-service  →  days      after  →  ↑ 400% faster
change failure rate         →  baseline  after  →  ↓ 33%
EKS cluster upgrades        →  1.23 to 1.29    →  zero downtime
deployment strategy         →  blue-green + canary across all envs
───────────────────────────────────────────────────────────────────
```

---

<!--
════════════════════════════════════════════════════════
  SECTION 03 — CLOUD RECRUITER
  Format: terraform plan diff — cost as infrastructure
  Signal: cost savings, architecture, scale decisions
════════════════════════════════════════════════════════
-->

## `> terraform plan -out=cost_optimisation.tfplan`

```hcl
Terraform will perform the following actions:

  # ── Arkose Labs · database & infrastructure optimisation ────────

  ~ resource "aws_db_instance" "analytics_primary" {
      instance_class  = "db.r5.4xlarge" -> "db.r5.2xlarge"
      multi_az        = true             # retained
    }
    # saving: $11,200 / month

  ~ resource "aws_eks_node_group" "data_workers" {
      instance_types  = ["m5.4xlarge"]  -> ["m5.2xlarge"]
      desired_size    = 12              -> 8
    }
    # saving: $9,400 / month

  ~ resource "aws_elasticache_cluster" "session_store" {
      node_type       = "cache.r6g.2xlarge" -> "cache.r6g.xlarge"
    }
    # saving: $5,800 / month

  + resource "aws_cost_anomaly_detector" "weekly_report" {
      threshold_expression = "ANOMALY_TOTAL_IMPACT_ABSOLUTE > 500"
      notify               = ["finance@arkose.com", "devops@arkose.com"]
    }

  ─────────────────────────────────────────────────────────────────
  Plan:  1 to add  ·  3 to change  ·  0 to destroy

  Changes to monthly cost estimate:
    before  $78,400 / month
    after   $48,400 / month
    saving  $30,000 / month  ·  $360,000 / year        ✔
  ─────────────────────────────────────────────────────────────────

  certified  →  AWS Solutions Architect Professional (2023)
  certified  →  HashiCorp Terraform Associate (2023)
```

---

<!--
════════════════════════════════════════════════════════
  SECTION 04 — SECURITY RECRUITER
  Format: trivy scan + audit log output
  Signal: compliance, zero findings, secrets hygiene
════════════════════════════════════════════════════════
-->

## `> trivy config . && aws securityhub get-findings`

```
┌─────────────────────────────────────────────────────────────────┐
│  SECURITY AUDIT — gulbadin-hasan — full scope                   │
├──────────────────────────────┬──────────────────────────────────┤
│  check                       │  result                          │
├──────────────────────────────┼──────────────────────────────────┤
│  iam_long_lived_credentials  │  ✔  NONE — migrated to roles     │
│  secrets_management          │  ✔  Vault  ·  KMS encrypted      │
│  pcidss_compliance           │  ✔  COMPLIANT  ·  0→1 build      │
│  critical_cves               │  ✔  0 critical  ·  0 high        │
│  privileged_containers       │  ✔  NONE detected                │
│  network_exposure            │  ✔  zero-trust enforced          │
│  eks_rbac                    │  ✔  least-privilege applied      │
│  cloudtrail_logging          │  ✔  all regions enabled          │
│  security_hub_score          │  ✔  passing all standards        │
├──────────────────────────────┼──────────────────────────────────┤
│  TOTAL CRITICAL FINDINGS     │  0                               │
│  TOTAL HIGH FINDINGS         │  0                               │
│  COMPLIANCE STATUS           │  PCIDSS COMPLIANT                │
└──────────────────────────────┴──────────────────────────────────┘

  certified  →  AWS Solutions Architect Professional
  tools      →  Vault · KMS · IAM · Security Hub · CloudTrail
```

---

<!--
════════════════════════════════════════════════════════
  SECTION 05 — CAREER
  Format: incident timeline (resolved) — not git log
  Each role = a closed incident with impact + resolution
════════════════════════════════════════════════════════
-->

## `> pagerduty incidents --filter=resolved --assignee=gulbadin`

```
┌──────────────────────────────────────────────────────────────────┐
│  INCIDENT HISTORY — all resolved                                 │
└──────────────────────────────────────────────────────────────────┘

INC-0006  [RESOLVED]  Oct 2024 – Mar 2025
  title    : Legacy deployment workflows blocking scale
  assignee : Gulbadin Hasan · Lead DevOps Engineer
  org      : 9Yards Technology  [Remote]
  impact   : Deployment bottlenecks · IAM credential risk · low observ.
  actions  : Redesigned to event-driven arch (Lambda·SQS/SNS·EventBridge)
             Implemented OpenTelemetry  →  MTTR ↓ 40%
             Migrated IAM users to role-based access via Terraform
  status   : ✔ RESOLVED  ·  no recurrence

INC-0005  [RESOLVED]  Apr 2023 – Jun 2024
  title    : Infrastructure cost overrun + upgrade risk
  assignee : Gulbadin Hasan · Sr. Cloud Infrastructure Engineer
  org      : Arkose Labs  [Pune]
  impact   : $30K/month overspend · EKS upgrade deferred 6 versions
  actions  : DB + infra optimisation  →  $30K/month recovered
             EKS 1.23 → 1.29 via rolling strategy  →  zero downtime
             AZ-aware routing  →  99.9%+ uptime
  status   : ✔ RESOLVED  ·  cost saving sustained

INC-0004  [RESOLVED]  Dec 2020 – Apr 2023
  title    : Platform reliability + secrets sprawl
  assignee : Gulbadin Hasan · Technical Lead
  org      : Incedo Inc  [Pune]
  impact   : Deployment failures · unmanaged secrets · slow incidents
  actions  : Vault-based secrets management + IAM hardening
             CI/CD pipeline improvement via Jenkins + Terraform
             AWS security audit (Trusted Advisor + Inspector)
  status   : ✔ RESOLVED

INC-0003  [RESOLVED]  May 2019 – Dec 2020
  title    : No cloud infrastructure · PCIDSS non-compliant
  assignee : Gulbadin Hasan · Data Engineer
  org      : Cratas Techno Solution  [Pune]
  impact   : Zero cloud footprint · regulatory exposure
  actions  : Built AWS infra from 0  (VPC·EC2·S3·IAM·networking)
             Achieved PCIDSS compliance  →  0 critical findings
             Terraform + CloudFormation automation
  status   : ✔ RESOLVED

INC-0002  [RESOLVED]  Jul 2016 – May 2019
  title    : Hadoop cluster instability + manual operations
  assignee : Gulbadin Hasan · Senior Systems Engineer
  org      : Astron Systems  [Nagpur]
  impact   : Cluster downtime · manual health checks · auth gaps
  actions  : CDH/HDP clusters on AWS + bare metal
             Kerberos auth + Active Directory integration
             Automated health checks via shell scripting
  status   : ✔ RESOLVED

INC-0001  [RESOLVED]  Jan 2014 – Jul 2016
  title    : Legacy enterprise system degradation
  assignee : Gulbadin Hasan · Senior Systems Engineer
  org      : Cognizant  [Pune]
  impact   : 50+ enterprise apps · SLA risk · Windows 2003 EOL
  actions  : Windows 2003 → 2008 migration
             ITIL-based incident · problem · change management
  status   : ✔ RESOLVED

──────────────────────────────────────────────────────────────────
total incidents assigned    :  6
total incidents resolved    :  6          resolution rate: 100%
open incidents              :  0
──────────────────────────────────────────────────────────────────
```

---

<!--
════════════════════════════════════════════════════════
  SECTION 06 — CERTIFICATIONS
  Format: x509 certificate inspect output
════════════════════════════════════════════════════════
-->

## `> openssl x509 -in certifications/ -text -noout`

```
Certificate 1:
    Subject   : CN=Gulbadin Hasan, O=Amazon Web Services
    Issuer    : Amazon Web Services Certification Authority
    Level     : Professional
    Title     : AWS Solutions Architect — Professional
    Valid     : 2023 – 2026
    Verify    : aws.amazon.com/certification/certified-solutions-architect-professional
    Status    : ✔ VALID

Certificate 2:
    Subject   : CN=Gulbadin Hasan, O=CNCF / Linux Foundation
    Issuer    : Cloud Native Computing Foundation
    Level     : Professional
    Title     : Certified Kubernetes Administrator (CKA)
    Valid     : 2022 – 2025
    Verify    : cncf.io/certification/cka
    Status    : ✔ VALID

Certificate 3:
    Subject   : CN=Gulbadin Hasan, O=HashiCorp
    Issuer    : HashiCorp Certification Authority
    Level     : Associate
    Title     : HashiCorp Certified: Terraform Associate
    Valid     : 2023 – 2025
    Verify    : hashicorp.com/certification/terraform-associate
    Status    : ✔ VALID

Certificate 4:
    Subject   : CN=Gulbadin Hasan, O=Microsoft
    Issuer    : Microsoft Certification Authority
    Level     : Fundamentals
    Title     : Microsoft Azure Fundamentals (AZ-900)
    Valid     : 2022 – ongoing
    Verify    : learn.microsoft.com/certifications/azure-fundamentals
    Status    : ✔ VALID
```

<div align="center">

<a href="https://aws.amazon.com/certification/certified-solutions-architect-professional/"><img src="https://img.shields.io/badge/AWS-Solutions_Architect_Pro-000?style=flat-square&logo=amazonwebservices&logoColor=fff&labelColor=000&color=fff" /></a>
&nbsp;
<a href="https://www.cncf.io/certification/cka/"><img src="https://img.shields.io/badge/CNCF-CKA-000?style=flat-square&logo=kubernetes&logoColor=fff&labelColor=000&color=fff" /></a>
&nbsp;
<a href="https://www.hashicorp.com/certification/terraform-associate"><img src="https://img.shields.io/badge/HashiCorp-Terraform_Associate-000?style=flat-square&logo=terraform&logoColor=fff&labelColor=000&color=fff" /></a>
&nbsp;
<a href="https://learn.microsoft.com/en-us/certifications/azure-fundamentals/"><img src="https://img.shields.io/badge/Microsoft-AZ--900-000?style=flat-square&logo=microsoftazure&logoColor=fff&labelColor=000&color=fff" /></a>

</div>

---

<!--
════════════════════════════════════════════════════════
  SECTION 07 — SKILLS
  Format: kubectl get — plain, no rainbow badges
  Badges: black bg, white logo only — no colour noise
════════════════════════════════════════════════════════
-->

## `> kubectl get skills --all-namespaces -o wide`

```
NAMESPACE       NAME                   STATUS    LEVEL       SINCE
──────────────────────────────────────────────────────────────────
cloud/aws       eks · ecs · ec2        Running   Expert      2019
cloud/aws       lambda · vpc · s3      Running   Expert      2019
cloud/aws       iam · kms · rds        Running   Expert      2019
cloud/aws       security-hub · ssm     Running   Advanced    2020
cloud/aws       cloudfront · emr       Running   Advanced    2020
──────────────────────────────────────────────────────────────────
containers      kubernetes             Running   Expert      2020
containers      docker · helm          Running   Expert      2020
containers      argocd                 Running   Expert      2022
──────────────────────────────────────────────────────────────────
iac             terraform              Running   Expert      2019
iac             github-actions         Running   Expert      2022
iac             jenkins                Running   Expert      2018
iac             cloudformation         Running   Advanced    2019
──────────────────────────────────────────────────────────────────
observability   opentelemetry          Running   Expert      2024
observability   splunk · new-relic     Running   Expert      2022
observability   prometheus · grafana   Running   Advanced    2021
observability   cloudwatch             Running   Expert      2019
──────────────────────────────────────────────────────────────────
security        pcidss · zero-trust    Running   Expert      2019
security        vault · kms · iam      Running   Advanced    2021
──────────────────────────────────────────────────────────────────
ai-llm          langchain · ollama     Running   Proficient  2024
ai-llm          rag · vector-dbs       Running   Proficient  2024
──────────────────────────────────────────────────────────────────
scripting       bash · python · yaml   Running   Expert      2014
```

<div align="center">

![AWS](https://img.shields.io/badge/AWS-000?style=flat-square&logo=amazonwebservices&logoColor=fff)
![Kubernetes](https://img.shields.io/badge/Kubernetes-000?style=flat-square&logo=kubernetes&logoColor=fff)
![Terraform](https://img.shields.io/badge/Terraform-000?style=flat-square&logo=terraform&logoColor=fff)
![ArgoCD](https://img.shields.io/badge/ArgoCD-000?style=flat-square&logo=argo&logoColor=fff)
![Docker](https://img.shields.io/badge/Docker-000?style=flat-square&logo=docker&logoColor=fff)
![Helm](https://img.shields.io/badge/Helm-000?style=flat-square&logo=helm&logoColor=fff)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-000?style=flat-square&logo=githubactions&logoColor=fff)
![Jenkins](https://img.shields.io/badge/Jenkins-000?style=flat-square&logo=jenkins&logoColor=fff)
![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-000?style=flat-square&logo=opentelemetry&logoColor=fff)
![Prometheus](https://img.shields.io/badge/Prometheus-000?style=flat-square&logo=prometheus&logoColor=fff)
![Grafana](https://img.shields.io/badge/Grafana-000?style=flat-square&logo=grafana&logoColor=fff)
![Splunk](https://img.shields.io/badge/Splunk-000?style=flat-square&logo=splunk&logoColor=fff)
![New Relic](https://img.shields.io/badge/New_Relic-000?style=flat-square&logo=newrelic&logoColor=fff)
![Vault](https://img.shields.io/badge/Vault-000?style=flat-square&logo=vault&logoColor=fff)
![Python](https://img.shields.io/badge/Python-000?style=flat-square&logo=python&logoColor=fff)
![Bash](https://img.shields.io/badge/Bash-000?style=flat-square&logo=gnubash&logoColor=fff)
![LangChain](https://img.shields.io/badge/LangChain-000?style=flat-square&logo=langchain&logoColor=fff)

</div>

---

## `> cat github_stats.log`

<div align="center">

<img height="170" src="https://github-readme-stats.vercel.app/api?username=gulbadinhasan&show_icons=true&hide_border=true&bg_color=000000&title_color=ffffff&icon_color=ffffff&text_color=888888&ring_color=ffffff&border_radius=2&include_all_commits=true&count_private=true" />
<img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=gulbadinhasan&layout=compact&hide_border=true&bg_color=000000&title_color=ffffff&text_color=888888&border_radius=2&langs_count=6" />

<br/>

<img width="96%" src="https://github-readme-activity-graph.vercel.app/graph?username=gulbadinhasan&bg_color=000000&color=ffffff&line=555555&point=ffffff&area_color=000000&area=true&hide_border=true&radius=2&custom_title=contribution+activity" />

</div>

---

## `> curl -s https://gulbadin-hasan.dev/contact`

```json
{
  "name"         : "Gulbadin Hasan",
  "role"         : "Lead DevOps Engineer",
  "location"     : "India",
  "email"        : "gulbadinhasan1@gmail.com",
  "linkedin"     : "linkedin.com/in/gulbadin-hasan",
  "portfolio"    : "gulbadin-hasan.dev",
  "open_to"      : ["Lead DevOps", "Principal Engineer", "Platform Eng", "Cloud Arch"],
  "availability" : "Immediate",
  "mode"         : "Remote or Hybrid",
  "response_sla" : "< 24 hours",
  "status"       : 200
}
```

<div align="center">

<a href="mailto:gulbadinhasan1@gmail.com"><img src="https://img.shields.io/badge/send_mail-000?style=for-the-badge&logo=protonmail&logoColor=fff&labelColor=000&color=fff" /></a>
&nbsp;
<a href="https://linkedin.com/in/gulbadin-hasan"><img src="https://img.shields.io/badge/connect-000?style=for-the-badge&logo=linkedin&logoColor=fff&labelColor=000&color=fff" /></a>
&nbsp;
<a href="https://gulbadin-hasan.dev"><img src="https://img.shields.io/badge/portfolio-000?style=for-the-badge&logo=gnubash&logoColor=fff&labelColor=000&color=fff" /></a>

</div>

---

```
> Infrastructure is code.
> Reliability is a feature.
> Security is non-negotiable.
>
> gulbadin@cloud ~ % █
```

<div align="center">
<img src="https://img.shields.io/badge/last_updated-2025-000?style=flat-square&labelColor=000&color=333&logo=github&logoColor=fff" />
</div>
