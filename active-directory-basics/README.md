# Active Directory Basics Lab

## Overview

This lab was completed as part of the TryHackMe Active Directory Basics room. The objective was to gain hands-on experience with Windows Active Directory administration, user management, Group Policy Objects (GPOs), authentication mechanisms, and enterprise directory structures.

---

## Objectives

* Understand the role of Active Directory in enterprise environments.
* Learn how users, computers, groups, and Organizational Units (OUs) are managed.
* Explore Group Policy Objects (GPOs) and their implementation.
* Understand Kerberos and NTLM authentication mechanisms.
* Learn the concepts of Domains, Trees, Forests, and Trust Relationships.

---

## Hands-On Tasks Completed

### User and OU Management

* Created and managed Organizational Units (OUs).
* Added and removed Active Directory users.
* Deleted unnecessary OUs after disabling accidental deletion protection.
* Organized users according to business requirements and departmental structure.

### Delegation of Control

* Delegated password reset permissions to a designated support user.
* Applied the Principle of Least Privilege by granting only required permissions.

### Computer Management

* Created separate OUs for:

  * Workstations
  * Servers
* Moved computer objects from the default **Computers** container into appropriate OUs.

### Group Policy Management

* Explored existing Group Policy Objects (GPOs).
* Created and configured:

  * Restrict Control Panel Access GPO
  * Auto Lock Screen GPO
* Linked GPOs to appropriate Organizational Units.
* Learned how SYSVOL distributes Group Policies throughout the domain.

---

## PowerShell Commands Used

### Reset User Password

```powershell
Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password')
```

### Force Password Change at Next Logon

```powershell
Set-ADUser -ChangePasswordAtLogon $true -Identity sophie
```

### Force Group Policy Update

```powershell
gpupdate /force
```

---

## Authentication Concepts Learned

### Kerberos Authentication

Key components:

* Ticket Granting Ticket (TGT)
* Ticket Granting Service (TGS)
* Key Distribution Center (KDC)
* Secure ticket-based authentication

Workflow:

1. User authenticates with the Domain Controller.
2. KDC issues a TGT.
3. User requests a TGS for a specific service.
4. User presents the TGS to access the service.

### NTLM Authentication

Key concepts:

* Challenge-response authentication
* Legacy Windows authentication protocol
* Domain Controller verification process

Workflow:

1. Client requests authentication.
2. Server sends a challenge.
3. Client generates a response using the NTLM hash.
4. Domain Controller verifies the response.
5. Access is granted or denied.

---

## Active Directory Architecture

### Domain

A single Active Directory environment used to manage users, computers, and resources.

### Tree

A collection of domains that share the same namespace.

Example:

```text
thm.local
├── uk.thm.local
└── us.thm.local
```

### Forest

A collection of one or more domain trees with different namespaces.

Example:

```text
thm.local
mht.local
```

### Trust Relationships

Trust relationships allow users from one domain to access resources located in another domain.

---

## Key Takeaways

* Active Directory serves as the foundation of identity and access management in enterprise environments.
* Organizational Units simplify administration and policy management.
* Group Policies provide centralized configuration and security enforcement.
* Kerberos is the default authentication protocol in modern Windows domains.
* Delegation of Control enables secure privilege distribution without granting full administrative rights.
* Trees, Forests, and Trust Relationships enable scalable enterprise network management.

---

## Skills Practiced

* Active Directory Administration
* Windows Server Management
* User and Computer Management
* Organizational Unit (OU) Management
* Group Policy Management (GPO)
* PowerShell for Active Directory
* Authentication and Authorization Concepts
* Enterprise Identity Management

---

## Lab Completion

Successfully completed the TryHackMe **Active Directory Basics** room and gained practical exposure to Active Directory administration and enterprise identity management concepts.
