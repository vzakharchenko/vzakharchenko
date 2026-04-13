# Hi, I'm Vasyl 👋

I'm a full-stack engineer and security researcher focused on platform architecture, developer tooling, and multi-tenant systems. Speaker and 1st Place Winner of Atlassian Codegeist 2025.
---

## 🏆 Recognition & Speaking

* **🏆 1st Place Winner, Atlassian Codegeist 2025**: Won the top prize with **[Secure Notes for Jira](https://github.com/vzakharchenko/Forge-Secure-Notes-for-Jira)**, an enterprise-grade Zero Trust application. Built a custom Drizzle-based ORM for Forge SQL to handle complex audit logs and strict B2B security requirements. 
  ➡️ **[View winning submission on Devpost](https://devpost.com/software/secure-notes-for-jira-coegvb)**
* **🎤 Speaker, [Atlassian Atlas Camp 2026](https://events.atlassian.com/atlascamp26-amsterdam/speaker/2052067/vasyl-zakharchenko)**: Presented *"Making Forge SQL Observable"*. Shared deep technical insights on handling Out-of-Memory (OOM) and Timeout errors in multi-tenant enterprise environments, analyzing TiDB execution plans, and optimizing complex queries for large-scale customers.
  * 🌍 **[Atlassian Community Event (ACE) Recap](https://ace.atlassian.com/events/details/atlassian-west-midlands-presents-atlas-camp-amsterdam-2026-recap/)**: Invited to present a condensed version of this talk to the global Atlassian community. 
  * ▶️ **[Watch my presentation on YouTube](https://youtu.be/Tw5_Jrrr3N0?t=2297)**
---

## ⚙️ What I do

* Design systems with a focus on trust boundaries and edge cases
* Explore platform internals (e.g., Atlassian Forge)
* Build developer tooling for complex distributed systems
* Research and report security issues in multi-tenant platforms

---

## 🚀 Core Project

### 🔹 forge-sql-orm — Enterprise ORM for Atlassian Forge SQL

[forge-sql-orm](https://github.com/forge-sql-orm/forge-sql-orm) is a Drizzle-based ORM built for reliable, production-grade Atlassian Forge apps.
It addresses a key gap in the Forge ecosystem where no native ORM layer exists.

Designed to handle complex Forge SQL patterns such as:

- caching
- optimistic locking
- query observability and diagnostics
- schema generation and migrations
- safe query construction for multi-tenant environments
- vector search and semantic retrieval patterns for AI-powered Forge apps

The project is actively used in the Forge ecosystem and has become one of the most visible community solutions for teams building serious apps on Forge SQL.

📦 npm: [![npm downloads](https://img.shields.io/npm/dm/forge-sql-orm)](https://www.npmjs.com/package/forge-sql-orm)

➡️ **GitHub:** https://github.com/forge-sql-orm/forge-sql-orm

### 🔹 Keycloak Radius Plugin — Embedded RADIUS Server for SSO

An advanced extension for [Keycloak](https://www.keycloak.org/) that embeds a fully functional **RADIUS server directly into the authentication flow**.

- Enables RADIUS authentication using Keycloak identities (OIDC, LDAP, Kerberos)
- Supports **OTP (TOTP/HOTP)**, **WebAuthn (FIDO2)**, and multi-factor authentication
- Includes **RadSec (RADIUS over TLS)** and RADIUS proxy capabilities
- Designed for **multi-tenant environments** with dynamic attribute mapping
- Integrates with network systems (Mikrotik, Cisco, VPNs, hotspot authentication)

➡️ https://github.com/vzakharchenko/keycloak-radius-plugin

## 🧩 Architectural Work

### 🔹 Forge SQL Observability — Safe Query Profiling Pattern

A practical observability pattern for analyzing SQL performance inside Atlassian Forge apps without breaking platform constraints.

The approach focuses on **deterministic, Forge-safe diagnostics**:

- Aggregating total DB execution time per invocation (`dbExecutionTime`)
- Identifying the **slowest queries** instead of relying on non-deterministic system tables
- Optional **EXPLAIN ANALYZE** re-execution for targeted queries
- Safe fallback strategies when metadata is evicted in long-running functions
- Post-mortem diagnostics for **Timeout** and **Out-of-Memory (OOM)** failures

Key idea:
Instead of relying on unstable `information_schema` windows, the pattern captures and analyzes queries **at the application layer**, making observability predictable even under strict Forge limits.

This approach is implemented in **[forge-sql-orm](https://github.com/forge-sql-orm/forge-sql-orm)** and complements platform-level observability with developer-controlled diagnostics.

📘 **Read the discussion:**
➡️ https://community.developer.atlassian.com/t/practical-sql-observability-for-forge-apps-with-forge-sql-orm/97237
### 🔹 Rovo + Forge SQL — Secure Pattern for Natural-Language Analytics

A practical security pattern for connecting **Rovo** with **Forge SQL** in apps that support natural-language analytics.

The approach treats AI-generated SQL as **untrusted input** and validates it through multiple independent layers before execution:

- **AST pre-check** to allow only a single read-only query against the intended table
- **EXPLAIN plan verification** to ensure the query does not touch unexpected tables
- **Post-execution metadata validation** to confirm returned fields originate only from the allowed table
- **Dynamic context injection** for values like `:currentUserId`, `:projectKey`, and `:issueKey`
- **Dynamic row-level security (RLS)** for per-user access control in multi-tenant apps

This pattern was later packaged into **[forge-sql-orm](https://github.com/forge-sql-orm/forge-sql-orm)** as a reusable “Guard” executor for secure Rovo → SQL integrations.

📘 **Read the discussion:**
➡️ [Rovo + Forge SQL: A Secure Pattern for Natural-Language Analytics in Forge Apps](https://community.developer.atlassian.com/t/rovo-forge-sql-a-secure-pattern-for-natural-language-analytics-in-forge-apps/97028)

### 🔹 Inbound Integration Pattern — Runs on Atlassian Safe Architecture

An architectural approach for integrating external services into Atlassian Forge apps **without breaking the “Runs on Atlassian” model**.

The pattern uses `route.navigate` and **static web triggers** to enable inbound-only communication, ensuring all execution remains inside Atlassian’s trusted environment.
It was **confirmed by Atlassian Staff** as fully aligned with Forge’s design principles.

📘 **Read the discussion:**
➡️ [Integrating External Services in Atlassian Forge](https://community.developer.atlassian.com/t/integrating-external-services-in-atlassian-forge-without-losing-the-runs-on-atlassian-eligibility/96055/8)

🧠 **Implementation demo:**
➡️ [Forge Health Monitor](https://github.com/vzakharchenko/Forge-Health-Monitor)

---

### 🔹 Keycloak API Gateway — Secure Multi-Tenant Access Layer

A gateway layer built on top of **Keycloak** for protecting and serving static or dynamic resources in **multi-tenant** environments.

It provides a **role-based access control layer** for JavaScript bundles, APIs, and files, working across **Express**, **Lambda@Edge**, and **serverless** deployments.
Supports **realm- and tenant-based routing**, **dynamic resource mapping**, and **pluggable storage backends** (`InMemory`, `DynamoDB`, etc.).

📘 **Project:**
➡️ [keycloak-api-gateway](https://github.com/vzakharchenko/keycloak-api-gateway)

🧩 **Examples:**

* [Single-tenant React app](https://github.com/vzakharchenko/keycloak-api-gateway/tree/master/examples/reactJSExample)
* [Multi-tenant React app](https://github.com/vzakharchenko/keycloak-api-gateway/tree/master/examples/multiTenantReactJSExample)

---

## 📝 Featured

📘 **Published on the Atlassian Developer Blog**

* **[Optimizing Forge SQL on a 600K+ Database with TiDB EXPLAIN](https://www.atlassian.com/blog/developer/optimizing-forge-sql-on-a-600k-database-with-tidb-explain)**
  A deep dive into query performance, execution plans, and how to work with large datasets in Forge SQL — based on real experiments and analysis.
* **[How to Prevent Data Loss in Forge SQL: Optimistic Locking in Action](https://www.atlassian.com/blog/developer/reliable-data-storage-using-optimistic-locking-in-forge-sql)**
  How to use optimistic locking in Forge SQL to prevent data loss with concurrent updates.
  
📘 **Community article: Local Semantic Search in Atlassian Forge**

* **[AI Magic in Atlassian Forge: Local Semantic Search with Forge SQL](https://community.developer.atlassian.com/t/ai-magic-in-atlassian-forge-local-semantic-search-with-forge-sql/100163)**
  A practical guide to building semantic search in Atlassian Forge using local embeddings, Forge SQL, and TiDB vector search — with both Custom UI (WebAssembly) and backend resolver-based embedding approaches.

🧩 **Working examples:**
* **[Frontend / client-side embeddings](https://github.com/forge-sql-orm/forge-sql-orm/tree/master/examples/forge-sql-orm-example-ai)**
* **[Backend / resolver-side embeddings](https://github.com/forge-sql-orm/forge-sql-orm/tree/master/examples/forge-sql-orm-example-backend-ai)**

📰 **More articles on Dev.to:**
➡️ [@vzakharchenko](https://dev.to/vzakharchenko)

---

## 📫 Where to find me
* Linkendin: [@vzakharchenko](https://www.linkedin.com/in/vasiliy-zakharchenko-22060134b/)
* GitHub: [@vzakharchenko](https://github.com/vzakharchenko)
* Dev.to: [vzakharchenko](https://dev.to/vzakharchenko)

