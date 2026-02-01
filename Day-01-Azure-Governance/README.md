# Day 01 – Azure Foundations & Governance

## Objective
Implement governance controls for an enterprise Azure environment.

## Scenario
- Separate Production and Development environments
- Prevent accidental deletion
- Enforce region compliance
- Enable cost tracking

## Implementation
- Created Resource Groups (RG-Prod, RG-Dev)
- Applied delete locks on production
- Assigned Azure Policy to restrict region
- Implemented tagging strategy

## Key Learnings
- Resource group location does not restrict resource location
- Locks override RBAC permissions
- Policies enforce compliance before deployment
- Tags are for management, not security

## AZ-104 Skills Covered
- Governance & Compliance
- Resource hierarchy
- Policy vs Lock vs RBAC
