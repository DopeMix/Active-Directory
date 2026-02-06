
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

