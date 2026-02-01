# Day 02 – Azure AD & RBAC

## Objective
Design identity and access control using Azure AD and RBAC with least privilege.

## Scenario
- App Team: Manage Dev resources only
- Finance Team: Read-only access
- Security Team: Identity management only

## Implementation
- Created Azure AD users and groups
- Assigned RBAC roles at correct scopes
- Assigned Azure AD User Administrator role
- Validated access through login testing

## Access Model
User → Group → Role → Scope

## Key Learnings
- Azure AD roles control identity, not resources
- RBAC roles control Azure resources
- Scope determines access power
- Group-based RBAC is best practice

## AZ-104 Skills Covered
- Azure AD vs RBAC
- Role assignment & scope
- Least privilege access
