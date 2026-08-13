# Open Engineering Sites

<p align="center">
  <img src="../assets/hero-banner.png" alt="Open Engineering Sites" width="100%">
</p>

Define places on the Web. Compose them from the ecosystem. Publish them as part of the whole.

Open Engineering Sites is the home for website definitions within the Open Engineering ecosystem.

A Site describes a web presence before it becomes a particular deployment.

It defines what a site is, what it contains, which Open Engineering capabilities it exposes, how people and machines can navigate it, and how it relates to the wider ecosystem.

Definition
    ↓
Site
    ↓
Composition
    ↓
Implementation
    ↓
Deployment
    ↓
Web

Sites turn Open Engineering resources into discoverable, navigable and interactive places.

⸻

Why Sites?

Open Engineering is distributed across many independently owned resources:

* definitions
* elements
* capabilities
* APIs
* documentation
* applications
* visualizations
* learning materials
* packages
* stories
* media
* runtime systems

Those resources need places where people — and increasingly agents — can encounter and use them.

A website should therefore not merely be a collection of handcrafted pages.

It should be possible to define, compose, generate, deploy, observe and evolve a site using the same engineering principles applied throughout Open Engineering.

That is the purpose of Open Engineering Sites.

⸻

The Core Idea

A Site is a declarative description of a web presence.

For example:

apiVersion: open-engineering.io/v1alpha1
kind: Site
metadata:
  name: open-engineering
  identifier: open-engineering-site
spec:
  domain: open-engineering.io
  purpose:
    - discover
    - explain
    - navigate
    - interact
  routes:
    - path: /
      role: home
    - path: /academy
      role: learning
    - path: /map
      role: discovery
  capabilities:
    - search
    - navigation
    - visualization
    - documentation
  deployment:
    type: static

The exact specification will evolve.

The important principle is that the definition of the site is separate from its implementation.

⸻

Sites as Compositions

A Site should rarely own everything it presents.

Instead, it composes resources from elsewhere in Open Engineering.

                         ┌────────────────────┐
                         │        Site        │
                         └─────────┬──────────┘
                                   │
                 ┌─────────────────┼─────────────────┐
                 │                 │                 │
                 ▼                 ▼                 ▼
          Documentation       Applications      Visualizations
                 │                 │                 │
                 └─────────────────┼─────────────────┘
                                   │
                 ┌─────────────────┼─────────────────┐
                 │                 │                 │
                 ▼                 ▼                 ▼
             APIs              Media             Academy
                                   │
                                   ▼
                           Open Engineering
                              Ecosystem

The Site becomes a composition boundary between ecosystem resources and their web presentation.

⸻

A Site Is More Than Pages

A useful Site definition can describe several concerns.

Identity

What is this site?

metadata:
  name: Open Engineering

Address

Where does it live?

domain: open-engineering.io

Sites may also define subdomains such as:

docs.open-engineering.io
packages.open-engineering.io
academy.open-engineering.io

Information Architecture

What does the visitor encounter?

/
├── academy/
├── docs/
├── map/
├── packages/
├── projects/
└── about/

Composition

Where does the site’s information originate?

sources:
  - definitions
  - documentation
  - packages
  - visualizations
  - applications

Capabilities

What can visitors do?

capabilities:
  - browse
  - search
  - learn
  - visualize
  - interact

Deployment

How can the Site become operational?

deployment:
  target: web

Observability

How do we know the Site is working?

A Site may define expectations for:

* availability
* performance
* accessibility
* telemetry
* analytics
* errors
* broken links
* deployment health

⸻

Human and Machine Visitors

Open Engineering Sites should be designed for two audiences.

                    Site
                     │
             ┌───────┴───────┐
             │               │
             ▼               ▼
          Humans           Agents
             │               │
             ▼               ▼
           HTML         Structured Data
           UI           APIs
           Media        Metadata
           Search       Semantic Graph
           Docs         Machine Discovery

Humans should receive a coherent web experience.

Agents should be able to discover the same ecosystem through structured, predictable and machine-readable interfaces.

This makes Sites part of the AI-native interface layer of Open Engineering.

⸻

Sites and the Open Engineering Map

A Site should not become another isolated source of truth.

Its definition should participate in the Open Engineering semantic graph.

For example:

Site
 │
 ├── hasDomain ─────────► Domain
 │
 ├── exposes ───────────► Capability
 │
 ├── contains ──────────► Page
 │
 ├── presents ──────────► Documentation
 │
 ├── presents ──────────► Visualization
 │
 ├── launches ──────────► Application
 │
 ├── references ────────► Definition
 │
 └── deployedBy ────────► Runtime

This allows questions such as:

Which sites expose this capability?

