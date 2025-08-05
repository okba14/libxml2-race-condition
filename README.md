# libxml2 Race Condition Vulnerability (XXE via readlink)

This repository documents a **race condition vulnerability** in `libxml2` (prior to version 2.12.7) that can lead to **information disclosure** through unsafe handling of external XML entities.

---

## 📌 Summary

A race condition exists in libxml2’s `readlink()` handling when resolving `file://` external entities. By rapidly switching a symbolic link’s target between a decoy and a sensitive file during XML parsing, an attacker can trick libxml2-based tools into unintentionally exposing sensitive data.

---

## 🧪 Affected Tools and Libraries

- `xmllint`
- `xsltproc`
- Python’s `lxml` library (which uses libxml2 under the hood)

Tested and confirmed on:

- Debian-based systems (Debian, Kali Linux)
- libxml2 < 2.12.7

---

## 🛡️ Impact

- **Information Disclosure**: Sensitive files may be read via crafted XML + symlink timing.
- **Potential Local Privilege Escalation**: If a privileged process parses untrusted XML, this may lead to privilege abuse.

---

## ⚙️ Technical Details

- Vulnerability Type: Race Condition, XXE (XML External Entity)
- Affected Functionality: `readlink()` usage in external entity resolution
- Attack Vector: Local attacker crafts XML with external entity → links to symlink → rapidly swaps symlink target during parsing.

---

## 📅 Status

- ✅ Vulnerability confirmed and reproducible
- ⏳ CVE ID requested (pending assignment)
- 🔐 Public PoC will be released after CVE is issued

---

## 🧑‍💻 Discoverer

**Guiar Oqba**  
<techokba@gmail.com>

---

## 📂 Notes

This repository will be updated with further technical details, full PoC code, and mitigation suggestions once the CVE process is completed.

---

