# iam-resources

A curated collection of IAM reference material — runbook templates, governance frameworks, protocol references, and operational guides built from real enterprise identity engineering experience.

Useful for IAM analysts, IGA engineers, and identity architects.

---

## 📁 Contents

```
iam-resources/
│
├── runbooks/
│   ├── joiner-process-runbook.md          # New hire provisioning steps
│   ├── mover-process-runbook.md           # Role change / transfer process
│   ├── leaver-process-runbook.md          # Offboarding and deprovisioning
│   ├── access-certification-runbook.md    # Running an access review campaign
│   └── incident-response-runbook.md       # IAM incident triage and resolution
│
├── governance/
│   ├── rbac-design-principles.md          # Role-based access control best practices
│   ├── least-privilege-framework.md       # Least privilege implementation guide
│   ├── segregation-of-duties.md           # SoD conflict matrix and controls
│   └── access-request-policy-template.md  # Access request policy template
│
├── protocols/
│   ├── saml-reference.md                  # SAML 2.0 quick reference
│   ├── oidc-reference.md                  # OIDC / OAuth 2.0 quick reference
│   ├── scim-reference.md                  # SCIM 2.0 quick reference
│   └── ldap-query-reference.md            # Common LDAP queries for AD operations
│
├── sailpoint-idn/
│   ├── idn-admin-checklist.md             # Day-to-day admin task checklist
│   ├── connector-troubleshooting.md       # Common connector issues and fixes
│   ├── aggregation-guide.md               # Source aggregation best practices
│   └── certification-campaign-guide.md    # Campaign setup and management guide
│
└── links.md                               # Curated external resources and docs
```

---

## 📋 JML Process — Quick Reference

### Joiner
```
1. HR system triggers new hire event
2. Identity created in IDN from authoritative source
3. Role assignment based on department / job code
4. Accounts provisioned to connected applications
5. Welcome email with access details sent
6. Manager notified for additional access requests
```

### Mover
```
1. HR system triggers transfer / role change event
2. IDN detects attribute change on next aggregation
3. Old role entitlements removed (if applicable)
4. New role entitlements provisioned
5. Access certification triggered for changed entitlements
```

### Leaver
```
1. HR system triggers termination event
2. IDN disables identity immediately
3. All application accounts suspended within SLA
4. Privileged access (CyberArk) revoked first
5. 30-day hold before hard delete (configurable)
6. Manager access review triggered for shared accounts
```

---

## 🔐 RBAC Design Principles

- **Least Privilege** — grant minimum access required for the job function
- **Role Explosion Prevention** — consolidate roles; aim for business roles, not technical roles
- **Naming Convention** — `Department-Function-AccessLevel` e.g. `Finance-AP-ReadOnly`
- **Regular Certification** — review role membership quarterly at minimum
- **Separation of Duties** — no single identity should have conflicting entitlements

---

## 🛠️ Common SailPoint IDN Connector Issues

| Issue | Likely Cause | Fix |
|---|---|---|
| Aggregation fails | Connectivity / credential expiry | Check source health, rotate credentials |
| Accounts not provisioning | Rule/policy blocking creation | Review provisioning policies and transforms |
| Entitlements not syncing | Aggregation schedule issue | Trigger manual entitlement aggregation |
| Correlation failure | Correlation config mismatch | Review correlation rules and identity attributes |
| Source shows degraded | Timeout / firewall | Check network path and connector logs |

---

## 🔗 Useful Links

| Resource | URL |
|---|---|
| SailPoint Developer Portal | https://developer.sailpoint.com |
| SailPoint IDN Documentation | https://documentation.sailpoint.com |
| SCIM 2.0 RFC 7644 | https://datatracker.ietf.org/doc/html/rfc7644 |
| OpenID Connect Specs | https://openid.net/connect/ |
| SAML 2.0 Overview | http://docs.oasis-open.org/security/saml/ |
| Microsoft Entra ID Docs | https://learn.microsoft.com/en-us/entra/identity/ |
| NIST Identity Guidelines | https://pages.nist.gov/800-63-3/ |

---

*All templates are generic starting points. Adapt to your organization's specific policies, platforms, and compliance requirements.*
