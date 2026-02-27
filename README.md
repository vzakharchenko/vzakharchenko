# Hi, I'm Vasyl 👋

I'm a full-stack developer, security researcher, and the **1st Place Winner of Atlassian Codegeist 2025** who loves digging into internals, simplifying complex systems, and building tools that help developers move faster.

---

## 🏆 Recognition & Speaking

* **🏆 1st Place Winner, Atlassian Codegeist 2025**: Won the top prize with **[Secure Notes for Jira](https://github.com/vzakharchenko/Forge-Secure-Notes-for-Jira)**, an enterprise-grade Zero Trust application. Built a custom Drizzle-based ORM for Forge SQL to handle complex audit logs and strict B2B security requirements. 
  ➡️ **[View winning submission on Devpost](https://devpost.com/software/secure-notes-for-jira-coegvb)**
* **🎤 Speaker, [Atlassian Atlas Camp 2026](https://events.atlassian.com/atlascamp26-amsterdam/speaker/2052067/vasyl-zakharchenko)**: Presented *"Making Forge SQL Observable"*. Shared deep technical insights on handling Out-of-Memory (OOM) and Timeout errors in multi-tenant enterprise environments, analyzing TiDB execution plans, and optimizing complex queries for large-scale customers.
  * 🌍 **[Atlassian Community Event (ACE) Recap](https://ace.atlassian.com/events/details/atlassian-west-midlands-presents-atlas-camp-amsterdam-2026-recap/)**: Invited to present a condensed version of this talk to the global Atlassian community. 
  * ▶️ **[Watch my presentation on YouTube](https://youtu.be/Tw5_Jrrr3N0?t=2297)**
---

## ⚙️ What I do

* Think in terms of architecture and edge cases
* Explore platform internals (like Atlassian Forge)
* Build and optimize developer tools
* Research and report security vulnerabilities in developer platforms

---

## 🌱 Open Source

[![GitHub Stats](https://github-readme-stats.vercel.app/api?username=vzakharchenko\&show_icons=true\&theme=default\&hide=issues\&hide_rank=true)](https://github.com/vzakharchenko)
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=vzakharchenko\&layout=compact\&theme=default\&exclude_repo=smartthings-phevctl,remote-ctrl-gsm)](https://github.com/vzakharchenko)


## 🧩 Architectural Work

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

📰 **More articles on Dev.to:**
➡️ [@vzakharchenko](https://dev.to/vzakharchenko)

---

## 📫 Where to find me

* GitHub: [@vzakharchenko](https://github.com/vzakharchenko)
* Dev.to: [vzakharchenko](https://dev.to/vzakharchenko)

