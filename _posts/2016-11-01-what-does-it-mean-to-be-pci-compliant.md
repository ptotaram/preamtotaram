---
layout: post
title: What does it mean to be PCI compliant?
date: 2016-11-01
categories: site standards
---

## What is PCI compliance?
  Adhering to a set of security standards created by the Payment Card Industry for companies that process, store, accept, or transmit payment card information. It is meant to assure this is done in a secure environment.

## What do I need to do to be considered PCI compliant?

### Proper penetration testing
Penetration testing is testing the ability to gain access to the server without access to user names, passwords, and access keys.

#### Penetration Test tools
- nmap
- nessus

### Keep all transmissions over ssl
Lock all transmissions down and use a reputable certificate provider like that from Symantec.

### Regularly monitor access to cardholder data
This can be done with DAM tools, like pimcore.

## What do I need to have to be considered PCI compliant?

### Firewalls

#### Properly Configure IPTables, to manage access to the server

- Add to configuration file management system (mentioned below)

#### ModSecurity

- A Firewall/Security toolkit

### System Vulnerability Management

#### System Hardening

- Change default passwords
- Remove unncessary software and services
- Multiple layer architecture
  + Have each layer on a different server.  This way, if one server gets compromised, the other layers are still protected.

#### Regular software patching

Stay on top of updates, run the updates in a test environment, first to assure there are no negative consequences to updating the system.

#### Configuration file management

Use Ansible, Puppet, or Chef for consistency and testing before hand.  Using these also provide the ability for incremental improvement.

#### Security Monitoring

Nagios and ModSecurity can do this,

## How do I store card data in a PCI compliant manner for recurring charges?
### Use one way hashing to save to the database
- PAN
- CVV
- Expiration Date (Unix Timestamp)

### BCrypt is the hashing algorithm I like to use
BCrypt is a hashing function that incorporates a salt. It can also be adaptive.  Over time, the iteration count can be increased to make it slower. This makes it resistent to brute force.

