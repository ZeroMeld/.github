# ZeroMeld

**Lightweight Information Management for Heterogeneous Sources**

[![GitHub](https://img.shields.io/badge/GitHub-ZeroMeld-blue?logo=github)](https://github.com/ZeroMeld)
[![License: Private](https://img.shields.io/badge/License-Private-red.svg)]()

> Automating social media content curation, delivery, and management. Integration between Reddit, Slack/Coda/CSV/databases/APIs/etc and custom content delivery systems. Manage heterogeneous information and cases in a single place easily. A lightweight CRM-like system for individuals, small organizations, nonprofits, authors, influencers, and anyone who needs to track and manage data from multiple sources.

---

## What is ZeroMeld?

**ZeroMeld** is a three-layer platform for ingesting, orchestrating, and managing information from diverse sources (Reddit, forums, Usenet/NNTP, news sites, Slack/Discord/IRC, etc.) and routing it to various destinations (Slack, Coda, CSV, APIs, databases, etc.).

**Think**: Salesforce CRM, but lightweight and accessible for small organizations, nonprofits, individuals, authors, influencers, small sellers, and users who want to track data without enterprise complexity.

### Three-Layer Architecture

1. **Sync Layer**: Ingest data from heterogeneous sources (reddit-slack, future connectors)
2. **Orchestration Layer**: Process, filter, route, and manage information flows (being abstracted from Django implementation)
3. **View Layer**: Present, manage, and interact with information (Django admin + ValidateMe security)

---

## System Architecture

```
External Sources                  ZeroMeld Platform                    Destinations
┌──────────────┐                                                      ┌──────────────┐
│ Reddit API   │─┐                                                    │ Slack        │
│ Forums       │ │               ┌─────────────────┐                  │ Webhooks     │
│ Usenet/NNTP  │─┼──────────────>│  Sync Layer     │─────────────────>│ Coda         │
│ News Sites   │ │               │  (reddit-slack) │                  │ CSV/API      │
│ Slack/Discord│ │               └─────────────────┘                  │ Database     │
└──────────────┘─┘                         |                          └──────────────┘
                                           |
                                           v
                           ┌─────────────────────────────────┐
                           │    Orchestration Layer          │
                           │  (being abstracted from Django) │
                           └─────────────────────────────────┘
                                           │
                                           v
                         ┌──────────────────────────────────────┐
                         │         View Layer                   │
                         │  ┌────────────────────────────────┐  │
                         │  │  ValidateMe (Security Gateway) │  │
                         │  │  IP + Auth Access Control      │  │
                         │  └────────────────────────────────┘  │
                         │                 │                    │
                         │                 v                    │
                         │  ┌────────────────────────────────┐  │
                         │  │  Django Backend                │  │
                         │  │  Management & API              │  │
                         │  └────────────────────────────────┘  │
                         └──────────────────────────────────────┘
```

---

## Projects

### reddit-slack

**Content Sync Layer**

**[Repository](https://github.com/djdarcy/reddit-slack)** *(Private - will migrate to ZeroMeld)*

Node.js service that monitors Reddit for new posts and delivers them to configured destinations (Slack, Coda, APIs, etc.) based on intelligent rules.

**Features**:

- Real-time Reddit monitoring
- Configurable source tracking (subreddits, keywords, flair)
- Intelligent content filtering
- Multiple destination support (Slack, Coda, databases, webhooks)
- Customizable delivery rules
- Error handling and retry logic

**Technology**: Node.js, Reddit API, Slack/Coda APIs, JSON configuration

**Role**: Sync Layer - ingests content from Reddit (and eventually other sources)

**Status**: Feature-complete, production-ready, nearly ready for public release

_____

### ZMView-ValidateMe 🔐

**Enterprise-Grade Security Gateway**

**[Repository](https://github.com/ZeroMeld/ZMView-ValidateMe)** *(Private - feature complete)*

IP-based access control and authentication gateway that protects the entire ZeroMeld infrastructure. Blocks all access to web services unless users validate through a privately provided source, then grants IP-based access.

**Key Features**:
- Multi-layer IP whitelisting with dynamic nginx configuration
- Dual authentication (username/password + IP validation)
- Multi-environment support (LIVE, STAGING, TEST, DEV, PRIVATE)
- Internal messaging and admin queue system
- Security analytics and audit trails
- Works with any Nginx server

**Technology**: Python/Django, Nginx, Redis, Celery

**Security Model**: Zero-trust architecture - attackers must know how to access ValidateMe, authenticate, AND pass IP validation before even beginning to probe the Django layer.

**Status**: Feature-complete, production-ready, nearly ready for public release

---

### redditslack-django
**Orchestration and Management Backend**

**[Repository](https://github.com/djdarcy/redditslack-django)** *(Private - will migrate to ZeroMeld)*

Django-based platform providing orchestration, content management, admin interface, and API for the information sync services.

**Features**:
- Web-based administration
- Content scheduling and routing
- User and permission management
- REST API for integration services
- Analytics and reporting
- Multi-environment database management

**Technology**: Django, SQLite/PostgreSQL, Django REST Framework, Authentication

**Role**: Orchestration + View Layer (being separated into distinct components)

---

## Use Cases

### Content Creators & Influencers
- Track mentions across Reddit, forums, social media
- Aggregate fan discussions and feedback
- Monitor industry trends and competitors
- Organize content ideas from multiple sources

### Small Organizations & Nonprofits
- Centralize information from various community channels
- Track donor conversations and engagement
- Monitor relevant news and policy updates
- Manage volunteer coordination across platforms

### Authors & Researchers
- Track discussions about topics/books
- Aggregate research from multiple sources
- Monitor reviews and reader feedback
- Organize reference materials

### Small Sellers & Businesses
- Monitor product mentions and reviews
- Track competitor activity
- Aggregate customer feedback
- Manage support inquiries from multiple channels

### Individual Users
- Personal knowledge management
- Track interests across platforms
- Organize information from diverse sources
- Create custom information workflows

---

## Key Capabilities

### Multi-Source Ingestion
**Current**: Reddit
**Planned**: Forums, Usenet/NNTP, news sites, Slack, Discord, IRC, RSS feeds, email, webhooks

### Intelligent Routing
- Rule-based content filtering
- Keyword and pattern matching
- Custom processing pipelines
- Conditional delivery logic

### Multi-Destination Delivery
**Current**: Slack, Coda, direct database
**Planned**: CSV export, REST APIs, email, webhooks, custom integrations

### Secure Access
- ValidateMe security gateway
- IP-based access control
- Multi-environment isolation
- Comprehensive audit logging

---

## Deployment

### Production Environments

ZeroMeld is deployed in multiple isolated environments. Each environment is independently secured through ValidateMe.

**Access**: Private - contact administrators

---

## Technology Stack

### Sync Layer (reddit-slack)
- Node.js 14+
- Reddit API client
- Slack/Coda SDK
- JSON-based configuration

### Orchestration Layer (abstracting from Django)
- Python 3.8+
- Async task processing
- Rule engine
- API integration layer

### View Layer
- Django 4.2+
- PostgreSQL/SQLite
- Nginx + Gunicorn
- Redis + Celery
- ValidateMe security gateway

---

## Development Status

**Current Status**: Private development, production deployments active

**Project Locations**:
- [ZeroMeld/ZMView-ValidateMe](https://github.com/ZeroMeld/ZMView-ValidateMe) *(Private, feature-complete)*
- [ZeroMeld/reddit-slack](https://github.com/djdarcy/reddit-slack) *(Private, will migrate)*
- [ZeroMeld/redditslack-django](https://github.com/djdarcy/redditslack-django) *(Private, will migrate)*

**Future Plans**:

- Complete migration to ZeroMeld organization
- Abstract orchestration layer from Django
- Public release of ValidateMe (security gateway)
- Open-source selected sync connectors
- Public documentation and community contributions
- Additional source connectors (forums, Usenet, Discord, etc.)
- Additional destination connectors (email, more APIs, etc.)

---

## Vision: Beyond Social Media

ZeroMeld started as Reddit-to-Slack integration but evolved into a broader vision:

**The Problem**: Information and "cases" are scattered across Reddit, forums, Slack, Discord, IRC, email, USENET, news sites, etc. Managing it manually is overwhelming.

**Enterprise Solution**: Salesforce, HubSpot, etc. - powerful but expensive, complex, overkill for individuals and small organizations.

**ZeroMeld Solution**: Lightweight, accessible information management that:

- Ingests from any source
- Routes intelligently to any destination
- Provides secure management interface
- Scales from individual use to small organizations
- Open-source components for community contribution

**Goal**: Make heterogeneous information management accessible to everyone, not just enterprises.

---

## Related Projects

### DazzleProj Ecosystem

ZeroMeld uses tools from [DazzleProj](https://github.com/DazzleProj):

- **[DazzleLib](https://github.com/DazzleLib)**: File operations for content management
- **[DazzleTools](https://github.com/DazzleTools)**: Deployment and maintenance utilities

---

## Contact

- **Organization**: [ZeroMeld on GitHub](https://github.com/ZeroMeld)
- **Repositories**: Private (members only)
- **Questions**: Contact via organization administrators

---

## License

**Current**: Private/Proprietary (repositories not yet public)

**Future**: Licensing to be determined as components become public. ValidateMe approaching public release with appropriate licensing.

---

## Note to Visitors

The ZeroMeld organization hosts private projects for heterogeneous information management and integration. If you're not a member, you won't see repository contents, but they exist and are actively maintained in production environments.

Projects will be migrated to this organization and components will be made public progressively, starting with ValidateMe (security gateway).

---

**Manage heterogeneous information in one place, easily** 📊
