# 🟨 Configure and manage secrets in Azure Key vault

**Introduction**

Azure Key Vault is a way to securely store and access data on the cloud. It's perfect for things like cryptographic keys, tokens, and secrets that you might otherwise put in an environment variable.

Azure Key Vault is not suitable for storing user data. Data that your users create should be stored in a database, which will have its own security mechanisms that you can configure and use. Instead, Key Vault is best suited for managing things like API keys, database access permissions, keys used to encrypt data, etc.

## Benefits of using Azure Key Vault:

**Centralized service:** It acts as a centralized service for managing your keys. This makes managing your keys easier for you and your team, but it also reduces the risk of accidental loss of security information, because everything is centralized in a single place. 

**Secure access:** It provides a secure way of accessing keys from within other cloud services, like a virtual machine

**Permission control:** It provides permission a way of controlling permissions around who can access keys and vaults (authentication) and what they can do with those keys (authorization)

**Access logging:** It keeps a log of every access to every key, which you can query and monitor for suspicious behavior.

## Key Concepts

There are three important concepts to working with Azure Key Vault:

### Vaults:

A Vault is a collection of keys and secrets.

For any given project, you're likely to have multiple different kinds of secrets and keys that you want to keep safe. in Key Vault, you can create a separate vault for each group of secrets.

You create and organize your keys into vaults based on how different keys and tokens group together logically as well as how you want to control access to those groups of keys and tokens.

In Azure Key Vault, you control access to keys at the vault level. This means you can give users different permissions to different vaults and therefore different sets of keys and tokens. Every developer could have their own set of keys for local development that they can use for accessing a third party API. Each developer can go into Azure and update their own keys. But only senior developers can modify the API keys for the production or testing environment.

In Azure Key Vault, logging access and use happens separately for each vault. That means you can monitor who is accessing and using different collections of keys separately. You probably wont monitor the vaults you set up for local development, while you'll closely monitor the logs for the production keys. 

Making new vaults is easy through the Azure portal, CLI, or by using the REST API.

### Keys:

Keys are the central actor in Azure Key Vault.

A key is a string of characters that acts like a username and password to encrypt and decrypt information, and get it in and out of Key Vault.

In Azure Key Vault, keys can be a single instance or they can be versioned. Versioned keys will change and update over time, which is a good security practice. Just like you want to change your passwords every few months, you want to change your keys on some regular schedule. You might update an existing key on a periodic basic or the key may expire, as with SSL certificates.

### Secrets:

A secret is anything you want to keep secure and private. Two really common use cases for keys are: API keys (sometimes also called tokens) and database connection information (either a connection string or the username and password).

## Use Cases

There are a couple of common use cases for Azure Key Vault, including:

**Secrets Management:** Every application will have some information that you want to keep secure. This could be API tokens, passwords, certificates or other secrets. 

**Key Management:** You need encryption keys to encrypt your data and Azure Key Vault makes managing those keys a lot easier.

**Certificate Management:** Azure Key Vault is used for creating and managing public and private SSL/TLS certificates that you would use to secure network traffic. These keys expire and need to be renewed every year. Managing them in Key Vault makes it easier and avoids any potential lapse that could expose your user data.

## Managing Access with Key Vault

There are two ways to think about managing access to data stored in Key Vault: the management level and the data level:

**Management Plane:** Securing data at the management level is about who can access, view, update, and create keys and secrets in a vault. 

**Data Plane:** Permission to create or update data within a vault is controlled by a separate access policy that determines the permissions of a given user to read, write, update, or delete a secret or key. 

This separation makes both managing vaults and managing keys and secrets more secure. 

## Restricting Network Access

When working with Azure Key Vault, it's also important to consider what services in your network can access a given vault and how much access those services have. You always want to limit access to the least possible and to the fewest possible services.


---
[[__ 🟨 Literature Note]]

Source: [[🟦 Configure and manage secrets in Azure Key Vault]]
Domain(s):
-  [[Azure]] [[Azure Key Vault]]



