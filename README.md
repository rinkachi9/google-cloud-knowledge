# Google Cloud Knowledge

A personal knowledge base about Google Cloud: its infrastructure and products, how they fit into architectures, and how to run them securely and reliably. Organized by the product categories Google Cloud uses.

## Table of Contents

- [About](#about)
- [Purpose](#purpose)
- [Scope](#scope)
- [Areas](#areas)
- [Full table of contents](#full-table-of-contents)
- [How to use this repository](#how-to-use-this-repository)
- [Reading the knowledge base](#reading-the-knowledge-base)
- [Repository layout](#repository-layout)
- [Sources and migration](#sources-and-migration)
- [Contributing and working with AI agents](#contributing-and-working-with-ai-agents)
- [Status](#status)

## About

This repository collects what I learn about Google Cloud as a cloud DevOps engineer and cloud architect: networking, security, compute, Kubernetes, data, AI and operations. Each note explains one topic in plain English, with diagrams, a worked example and links to official documentation. The notes are written so that they are still useful when I come back after a year, and so that someone new to the topic can follow them from top to bottom.

This is a personal knowledge base, not a tutorial site or official documentation. Google Cloud changes quickly; every note records what was checked and when, and marks what still has to be verified.

## Purpose

The repository exists to:

- build a durable reference on Google Cloud that I can search, extend and trust,
- force real understanding by explaining every concept precisely, with examples, analogies and diagrams,
- prepare for architecture work and Google Cloud certifications (Professional Cloud Architect, Professional Cloud DevOps Engineer, Professional Cloud Security Engineer),
- keep one consistent standard, so the collection stays coherent as it grows,
- provide a source of truth that both people and AI assistants can work with under the same rules.

## Scope

**In scope**

- Google Cloud concepts, products, mechanisms and the reasoning behind them.
- Architecture patterns, case studies, decision guides and comparisons.
- Commands, configuration and code examples, with tool versions.
- Security, reliability, cost and operations practices on Google Cloud.

**Out of scope**

- Credentials, service account keys, project numbers, billing IDs or other real identifiers.
- Content copied wholesale from documentation, courses or exam material.
- General topics that are not specific to Google Cloud (general Kubernetes, networking or security theory) beyond what a note needs; they belong in separate knowledge bases.

## Areas

The top level follows the [Google Cloud product categories](https://cloud.google.com/products), which is also the division of the original notes. Two areas are not product categories: foundations, which every other area assumes, and case studies, which combine many products. Each area has a `README.md` that lists its notes in reading order and its planned topics.

| Area | What it covers |
| --- | --- |
| [Foundations](foundations/README.md) | Overview of Google Cloud, global infrastructure, resource hierarchy, gcloud CLI. |
| [Compute](compute/README.md) | Compute Engine, Cloud Run, Cloud Run functions, App Engine, Batch. |
| [Containers and Kubernetes](containers-and-kubernetes/README.md) | GKE networking, autoscaling, security, fleets, Policy Controller, Config Sync, Cloud Service Mesh. |
| [Storage and databases](storage-and-databases/README.md) | Cloud Storage, Cloud SQL, Spanner, Bigtable, Firestore and the other storage options. |
| [Networking](networking/README.md) | VPC, firewall, peering, Private Service Connect, VPC Service Controls, load balancing, hybrid connectivity. |
| [Security and identity](security-and-identity/README.md) | IAM, service accounts, Cloud Identity, Security Command Center, Cloud IDS, security best practices. |
| [Data analytics](data-analytics/README.md) | BigQuery, Pub/Sub, Dataflow, Dataproc, Dataplex, Looker. |
| [AI and machine learning](ai-and-machine-learning/README.md) | Vertex AI, AutoML, ML development options, AI infrastructure. |
| [Developer and DevOps tools](developer-and-devops-tools/README.md) | Cloud Build, Artifact Registry, Cloud Deploy, Terraform. |
| [Operations](operations/README.md) | Google Cloud Observability, Cloud Logging, monitoring and SLOs. |
| [Integration and APIs](integration-and-apis/README.md) | Apigee, API Gateway, Pub/Sub, Eventarc, Workflows, Cloud Tasks. |
| [Hybrid and multicloud](hybrid-and-multicloud/README.md) | GKE Enterprise, BigQuery Omni, migration tools. |
| [Management and governance](management-and-governance/README.md) | Resource Manager, Organization Policy, billing, Asset Inventory, quotas, Assured Workloads. |
| [Case studies](case-studies/README.md) | Architecture case studies and reference architectures (planned). |

Where a product fits two areas, it has one home note and the other area links to it. For example, BigQuery lives in data analytics and the storage overview links to it; Apigee lives in integration and APIs and the networking README links to it.

## Full table of contents

[ToC.md](ToC.md) lists every file in the repository as an indented tree, with planned topics shown without links. Use it to see the whole structure at once. Use the area READMEs for the recommended reading order.

## How to use this repository

- To learn a topic, open the area, then read the notes in the order the area `README.md` gives.
- To look something up, start from [ToC.md](ToC.md) or search with `grep -rn "term" --include="*.md" .`.
- To find open gaps and claims still to verify, run `grep -rn "TODO:" --include="*.md" .`.

## Reading the knowledge base

This repository is set up for [Librarian OS](https://japonics.io), a reader for Markdown knowledge repositories. [librarian-os.json](librarian-os.json) names the project and lists the entry points (the area directories). Librarian OS renders the notes with Mermaid diagrams, search, a graph of the relations between notes and practice questions.

```bash
# in the librarian-os directory
npm install
npm run dev -- --repo /absolute/path/to/this/repository
```

The relations come from the sidecar files described in [GUIDELINE.md](GUIDELINE.md#35-sidecar-metadata): every `note.md` has a `note.md.json` next to it. The tools that keep them valid run from Librarian OS: `npm run check`, `npm run scaffold` and `npm run toc`, each with this repository's path as the argument.

## Repository layout

```text
ToC.md                  # full tree of every file
GUIDELINE.md            # rules for structure, note format and style
INSTRUCTIONS.md         # Librarian OS adaptation guide
_sources/               # original exports that notes are migrated from (not committed)
librarian-os.json       # configuration for Librarian OS (project name, entry points, rules)
_assets/<area>/         # images and other files used by notes
<area>/
    README.md           # notes in reading order and planned topics
    README.md.json      # its sidecar
    <topic>.md          # a single note
    <topic>.md.json     # its sidecar: node header, relations and sources
    <subarea>/          # optional group of related notes
```

The full rules for structure and naming are in [GUIDELINE.md](GUIDELINE.md#3-repository-structure-and-naming).

## Sources and migration

The notes were migrated from an export of my earlier Google Cloud notes (a ClickUp document) kept locally in `_sources/` and excluded from version control. The content was restructured into the areas above, translated into the note skeleton, extended with diagrams and examples, and checked for outdated statements: corrections are stated in the notes, and statements that still need verification are marked with `TODO:` lines. Images from the original notes, mostly Google Cloud training slides, are kept in `_assets/` for personal study with credit in their alt text; they should be redrawn as Mermaid or SVG over time.

## Contributing and working with AI agents

All notes follow [GUIDELINE.md](GUIDELINE.md). It applies to people and to AI agents alike. Agent-specific entry points are [AGENTS.md](AGENTS.md) and [CLAUDE.md](CLAUDE.md). Both point to the GUIDELINE and do not repeat its rules.

## Status

All fourteen areas exist. Thirteen areas have notes and case studies has its structure and planned topics; the remaining planned topics are listed in each area README and in [ToC.md](ToC.md). Every note is in `draft` status until it has been checked against the current documentation, which is tracked with `TODO:` lines.
