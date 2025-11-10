# ZeroMeld/.github

**Organization profile and community health files for ZeroMeld**

[![GitHub](https://img.shields.io/badge/GitHub-ZeroMeld-blue?logo=github)](https://github.com/ZeroMeld)
[![License: Private](https://img.shields.io/badge/License-Private-red.svg)]()

> This repository contains the organization profile, community health files, and metadata for the ZeroMeld organization.

---

## What is This Repository?

This is a special `.github` repository that provides:

1. **Organization Profile** (`profile/README.md`) - Displayed on https://github.com/ZeroMeld
2. **Community Health Files** - Contribution guidelines, funding information
3. **GitHub Actions Workflows** - Automation for organization-level tasks

**Note**: This repository is **not** the ZeroMeld platform itself. It's the meta-repository for organization-level configuration and documentation.

---

## What is ZeroMeld?

**ZeroMeld** is a three-layer platform for ingesting, orchestrating, and managing information from diverse heterogeneous sources (Reddit, forums, Usenet/NNTP, news sites, Slack/Discord/IRC, etc.) and routing it to various destinations (Slack, Coda, CSV, APIs, databases, etc.).

**Think**: Salesforce CRM, but lightweight and accessible for small organizations, nonprofits, individuals, authors, influencers, and small businesses.

**[View the full organization profile →](profile/README.md)**

---

## Repository Structure

```
.github/
├── profile/
│   └── README.md          # Organization profile (displayed on GitHub)
├── .github/
│   ├── FUNDING.yml        # Sponsorship configuration
│   └── workflows/         # Organization-level automation
└── README.md              # This file (meta-info about .github repo)
```

---

## ZeroMeld Projects

The ZeroMeld platform consists of multiple repositories:

### Core Components

**[ZMView-ValidateMe](https://github.com/ZeroMeld/ZMView-ValidateMe)** *(Private)*
- Enterprise-grade security gateway
- IP-based access control
- Zero-trust architecture
- Status: Feature-complete, production-ready

**[reddit-slack](https://github.com/djdarcy/reddit-slack)** *(Private - will migrate)*
- Content sync layer
- Real-time Reddit monitoring
- Multi-destination delivery
- Status: Feature-complete, production-ready

**[redditslack-django](https://github.com/djdarcy/redditslack-django)** *(Private - will migrate)*
- Orchestration and management backend
- Django-based admin interface
- REST API for integrations
- Status: Active development

---

## Three-Layer Architecture

```
External Sources → Sync Layer → Orchestration Layer → View Layer → Destinations
                  (reddit-slack)                    (ValidateMe + Django)
```

1. **Sync Layer**: Ingest data from heterogeneous sources
2. **Orchestration Layer**: Process, filter, route, manage information flows
3. **View Layer**: Present, manage, interact (Django admin + ValidateMe security)

**[Read full architecture documentation →](profile/README.md#system-architecture)**

---

## Purpose of This Repository

### Organization Profile

The `profile/README.md` file is displayed on the ZeroMeld organization page and provides:
- Platform overview and vision
- Architecture explanation
- Project descriptions
- Use cases and capabilities
- Technology stack details
- Development status

### Community Health Files

Files in `.github/` provide organization-wide defaults:
- `FUNDING.yml` - Sponsorship options (GitHub Sponsors, Buy Me a Coffee)
- Contribution guidelines (when added)
- Issue templates (when added)
- Pull request templates (when added)

### Automation

GitHub Actions workflows for:
- Documentation updates
- Repository management
- Organization-level tasks

---

## Development Status

**Current**: Private development, production deployments active

**Future Plans**:
- Complete migration to ZeroMeld organization
- Public release of ValidateMe (security gateway)
- Open-source selected sync connectors
- Public documentation and community contributions

---

## Related Projects

ZeroMeld uses tools from [DazzleProj](https://github.com/DazzleProj):
- **[DazzleLib](https://github.com/DazzleLib)** - File operations for content management
- **[DazzleTools](https://github.com/DazzleTools)** - Deployment and maintenance utilities

---

## Editing This Repository

### Update Organization Profile

Edit `profile/README.md` to change what appears on https://github.com/ZeroMeld

### Update Community Health Files

Edit files in `.github/` to change organization-wide defaults.

### Manage Workflows

Add or modify workflows in `.github/workflows/` for organization automation.

---

## Contact

- **Organization**: [ZeroMeld on GitHub](https://github.com/ZeroMeld)
- **Profile**: [View organization profile](https://github.com/ZeroMeld)
- **Repositories**: Private (members only)
- **Questions**: Contact via organization administrators

---

## License

**Current**: Private/Proprietary (repositories not yet public)

**Future**: Licensing to be determined as components become public.

---

## Note to Visitors

This `.github` repository is public to display the organization profile, but the actual ZeroMeld platform repositories are private. If you're not a member, you won't see repository contents, but they exist and are actively maintained in production environments.

---

**Manage heterogeneous information in one place, easily** 📊
