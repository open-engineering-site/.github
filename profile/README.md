# Open Engineering Site

<p align="center">
  <img src="../assets/hero-banner.png" alt="Open Engineering Site" width="100%">
</p>

A site is a deployed, addressable place where Open Engineering becomes accessible.

Welcome to Open Engineering Site — the home of the implementation model, tooling, and reference implementations for individual sites in the Open Engineering ecosystem.

Where Open Engineering Sites defines what a site is, Open Engineering Site focuses on how a concrete site is realized.

A site turns composed engineering resources into something people, machines, agents, and other systems can actually visit and use.

⸻

## What is a Site?

A Site is an addressable presentation and interaction surface for Open Engineering resources.

It may expose:

* documentation,
* applications,
* dashboards,
* visualizations,
* APIs,
* learning material,
* catalogs,
* maps,
* interactive experiences,
* operational interfaces,
* or combinations of these.

A site is not necessarily just a traditional website.

It is the boundary at which selected parts of the Open Engineering ecosystem are published, presented, discovered, and interacted with.

For example:
```
Open Engineering resources
        │
        ▼
    Composition
        │
        ▼
      Site
        │
        ▼
https://open-engineering.io/...
```
⸻

## Site vs. Sites

The Open Engineering ecosystem deliberately separates definitions from implementations.

| Organization | Responsibility |  
| —- | —- |  
| open-engineering-sites | Definitions, contracts, schemas, conventions, and lifecycle of sites |  
| open-engineering-site | Implementations and reference realizations of individual sites |  

In short:
```
Sites
  │
  │ defines
  ▼
Site
  │
  │ implements
  ▼
Running site
```
This separation allows many different site implementations to conform to the same shared model.

⸻

## Purpose

This organization exists to answer the practical question:

How do we turn an Open Engineering Site definition into a running, reachable experience?

A site implementation may therefore contain or coordinate:
```
Site Definition
      │
      ▼
   Content
      │
      ├── Documentation
      ├── Visualizations
      ├── Applications
      ├── APIs
      └── Interactive experiences
      │
      ▼
     Build
      │
      ▼
   Deployment
      │
      ▼
    Runtime
      │
      ▼
open-engineering.io
```
⸻

## Repository Model

The primary implementation work belongs in:

`open-engineering-site/source`

A typical implementation can evolve toward a structure such as:
```
source/
├── README.md
├── site.yaml
├── content/
├── components/
├── layouts/
├── assets/
├── public/
├── adapters/
├── integrations/
├── deployment/
├── tests/
└── examples/
```
The exact structure should remain driven by the contracts defined by Open Engineering Sites rather than by a particular frontend framework.

⸻

#- Site Manifest

Every site should eventually be describable declaratively.

For example:
```
apiVersion: open-engineering.io/v1alpha1
kind: Site
metadata:
  name: open-engineering
spec:
  hostname: open-engineering.io
  source:
    type: composition
  capabilities:
    - documentation
    - discovery
    - visualization
    - interaction
  deployment:
    strategy: managed
```
The manifest represents intent.

The site implementation is responsible for turning that intent into a functioning site.

⸻

## Sites are Compositions

A site should not become another system of record containing copies of everything it presents.

Instead, it should compose resources from elsewhere in the ecosystem.
```
Definitions ───────┐
Elements ──────────┤
Picos ─────────────┤
Capsules ──────────┤
Visualizations ────┤
Documentation ─────┤
Applications ──────┤
APIs ──────────────┤
                   ▼
               Composition
                   │
                   ▼
                  Site
                   │
                   ▼
                Visitor
```
This preserves one of the central principles of Open Engineering:

### Composition over duplication.

⸻

## Addressability

Sites give Open Engineering resources stable places in the public namespace.

The canonical domain is:

open-engineering.io

Sites may occupy paths:
```
https://open-engineering.io/
https://open-engineering.io/academy/
https://open-engineering.io/map/
https://open-engineering.io/docs/
```
or, where appropriate, subdomains:

`https://packages.open-engineering.io/`

The URL becomes part of the site’s identity and provides a human- and machine-addressable entry point into the ecosystem.

⸻

## Declarative Delivery

The long-term goal is for a site to be deployable from declarative intent.
```
site.yaml
    │
    ▼
Open Engineering Parser
    │
    ▼
Open Engineering Composer
    │
    ▼
Open Engineering Builder
    │
    ▼
Deployment Resources
    │
    ▼
Runtime Infrastructure
    │
    ▼
Running Site
```
This allows site creation to participate in the same engineering model as the rest of Open Engineering.

