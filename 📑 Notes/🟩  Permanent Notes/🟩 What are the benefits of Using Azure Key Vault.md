---
title: What are the benefits of Using Azure Key Vault
type: [[__ 🟩 Permanent Note]]
domain(s):
- [[Azure]]
- [[Azure Key Vault]] 
- [[Cloud Computing]] 
- [[Security and Cloud Computing]] 
- [[Managing API Keys]]
---
# What are the benefits of Using Azure Key Vault

There are four main benefits to using a system like Azure Key Vault: centralizing secret and token storage, securing access to secrets and tokens, controlling access permissions, and logging access.

**Centralized Storage**

Key Vault acts as a central store for all secret and private data within your entire system or architecture. Anything that should be kept secret or hidden should go in there: API keys and tokens, encryption keys, passwords, connection strings, etc.

Centralizing all of these in a single place makes it less likely someone will accidentally expose one of these secrets somewhere in the system. It also makes working with secrets in a secure way a lot easier.

**Secure Access**

Another key benefit of Key Vault is that it lets you secure access to keys and secrets.

So you can set up an access policy so that only certain VMs within your system can access the database connection string. Whitelisting those select VMs means no other service in your system has access to the connection string, which adds an additional layer of security on top only permitting access from those VMs from the database's security policy. 

**Permission Control**

In addition to controlling which services can access certain secrets, you can also set up permissions around who on your team can manage or modify vaults, keys, and secrets.

You could, for instance, set up a policy so that every developer on your team can read a production API key, but only a handful of senior developers can update those keys.

**Access Logging**

Finally, perhaps one of the most important benefits of Key Vault is that it records all access to any key in any vault to a set of logs that you can monitory. Anytime a team member or service accesses and uses a key is recorded, so you can monitor this log for suspicious behavior. 

## Related Notes
- 

## Sources
- [[🟨 Configure and manage secrets in Azure Key vault]]
