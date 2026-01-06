# Mini SaaS Platform

A lightweight SaaS platform demonstration using only Markdown, YAML, and GitHub Actions. This repository showcases environment management, feature flags, user management, and automated validation workflows.

## 🏗️ Architecture

```
mini-saas-platform/
├── .github/
│   └── workflows/
│       └── validate-environments.yml
├── config/
│   ├── environments/
│   │   ├── dev.yml
│   │   ├── staging.yml
│   │   └── prod.yml
│   └── feature-flags.yml
├── data/
│   ├── users.yml
│   └── features.yml
├── docs/
│   └── release-notes.md
└── README.md
```

## 📋 Components

### Users (`data/users.yml`)
Manages user accounts across different subscription tiers with role-based access control.

### Features (`data/features.yml`)
Defines platform features with their availability per subscription tier.

### Feature Flags (`config/feature-flags.yml`)
Controls feature rollout across different environments with percentage-based rollouts.

### Environments
- **Development** (`config/environments/dev.yml`) - Latest features, debugging enabled
- **Staging** (`config/environments/staging.yml`) - Pre-production testing
- **Production** (`config/environments/prod.yml`) - Live environment with strict controls

### CI/CD Validation
Automated GitHub Actions workflow that validates:
- YAML syntax across all configuration files
- Environment configuration consistency
- Feature flag integrity
- User data structure validation

## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd mini-saas-platform
   ```

2. **Review configurations**
   - Check environment settings in `config/environments/`
   - Review feature flags in `config/feature-flags.yml`
   - Examine user data in `data/users.yml`

3. **Run local validation** (requires yamllint)
   ```bash
   yamllint config/ data/
   ```

## 🎯 Feature Flag Usage

Feature flags control which features are available in each environment:

- **enabled**: `true/false` - Feature availability
- **rollout_percentage**: 0-100 - Gradual rollout control
- **allowed_tiers**: List of subscription tiers with access

Example:
```yaml
advanced_analytics:
  dev:
    enabled: true
    rollout_percentage: 100
  staging:
    enabled: true
    rollout_percentage: 50
  prod:
    enabled: true
    rollout_percentage: 10
    allowed_tiers: [enterprise]
```

## 📊 Subscription Tiers

- **Free**: Basic features only
- **Pro**: Enhanced features with higher limits
- **Enterprise**: Full feature access with priority support

## 🔄 Release Process

1. Develop and test in **dev** environment
2. Promote to **staging** for UAT
3. Gradual rollout to **production** using feature flags
4. Document changes in `docs/release-notes.md`

## 🧪 CI/CD Pipeline

The GitHub Actions workflow runs on:
- Every push to main branch
- Pull requests
- Manual workflow dispatch

Validates:
- YAML syntax and structure
- Environment configurations
- Feature flag consistency
- User data integrity

## 📝 Release Notes

See [docs/release-notes.md](docs/release-notes.md) for detailed release history and upcoming features.

## 🤝 Contributing

1. Create feature branch
2. Update relevant YAML files
3. Add release notes entry
4. Submit pull request (triggers CI validation)

## 📄 License

MIT License - Feel free to use and modify for your needs.