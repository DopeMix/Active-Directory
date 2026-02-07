
**Active Directory**
- is a distributed, hierarchical structure that allows for centralized management of an organization's resources,
  including **_users, computers, groups, network devices, file shares, group policies, devices, and trust_**
- provides **authentication and authorization** functions within a Windows domain environment.
- it is designed to be backward-compatible, and many features are arguably not "secure by default", and it can
  be easily misconfigured, this weakness can be leveraged to move laterally and vertically within a network and
  gain unauthorized access.
- is essentially a sizeable read-only database accessible to all users within the domain, regardless of their
  priviledge level, a **basic AD user account** with no added privileges can enumerate objects within the domain,
  regardless of their privilege level.
- this fact makes it extremely important to properly secure an AD implementation because ANY user account,
  can be used to enumerate the domain and hunt for misconfigurations and flaws thouroughly.

<img width="750" height="600" alt="image" src="https://github.com/user-attachments/assets/7d3b1604-5264-4bc0-83ba-a30f6ca3f2aa" />

**Active Directory Structure**
- A directory service, such as **Active Directory Domain Services (AD DS)** gives an organization ways to store
  directory data and make it available to both standard users and administrators on the same network.
- **AD DS** stores information such as usernames and passwords and manages the rights needed for authorized
  users to access this information.
- **Active Directory flaws and misconfigurations can be often used to obtain a foothold(internal access)**,
  move laterally and vertically within a network, and gain unauthorized access to protected resources such as
  databases, file shares, source code, and more.
- AD is essentially a large database accessible to all users within the domain and a basic AD user account
  with no added privileges can be used to enumerate the majority of objects contained within AD, including
  but not limited to:
<img width="657" height="270" alt="image" src="https://github.com/user-attachments/assets/122572fc-6ac6-4f72-bce8-b5a7397b88d9" />

**Active Directory Terminologies**

1. AD Core Concepts
- Object: Anything in AD—users, computers, printers, OUs, etc.
- Attributes: Characteristics of objects, like a username, computer name, or email. Each has an LDAP name
  (e.g., displayName).
- Schema: Blueprint of AD. Defines which object types exist (user, computer) and what attributes they have.

2. AD Structure
- Domain: A logical group of objects (like a city).
- Forest: Top-level container of domains (like a country).
- Tree: Collection of domains starting from a root domain. Multiple trees can exist in a forest.
- Container vs Leaf:
- Container: Holds other objects (like folders).
- Leaf: End objects that don’t hold other objects (like users or computers).

3. IDs and Security
- GUID (Global Unique Identifier): Unique ID for every object in AD; never changes.
- SID (Security Identifier): Unique ID for accounts/groups, used for authentication and permissions.
- Security Principals: Any AD object that can authenticate (users, computers, service accounts).

4. Names in AD
- Distinguished Name (DN): Full path to an object, e.g., cn=bjones,ou=IT,dc=domain,dc=com.
- Relative Distinguished Name (RDN): The object’s name at its current level, e.g., bjones.
- sAMAccountName: Short login name (max 20 characters).
- userPrincipalName: Login in email-style, e.g., bjones@domain.com.

5. Roles and Replication
- FSMO Roles: Specialized DC responsibilities to prevent conflicts:
- Schema Master, Domain Naming Master, RID Master, PDC Emulator, Infrastructure Master.
- Global Catalog (GC): DC that holds all objects in a forest for search/authentication.
- RODC (Read-Only DC): A DC that can’t make changes; used in remote sites for security.
- Replication: AD keeps objects in sync across DCs automatically.

6. Authentication & Services
- SPN (Service Principal Name): Unique ID for services to authenticate via Kerberos.
- Group Policy Objects (GPOs): Policies applied to users/computers.
- ACLs/ACEs/DACLs/SACLs: Permissions system:
- ACL: List of all permissions.
- ACE: Each permission entry.
- DACL: Who is allowed/denied access.
- SACL: Logs access attempts.

7. DNS / Network-related AD Concepts
- FQDN: Full host name including domain, e.g., DC01.domain.local.
- SYSVOL: Shared folder on DCs storing GPOs and scripts.
- AdminSDHolder / SDProp: Protects privileged accounts (Domain Admins) by applying ACLs automatically.
- dsHeuristics / adminCount: Attributes controlling account protections; adminCount=1 = privileged account.

8. Recovery & Deleted Objects
- Tombstone: Deleted AD object kept temporarily for backup.
- AD Recycle Bin: Modern feature allowing full recovery of deleted objects.

9. AD Database & Files
- NTDS.DIT: Core AD database storing all objects and password hashes.
- sIDHistory: Tracks old SIDs during migrations to retain access.

10. Tools & Protocols
- ADUC: GUI for basic AD management.
- ADSI Edit: Advanced tool for editing all AD attributes.
- MSBROWSE: Old protocol for network browsing; mostly obsolete.
- SMB/CIFS: Modern protocols for file/printer sharing.

11. Practical Takeaways
- AD is hierarchical: Forest → Tree → Domain → OU → Object.
- Objects are unique: Each has a GUID and SID.
- Permissions are complex: ACLs, ACEs, DACLs, SACLs define who can do what.
- Replication keeps AD consistent across all DCs.
- Deleted object handling: Tombstone vs Recycle Bin.
- Tools matter: ADUC for normal management, ADSI Edit for deep changes, PowerShell for automation.

💡 Tip to remember: Think of AD like a city map:
- Forest = country
- Domain = city
- OU = district
- Objects = buildings (users, computers, printers)
- GUID/SID = unique building ID
- ACL = who can enter the building
