# helm app checker

## Check your Helm release versions against the latest available from **Artifact Hub** and **GitHub Releases**.

## Prerequisities
- Go 1.24
- homebrew

## Install via Homebrew

```bash
brew install 7adityaraj/tap/helm-app-checker
brew uninstall helm-app-checker 2>&1; brew untap 7adityaraj/tap 2>&1
```

### config.yaml
```yaml
# helm-app-checker configuration
# Auto-detected from: ./config.yaml, ~/.helm-app-checker.yaml, ~/.config/helm-app-checker/config.yaml

# Kubernetes context to use (empty = use current context)
# kubeContext: ""

# AWS/Kubeconfig paths (empty = use system defaults)
# awsConfig: ~/.aws/config
# kubeConfig: ~/.kube/config

# Release name prefixes to skip (e.g. workload apps)
# ignoreAppPrefixes:
#   - myapp-

# Custom Artifact Hub mappings (only needed for charts not auto-discovered)
# repoMappings:
#   my-chart:
#     org: my-org
#     chart: my-chart

# GitHub release mappings (for charts versioned via GitHub releases)
# githubMappings:
#   ingress-nginx:
#     owner: kubernetes
#     repo: ingress-nginx
#     tagPrefix: "helm-chart-"

# Storage: "local" (default) or "configmap"
# storage:
#   type: local

```

### cmd & output

```
$ helm-app-checker

📂 Loaded config from: /Users/user/Documents/helm-version-checker/config.yaml

🔍 Starting Helm release analysis...
🚀 Pre-flight checks:
ℹ️  Using Kubernetes context: minikube
🌐 Checking internet connectivity... ✅
☸️  Checking Kubernetes connectivity (minikube)... ✅
✅ Pre-flight checks completed
📄 Using cluster-specific local file: /Users/user/Documents/helm-version-checker/reports/helm_report_minikube_2026-03-14.json
📄 Loaded previous report from /Users/user/Documents/helm-version-checker/reports/helm_report_minikube_2026-03-14.json
📋 Fetching Helm releases...
📋 Found 1 deployed releases
🎯 Comparing deployed versions vs latest available
🔍 Processing: keycloak (chart: keycloakx, version: 7.1.4)
   🔍 Searching version sources...
   📍 Found on artifacthub: codecentric/keycloakx

========================================================================================================================
🎯 HELM RELEASE VERSION ANALYSIS
========================================================================================================================

📊 SUMMARY:
   Scan Date: 2026-03-14 11:33:03
   Cluster: minikube
   Context: minikube
   Kubernetes: unknown
   Total Releases: 1
   Up to Date: 0
   Updates Available: 1

Release Name  Namespace  Deployed  Latest  Status        Repository       Source     
─────────────────────────────────────────────────────────────────────────────────────
keycloak      test       7.1.4     7.1.9   🔴 UPDATE      codecentric      artifacthub

🚨 UPDATES NEEDED:
   • keycloak: 7.1.4 → 7.1.9

🎯 Note: Updates are based on deployed version vs latest available
📄 Report stored in local file: /Users/user/Documents/helm-version-checker/reports/helm_report_minikube_2026-03-14.json
📄 JSON report saved to: /Users/user/Documents/helm-version-checker/reports/helm_report_minikube_2026-03-14.json
```