# Backstage Software Catalog: Understanding Entities

In Backstage, an **entity** is a core concept in the Software Catalog that represents a piece of software or infrastructure within your organization. Entities are defined using **YAML files** and describe things like **services**, **libraries**, **APIs**, **resources**, **users**, and **groups**. These YAML files are typically stored in your Git repository and registered into the catalog.

---

## What is an Entity?

An **entity** is any unit of ownership, infrastructure, or software that's important to your organization and that you want to track in Backstage.

### Entities have:
- A **kind** (like `Component`, `API`, `User`, etc.)
- A **metadata** section (name, description, tags)
- A **spec** section (depends on the kind—e.g., owner, type, lifecycle)

---

## Common Entity Kinds

| Kind       | Description                                                  |
|------------|--------------------------------------------------------------|
| Component  | A software piece like a service, library, or website         |
| API        | Describes an interface provided or consumed by components    |
| User       | Represents a user in your organization                       |
| Group      | Represents a team or department                              |
| Resource   | Represents infrastructure elements (e.g., databases, queues) |
| System     | A collection of components that form a system                |
| Domain     | High-level grouping of systems by business or capability     |

---

## Example: A Service Component Entity

```yaml
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: payment-service
  description: Handles all payment processing
  tags:
    - java
    - payments
spec:
  type: service
  lifecycle: production
  owner: team-payments
  system: billing-system
```

This entity defines a component called `payment-service`, owned by the `team-payments`, tagged as `java`, and part of the `billing-system`.

---

## How Entities Work in Backstage

1. **Defined in YAML**  
   Stored in source control (e.g., GitHub) as `catalog-info.yaml`.

2. **Registered in Catalog**  
   Entities are registered via the Backstage UI or config files.

3. **Managed in UI**  
   Once registered, entities appear in the catalog UI where users can browse, search, and manage them.

4. **Linked Together**  
   Entities reference one another—e.g., services link to APIs, owners, and resources.

---

## Why Entities Matter

Entities allow Backstage to:

- Map your entire software ecosystem
- Show dependencies between services and teams
- Standardize documentation and metadata
- Provide quick access to CI/CD, monitoring, ownership, and more

---


