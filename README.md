# contoso payment processing


cardholder -> merchant

WAF - external IDS (can be connected elswhere)

API Gateway either cached via blob or to load balancer via vnet (CERTS)

Load balancer to targets

target:

- Target has tasks which go via function / AKS to a container which is pulled from priv registry

- Target stores transaction in cache and db with relevant security

- Target auths transaction

- Container app runs

- Target completes transation

Output via second vnet to SQL DB (Multi AZ) and monitoring logging / sec complaince

Success / failure returned to merchant

> All components auto size / scale up / down / out

Monitoring 
- log analytics
- Grafana
- health etc

Sec / Compliance
- Sentinel 
- Policy / Blueprints 
- Key vault

Git / Repo 
- builds the infra on one pipe and the app container is published via another
- blob for tfstate
- logs to logging sub
- uses kv for secrets
- enforces dev -> uat -> prod

Container would have to go thru approvals
-  dev, uat, prod etc all via ADO
- Automated unit testing of container app