A site should increasingly be something that is declared and composed, rather than manually assembled.

⸻

## Relationship to Builders

A Builder can transform the resources required by a Site into deployable artifacts.

For example:
```
Site
 │
 ▼
Builder
 │
 ├── resolve resources
 ├── validate contracts
 ├── generate artifacts
 ├── build frontend
 └── package deployment
 │
 ▼
Deployable Site
```
This keeps the Site concerned with what should exist, while Builders determine how artifacts are produced.

⸻

## Relationship to Parsers

Parsers allow site definitions and their referenced resources to be understood consistently.
```
Site Definition
      │
      ▼
    Parser
      │
      ▼
Normalized Model
      │
      ▼
   Composer
```
A site therefore does not need to understand every source format itself.

⸻

## Relationship to Composers

Sites are natural consumers of composition.

A Composer can resolve a site into the collection of resources needed to present it:
```
Site
 │
 ├── Elements
 ├── Definitions
 ├── Documentation
 ├── Applications
 ├── Visualizations
 ├── Assets
 └── Capabilities
      │
      ▼
   Composer
      │
      ▼
Resolved Site
```
The resulting composition can then be handed to a Builder and deployment pipeline.

⸻

## Relationship to Open Engineering

A Site is one of the places where the architecture becomes tangible.
```
Ontology
   │
   ▼
Definitions
   │
   ▼
Elements
   │
   ▼
Composition
   │
   ▼
Runtime
   │
   ▼
Site
   │
   ▼
People + Agents + Systems
```
This makes Sites an important bridge between the internal engineering graph and its external representation.

⸻

## Machine Readability

Sites should be useful to agents as well as humans.

Where practical, a Site should expose structured representations alongside its visual interface.

For example:
```
Human
  │
  └── HTML / UI
Agent
  │
  ├── JSON
  ├── JSON-LD
  ├── APIs
  └── semantic metadata
Automation
  │
  ├── manifests
  ├── events
  └── machine-readable contracts
```
The website is therefore not the entire Site.

It is one representation of it.

⸻

## Design Principles

Site implementations should follow several principles:

### Declarative
Describe the desired site rather than encoding deployment knowledge everywhere.

### Composable
Reuse resources maintained elsewhere in Open Engineering.

### Addressable
Every meaningful published resource should have a stable identity and location.

### Discoverable
Humans and machines should be able to understand what the site contains.

### Machine-readable
Structured representations should accompany human-facing presentation where useful.

### Portable
A Site definition should not unnecessarily depend on one hosting provider or frontend framework.

### Observable
Builds, deployments, versions, failures, and runtime state should be visible.

### Reproducible
The same definition and inputs should be capable of producing the same site.

### Open by design
Prefer open formats, explicit contracts, and replaceable implementations.

⸻

## A Small Example

Imagine a site definition declaring:
```
kind: Site
metadata:
  name: academy
spec:
  path: /academy
  content:
    - source: open-engineering-academy
  capabilities:
    - documentation
    - learning
    - search
```
The Open Engineering toolchain could resolve this into:
```
Academy definition
       │
       ▼
    Composer
       │
       ▼
Academy resources
       │
       ▼
     Builder
       │
       ▼
Deployment artifact
       │
       ▼
     Runtime
       │
       ▼
open-engineering.io/academy/
```
The important part is that the published Academy remains connected to its source definitions rather than becoming an isolated website.

⸻

#- Direction

The ambition is larger than hosting a collection of web pages.

Open Engineering Sites should make it possible to declare:

“Make this part of the engineering ecosystem available here.”

and allow the platform to determine how to compose, build, deploy, expose, observe, and maintain it.

That gives Open Engineering a consistent path from:
```
Meaning
  ↓
Definition
  ↓
Composition
  ↓
Execution
  ↓
Presentation
  ↓
Interaction
```
⸻

## Status

This organization is under active development.

Initial work should focus on:

1. implementing the Site contracts defined by open-engineering-sites,
2. defining a minimal site.yaml,
3. creating a minimal reference Site,
4. integrating with Open Engineering Parsers, Composers, and Builders,
5. producing a reproducible deployment,
6. exposing the result through open-engineering.io,
7. adding machine-readable discovery and metadata,
8. and documenting the complete Site lifecycle.

⸻

## The Goal

Open Engineering should eventually make publishing an engineering capability as deliberate and reproducible as deploying any other engineered system.

Define it. Compose it. Build it. Deploy it. Visit it.

That is an Open Engineering Site.
