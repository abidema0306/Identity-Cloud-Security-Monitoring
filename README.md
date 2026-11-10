# Identity & Cloud Security Monitoring
# Threat Hunting | Microsoft Sentinel | KQL | Identity Governance
🎯 # Project Overview

This project explores how Microsoft Sentinel and Kusto Query Language (KQL) can be used to identify, investigate and monitor potentially suspicious identity and cloud infrastructure activities.

The project combines security operations with identity governance principles to provide visibility into how identities interact with cloud resources.
# Core objectives:

* Detect potentially suspicious identity and infrastructure activities.

* Investigate Azure RBAC role assignments and privilege changes.

* Monitor cloud resource operations.

* Explore non-human identity activity.

* Connect security monitoring with ownership and accountability.

# Security Use Cases
| Use Case      |               Data Source  |     Security Objective |
| ------------- |               -------------|     ----------------   |
| Possible Privilege Escalation    | Azure Activity |  Investigate Azure RBAC role assignments
| Suspicious VM Command Execution  | Azure Activity |  Identify potentially suspicious remote command execution
| Sas Token Generation             | Azure Activity |  Monitor delegated storage access
| Network Security Changes         | Azure Activity |  Identify potentially risky NSG modifications
| Public IP Creation               | Azure Activity | Monitor changes to cloud attack surface
| Identity Activity                | Entra ID logs  | Investigate human and non-human identity activity

# 🧪 Investigation 01: Azure RBAC Role Assignments

Objective: Identify Azure RBAC role assignment operations and investigate the initiating identity, target principal and assigned role.

* Data source: AzureActivity
* Operation monitored: MICROSOFT.AUTHORIZATION/ROLEASSIGNMENTS/WRITE

# Investigation fields
| Field         | Description   |
| ------------- | ------------- |
| Caller          | Identity initiating the operation  |
| CallerIpAddress | Source IP address  |
| PrincipalID     | Identity receiving the role |
| RoleDefinitionID | Azure role definition identifier |
| PrincipalType    |  Type of target identity |
| ActivityStatusValue | Operation Status |
| ResourceId          | Resource or scope associated with the operation |


# Investigation questions

* Who initiated the role assignment?

* Which identity received the role?

* What role was being assigned?

* Were the operations successful or unsuccessful?

* Was the activity expected and authorized?

Security consideration: A role assignment does not automatically indicate privilege escalation. The assigned permissions, scope and authorization context must also be evaluated.

# 🧠 Identity-Centric Governance Perspective

Beyond detecting security events, this project explores a governance question:

Can identities and cloud resources be connected to accountable owners?

Areas of exploration include:

* Human identities

* Service principals

* Managed identities

* AI agent identities

* Cloud resources

* Ownership and accountability

The long-term objective is to explore how identity activity and resource ownership information can complement security monitoring.

# 🛠️ Technologies & Tools

* Microsoft Sentinel

* Microsoft Entra ID

* Azure Activity Logs

* Kusto Query Language (KQL)

