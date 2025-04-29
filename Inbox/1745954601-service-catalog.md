---
id: 1745954601-service-catalog
aliases:
  - Service Catalog
tags: []
---

# Service Catalog

This service allows us to define which services and products should be available in an aws account to use. The administrator can define a set of products that the sub accounts should use. This helps us to streamline the deployment process of all accounts to be as standardized as possible, prevents uncontrolled spending for resources, reduces the lack of governance and compliance, reduces complexity of multi account environments.

Imagine we have a Catalog where we build templates of aws services for certain deployments and applications. The users can select those templates and create the resources without configuring all those services.

Another important feature is the portfolio. In here, we can group multiple templates and share these with other aws accounts. With this, we can define role based portfolios of needed templates.

It uses CloudFormation under the hood.