Where can this definition be viewed?

Which site presents this application?

Which domain belongs to this Site?

Which deployed Sites depend on this resource?

Sites therefore become nodes in the wider Open Engineering graph rather than standalone web projects.

⸻

Definition vs. Implementation

Open Engineering deliberately separates what something means from one realization of it.

For Sites:

open-engineering-sites
        │
        │ defines
        ▼
      Site
        │
        │ instantiated by
        ▼
 Site Implementation
        │
        │ deployed as
        ▼
   Running Website

This separation makes it possible to change frameworks, hosting platforms and rendering technologies without changing the conceptual definition of a Site.

A Site should not inherently mean:

Svelte
React
Astro
Next.js
Deno
Node.js
Cloudflare
Vercel
GitHub Pages
Kubernetes

Those are implementation or deployment choices.

The Site definition remains above them.

⸻

Example

Imagine the primary Open Engineering web presence:

https://open-engineering.io

Its Site definition could express:

kind: Site
metadata:
  name: Open Engineering
spec:
  domain: open-engineering.io
  audience:
    - engineers
    - learners
    - contributors
    - agents
  sections:
    - ecosystem
    - academy
    - documentation
    - map
    - projects
  capabilities:
    - discovery
    - search
    - learning
    - visualization
  sources:
    - github
    - open-engineering-map
    - open-engineering-academy

A renderer could then turn that definition into an implementation.

A deployment system could publish it.

Observability could verify it.

The Open Engineering Map could index it.

Agents could discover it.

Humans could browse it.

One definition participates in the complete lifecycle.

⸻

Site Lifecycle

Idea
 │
 ▼
Definition
 │
 ▼
Validation
 │
 ▼
Composition
 │
 ▼
Rendering
 │
 ▼
Build
 │
 ▼
Deployment
 │
 ▼
Observation
 │
 ▼
Evolution

Each stage should be independently replaceable and automatable.

⸻

Design Principles

Declarative

Describe the desired Site rather than prescribing every implementation step.

Composable

Sites assemble capabilities and resources already present elsewhere in the ecosystem.

Portable

A Site definition should not unnecessarily depend on a particular framework or hosting provider.

Discoverable

Sites and their contents should participate in Open Engineering metadata and semantic discovery.

Human-Friendly

Machine readability must never come at the expense of a clear, accessible and enjoyable human experience.

Agent-Friendly

Important resources, actions and relationships should also be discoverable programmatically.

Observable

Deployment health, accessibility, performance and usage should be measurable.

Open by Design

Definitions, conventions and implementations should use open formats and remain portable wherever practical.

⸻

Relationship to Other Open Engineering Resources

Sites sit near the outer edge of the ecosystem where engineered resources meet their audiences.

Definitions
     │
Elements
     │
Capabilities
     │
Applications
     │
Documentation
     │
Visualizations
     │
Media
     │
     ▼
   Sites
     │
     ▼
   Web
     │
 ┌───┴───┐
 ▼       ▼
People  Agents

A Site does not replace these resources.

It presents and composes them.

⸻

Repository Direction

The repositories maintained by this organization should focus on reusable Site definitions and specifications, rather than individual website implementations.

A future source repository could evolve toward:

source/
├── README.md
├── schema/
│   └── site.schema.json
├── definitions/
│   ├── open-engineering/
│   │   └── site.yaml
│   ├── academy/
│   │   └── site.yaml
│   └── packages/
│       └── site.yaml
├── examples/
│   ├── minimal/
│   └── composed/
├── docs/
│   ├── concepts/
│   ├── composition/
│   └── lifecycle/
└── tests/

Over time this can become a catalog of reusable, validated Site definitions.

⸻

A Small Example

The smallest useful Site might be:

apiVersion: open-engineering.io/v1alpha1
kind: Site
metadata:
  name: hello-world
spec:
  domain: hello.open-engineering.io
  pages:
    - path: /
      title: Hello World

From that small definition, the ecosystem should eventually be able to:

validate
    ↓
compose
    ↓
render
    ↓
build
    ↓
deploy
    ↓
observe

That is the direction.

⸻

The Bigger Picture

The Web is one of the places where the Open Engineering ecosystem becomes tangible.

A visitor should not need to understand repositories, schemas, runtime architectures or semantic graphs before they can benefit from what has been engineered.

Sites provide that bridge.

Engineering
     ↓
Composition
     ↓
Site
     ↓
Experience

They transform reusable engineering resources into coherent destinations.

For humans.

For machines.

For agents.

For whatever comes next.

⸻

Open Engineering Sites

Define the destination. Compose the experience. Publish the ecosystem.

🌐 Open Engineering — open-engineering.io
