# libxml2-race-condition
Race condition in libxml2 readlink() handling of external entities

# libxml2 Race Condition Vulnerability (XXE via readlink)

This repository documents a race condition vulnerability discovered in libxml2 prior to version 2.12.7.

## Summary

libxml2's handling of external XML entities via `file://` URLs is vulnerable to a race condition involving symlinks. An attacker can switch the target of a symlink between a decoy and a sensitive file during XML parsing, leading to unintended disclosure of sensitive data.

## Impacted Tools

- xmllint
- xsltproc
- Python-lxml

## Impact

- Information Disclosure
- Potential Local Privilege Escalation (depending on usage context)

## Status

- Vulnerability confirmed and tested on Debian/Kali Linux
- Awaiting CVE assignment

> A public PoC will be published here upon CVE assignment.

## Discoverer

Guiar Oqba (@techokba)


