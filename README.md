# Proscan Compliance Mappings

This repository contains the CWE-to-compliance-framework control mappings used by [Proscan](https://proscan.one) to generate compliance reports.

These mappings are based on publicly documented relationships between CWE (Common Weakness Enumeration) identifiers and the controls defined by each compliance framework. They are derived from official framework documentation, MITRE CWE references, and NIST NVD cross-references.

## Frameworks

| Framework | File | Controls Mapped |
|-----------|------|-----------------|
| OWASP Top 10 (2021) | [owasp-top10-2021.json](mappings/owasp-top10-2021.json) | 10 categories |
| PCI DSS 4.0 | [pci-dss-4.0.json](mappings/pci-dss-4.0.json) | 12 requirements |
| NIST 800-53 Rev 5 | [nist-800-53.json](mappings/nist-800-53.json) | Selected SI/AC/SC controls |
| HIPAA | [hipaa.json](mappings/hipaa.json) | Technical safeguard provisions |
| SOC 2 | [soc2.json](mappings/soc2.json) | Trust Services Criteria |
| ISO 27001:2022 | [iso-27001.json](mappings/iso-27001.json) | Annex A controls |
| GDPR | [gdpr.json](mappings/gdpr.json) | Articles 25 and 32 technical measures |

## How Mappings Work

When Proscan identifies a vulnerability, it assigns a CWE identifier. Each CWE maps to one or more controls across multiple frameworks. For example:

**CWE-89 (SQL Injection)** maps to:
- OWASP A03:2021 — Injection
- PCI DSS 6.2.4 — Software engineering techniques to prevent injection
- NIST 800-53 SI-10 — Information input validation
- HIPAA §164.312(a)(1) — Access control / technical safeguards
- SOC 2 CC6.1 — Logical and physical access controls
- ISO 27001 A.8.28 — Secure coding

These mappings are standard across the security industry. Any auditor can verify them against the published framework documentation.

## File Format

Each JSON file contains an array of control definitions with their associated CWEs:

```json
{
  "framework": "PCI DSS",
  "version": "4.0",
  "controls": [
    {
      "id": "6.2.4",
      "title": "Software engineering techniques prevent common attacks",
      "cwes": ["CWE-89", "CWE-79", "CWE-78", "CWE-22"]
    }
  ]
}
```

## Sources

- [MITRE CWE](https://cwe.mitre.org/)
- [NIST NVD](https://nvd.nist.gov/)
- [OWASP Top 10 CWE Mapping](https://owasp.org/Top10/)
- [PCI DSS v4.0](https://www.pcisecuritystandards.org/)
- [NIST SP 800-53 Rev 5](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)

## License

These mappings are provided under the MIT license. The underlying standards are the property of their respective organizations.
