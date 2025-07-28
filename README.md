# Okta User Audit

The components of this repo provide a way to build an audit trail of Cribl's user, teams, roles, permissions, etc. based the the Cribl API 

## How it works
REST Collectors run scheduled collections against CRIBL API endpoints.  The Default collection rate is once per hour.  The frequency set here will have implicatoins on the granularity of user_change events that can be measured (i.e. scheduled once per hour -> a role change happened sometime between hour 1 and hour 2) 

## Configuring

### Cribl Lake Destination
Provision a Cribl Lake Dataset `user_audit` and an associated Cribl Lake Destination `cribl_user_audit` in Stream

### REST Collectors

You must provision Cribl API Credentials, and replace two placeholders in the REST Collector Configurations:
`{{CRIBL CLIENT SECRET}}` 

`{{CRIBL CLIENT ID}}` 

You should also validate the the expression is evaluating the proper workspace and org_id for your environment:
`${C.env.CRIBL_WORKSPACE_NAME}-${C.env.TENANT_ID}`


### Event Breaker

Import the provided event breaker and validate the REST Collectors, which use it, are properly referencing it.  


### Cribl Lake
Provision a Cribl Lake Destination `user_audit`

### Cribl Search
Import the search dashboards

Authors:
Ryan Allen
Daniel Adamic

