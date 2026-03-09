# Workflow Templates - Traffic Light Orchestration

This directory contains reusable GitHub Actions workflow templates for the BlackRoad-Cloud organization, following a traffic light orchestration pattern.

## 🚦 Traffic Light Orchestration System

The traffic light system provides clear, intuitive workflow states for CI/CD pipelines:

### 🔴 RedLight - Block on Failure
**Purpose**: Quality gate enforcement  
**Status**: STOP - Critical issues detected  
**Use Case**: Pre-merge validation, security gates, quality checks

**Features**:
- Runs automated tests
- Performs security scanning
- Validates code quality and linting
- Checks code coverage thresholds
- Blocks merging when checks fail
- Notifies team of failures

**When to Use**:
- Pull request validation
- Pre-merge quality gates
- Critical security checks
- Mandatory compliance validation

---

### 🟡 YellowLight - Manual Approval Required
**Purpose**: Controlled deployment with human oversight  
**Status**: CAUTION - Awaiting approval  
**Use Case**: Staging/production deployments, sensitive operations

**Features**:
- Pre-deployment validation checks
- Manual approval gates
- Environment-specific configurations
- Deployment plan generation
- Post-approval execution
- Approval notifications

**When to Use**:
- Production deployments
- Infrastructure changes
- Sensitive operations requiring oversight
- Regulatory compliance scenarios

---

### 🟢 GreenLight - Deploy on Success
**Purpose**: Automated deployment pipeline  
**Status**: GO - All checks passed  
**Use Case**: Continuous deployment, automated releases

**Features**:
- Automated testing
- Build and packaging
- Deployment automation
- Health verification
- Success notifications
- Automatic rollback on failure

**When to Use**:
- Continuous deployment to dev/staging
- Automated releases
- Post-merge deployments
- Release automation

---

## 📋 Using These Templates

### For Organization Members

These templates are available when creating new workflows in any repository within the BlackRoad-Cloud organization:

1. Go to your repository
2. Navigate to **Actions** tab
3. Click **New workflow**
4. Look for the traffic light templates in the organization section:
   - 🔴 RedLight - Block on Failure
   - 🟡 YellowLight - Manual Approval Required
   - 🟢 GreenLight - Deploy on Success
5. Click **Configure** on the desired template
6. Customize for your specific needs
7. Commit the workflow to your repository

### Customization

Each template includes placeholder comments where you should add your specific commands:

```yaml
# Add your test command here (e.g., npm test, pytest, mvn test)
# Add deployment commands (e.g., kubectl apply, terraform apply)
# Add notification logic (e.g., Slack, email)
```

### Required Secrets

Depending on your customization, you may need to configure repository secrets:

- `SLACK_WEBHOOK_URL` - For Slack notifications
- `DEPLOY_TOKEN` - For deployment authentication
- Cloud provider credentials (AWS, GCP, Azure)
- Registry credentials for Docker images

### Environment Configuration

For YellowLight workflows using manual approvals:

1. Go to repository **Settings** → **Environments**
2. Create environments: `staging`, `production`
3. Add required reviewers for each environment
4. Configure environment-specific secrets

---

## 🔄 Workflow Orchestration Patterns

### Sequential Pattern (Traffic Light Progression)

Run workflows in sequence for complete CI/CD:

```
🔴 RedLight (Validate) → 🟡 YellowLight (Approve) → 🟢 GreenLight (Deploy)
```

### Parallel Pattern (Multiple Gates)

Run multiple RedLight checks simultaneously:

```
🔴 Unit Tests
🔴 Integration Tests    → 🟢 GreenLight (Deploy)
🔴 Security Scan
```

### Hybrid Pattern (Selective Approval)

Combine automated and manual gates:

```
🔴 RedLight (Validate) → 🟢 GreenLight (Deploy to Staging) → 🟡 YellowLight (Approve) → 🟢 GreenLight (Deploy to Production)
```

---

## 🛠️ Workflow Template Maintenance

### Updating Templates

To update these organization-wide templates:

1. Make changes to files in this directory
2. Commit and push to the `.github` repository
3. Updates will be available to all organization repositories
4. Existing workflows using these templates won't be automatically updated

### Best Practices

- **Keep templates generic**: Use placeholders for project-specific commands
- **Document well**: Include clear comments in YAML files
- **Version control**: Track template changes with meaningful commit messages
- **Test thoroughly**: Validate template changes in a test repository first
- **Communicate changes**: Notify teams when templates are updated

---

## 📚 Additional Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow Syntax Reference](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- [Using Workflow Templates](https://docs.github.com/en/actions/learn-github-actions/using-workflow-templates)
- [Environment Protection Rules](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment)

---

## 🤝 Contributing

To suggest improvements to these templates:

1. Open an issue in the `.github` repository
2. Describe the proposed change and rationale
3. If accepted, submit a pull request with the changes
4. Changes will be reviewed by the infrastructure team

---

<div align="center">
  <strong>Part of BlackRoad-Cloud Infrastructure</strong><br>
  <sub>Building sovereign, decentralized infrastructure for the future</sub>
</div>
