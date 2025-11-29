# Compliance Frameworks

> Machine-readable compliance requirements and control mappings in JSON/YAML format

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![SecureByte](https://img.shields.io/badge/SecureByte-Organization-181717?style=flat&logo=github&logoColor=white)](https://github.com/securebyte-consulting)
[![Status](https://img.shields.io/badge/Status-Planning-yellow.svg)]()

## 🎯 Purpose

This repository provides machine-readable compliance framework data that can be consumed by automation tools, compliance platforms, and security applications. We're building a comprehensive, open-source library of compliance requirements, control mappings, and crosswalks with a focus on South African regulations.

## 📦 What's Included

### Compliance Frameworks (Q3 2026)

```
compliance-frameworks/
├── frameworks/
│   ├── popia/
│   │   ├── framework.json          # POPIA framework metadata
│   │   ├── controls.json           # All POPIA requirements
│   │   ├── conditions.json         # 8 POPIA conditions
│   │   └── mappings/               # Mappings to other frameworks
│   ├── soc2/
│   │   ├── framework.json          # SOC 2 Type II metadata
│   │   ├── trust-criteria.json     # Trust Services Criteria
│   │   ├── common-criteria.json    # CC controls
│   │   └── mappings/
│   ├── iso27001-2022/
│   │   ├── framework.json          # ISO 27001:2022 metadata
│   │   ├── annex-a.json            # All Annex A controls
│   │   ├── categories.json         # Control categories
│   │   └── mappings/
│   ├── cis-controls-v8.1/
│   │   ├── framework.json          # CIS Controls v8.1 metadata
│   │   ├── controls.json           # All 18 CIS Controls
│   │   ├── safeguards.json         # Implementation Groups
│   │   └── mappings/
│   └── nist-csf-2.0/
│       ├── framework.json          # NIST CSF 2.0 metadata
│       ├── functions.json          # 6 core functions
│       ├── categories.json         # Categories and subcategories
│       └── mappings/
├── mappings/
│   ├── popia-to-iso27001.json
│   ├── popia-to-soc2.json
│   ├── popia-to-cis.json
│   ├── popia-to-nist.json
│   ├── iso27001-to-soc2.json
│   ├── iso27001-to-cis.json
│   ├── iso27001-to-nist.json
│   ├── soc2-to-cis.json
│   ├── soc2-to-nist.json
│   └── cis-to-nist.json
├── schemas/
│   ├── framework-schema.json       # JSON schema for frameworks
│   ├── control-schema.json         # JSON schema for controls
│   └── mapping-schema.json         # JSON schema for mappings
└── examples/
    ├── querying-frameworks.md
    ├── building-compliance-tools.md
    └── integration-examples/
```

## ✨ Features

- **Machine-Readable** - JSON/YAML formats for easy parsing
- **Standardized Schema** - Consistent structure across all frameworks
- **Rich Metadata** - Includes descriptions, references, implementation guidance
- **Control Mappings** - Cross-framework relationships and overlaps
- **Mapping Strength** - Categorized as FULL, PARTIAL, or RELATED
- **South African Focus** - POPIA as a first-class framework
- **Regularly Updated** - Maintained to reflect latest framework versions

## 🚧 Current Status

**Status:** Planning Phase  
**Target Release:** Q3 2026  
**License:** Apache 2.0

## 📋 Data Structure Examples

### Framework Metadata
```json
{
  "id": "popia",
  "name": "Protection of Personal Information Act",
  "version": "2021",
  "jurisdiction": "South Africa",
  "type": "PRIVACY",
  "description": "South African data protection and privacy law",
  "authority": "Information Regulator of South Africa",
  "url": "https://popia.co.za",
  "last_updated": "2021-07-01",
  "controls_count": 67,
  "categories": [
    "Accountability",
    "Processing Limitation",
    "Purpose Specification",
    "Further Processing Limitation",
    "Information Quality",
    "Openness",
    "Security Safeguards",
    "Data Subject Participation"
  ]
}
```

### Control Definition
```json
{
  "id": "POPIA-CONDITION-7-19",
  "framework_id": "popia",
  "control_id": "Condition 7, Section 19",
  "title": "Security Safeguards",
  "description": "A responsible party must secure the integrity and confidentiality of personal information in its possession or under its control",
  "category": "Security Safeguards",
  "sub_category": "Technical and Organizational Measures",
  "requirement_text": "Take appropriate, reasonable technical and organisational measures to prevent loss of, damage to or unauthorised destruction of personal information and unlawful access to or processing of personal information",
  "legal_reference": "Section 19(1)",
  "severity": "CRITICAL",
  "automated": true,
  "implementation_guidance": [
    "Implement encryption for data at rest and in transit",
    "Establish access control mechanisms",
    "Deploy intrusion detection systems",
    "Maintain audit logs",
    "Regular security assessments"
  ],
  "evidence_types": [
    "Security policy documentation",
    "Encryption configuration",
    "Access control lists",
    "Security audit reports",
    "Penetration test results"
  ],
  "related_controls": [
    "POPIA-CONDITION-7-20",
    "POPIA-CONDITION-7-21"
  ],
  "tags": [
    "encryption",
    "access-control",
    "security-measures",
    "data-protection"
  ]
}
```

### Control Mapping
```json
{
  "source_framework": "popia",
  "source_control": "POPIA-CONDITION-7-19",
  "target_framework": "iso27001-2022",
  "target_control": "ISO27001-A.8.24",
  "mapping_strength": "FULL",
  "confidence": 0.95,
  "mapping_rationale": "Both controls require encryption of data at rest and in transit with similar technical implementation requirements",
  "shared_requirements": [
    "Data encryption",
    "Access control",
    "Security monitoring",
    "Audit logging"
  ],
  "implementation_notes": "Implementing ISO 27001 A.8.24 satisfies POPIA Condition 7 Section 19 requirements for technical security safeguards",
  "evidence_reusability": "FULL",
  "last_reviewed": "2024-01-15"
}
```

### Mapping Matrix
```json
{
  "name": "POPIA to SOC 2 Mapping Matrix",
  "source_framework": "popia",
  "target_framework": "soc2",
  "generated_date": "2024-01-15",
  "total_mappings": 145,
  "mapping_summary": {
    "FULL": 67,
    "PARTIAL": 58,
    "RELATED": 20
  },
  "mappings": [
    {
      "popia_control": "POPIA-CONDITION-7-19",
      "soc2_controls": ["CC6.1", "CC6.6", "CC6.7"],
      "strength": "FULL",
      "coverage": "100%"
    }
  ]
}
```

## 🎨 Use Cases

### For Compliance Platforms
```javascript
// Load POPIA framework
const popia = require('@securebyte/compliance-frameworks/popia/framework.json');

// Find all critical controls
const criticalControls = popia.controls.filter(c => c.severity === 'CRITICAL');

// Get controls that can be automated
const automatedControls = popia.controls.filter(c => c.automated === true);
```

### For Security Tools
```python
import json

# Load control mappings
with open('mappings/popia-to-iso27001.json') as f:
    mappings = json.load(f)

# Find overlapping controls
full_mappings = [m for m in mappings if m['mapping_strength'] == 'FULL']

# Evidence collected for ISO 27001 can be reused for POPIA
reusable_evidence = [m for m in mappings if m['evidence_reusability'] == 'FULL']
```

### For Audit Preparation
```typescript
// Generate compliance checklist
import { Framework } from '@securebyte/compliance-frameworks';

const soc2 = Framework.load('soc2');
const checklist = soc2.generateChecklist({
  includeEvidence: true,
  groupByCategory: true,
  outputFormat: 'markdown'
});
```

## 🛠️ Planned Tools

### CLI Tool
```bash
# Query framework information
compliance-frameworks info popia

# List all controls in a framework
compliance-frameworks list soc2 --category security

# Find control mappings
compliance-frameworks map popia iso27001

# Validate custom framework files
compliance-frameworks validate ./my-framework.json

# Generate mapping matrix
compliance-frameworks matrix --frameworks popia,soc2,iso27001
```

### NPM Package
```bash
npm install @securebyte/compliance-frameworks
```

```javascript
const { Framework, Mapper } = require('@securebyte/compliance-frameworks');

// Load frameworks
const popia = Framework.load('popia');
const soc2 = Framework.load('soc2');

// Find overlapping controls
const mapper = new Mapper();
const overlaps = mapper.findOverlaps([popia, soc2]);

// Calculate compliance coverage
const coverage = mapper.calculateCoverage(popia, implementedControls);
```

## 🤝 Contributing

We welcome contributions to improve and expand this framework library! Planned contribution areas:

### Add New Frameworks
- HIPAA (Healthcare)
- PCI DSS (Payment Card Industry)
- GDPR (European Privacy)
- FedRAMP (US Government)
- Local regulations from other African countries

### Improve Existing Data
- Enhance control descriptions
- Add implementation guidance
- Refine mapping accuracy
- Include more evidence examples
- Translate to additional languages

### Build Tools & Integrations
- SDKs for various languages (Python, Go, Ruby, etc.)
- Visualization tools for mapping matrices
- Compliance gap analysis tools
- Report generators

**Contribution guidelines will be published with our first release.**

## 📖 Schema Validation

All framework data conforms to our JSON schemas for consistency and validation:

```bash
# Validate framework file
npm run validate:framework frameworks/popia/framework.json

# Validate control definitions
npm run validate:controls frameworks/popia/controls.json

# Validate mappings
npm run validate:mappings mappings/popia-to-iso27001.json
```

## 🎯 Design Principles

1. **Machine-First** - Designed for programmatic consumption
2. **Human-Readable** - Clear, understandable JSON/YAML
3. **Comprehensive** - Complete framework coverage, not just highlights
4. **Accurate** - Verified against official sources
5. **Versioned** - Framework versions tracked and maintained
6. **Extensible** - Easy to add new frameworks and mappings
7. **Open** - Transparent methodology and community-driven

## 📚 Documentation (Coming Q3 2026)

- Framework data structure guide
- Mapping methodology explanation
- Integration examples
- API reference
- Contribution guide
- Framework update process

## 🔗 Related Projects

- **Main Platform:** [securebyte](https://github.com/securebyte-consulting/securebyte) (private)
- **CLI Tool:** [securebyte-cli](https://github.com/securebyte-consulting/securebyte-cli)
- **Documentation:** [securebyte-docs](https://github.com/securebyte-consulting/securebyte-docs)
- **Integrations:** [securebyte-integrations](https://github.com/securebyte-consulting/securebyte-integrations) (planned)

## 📖 About SecureByte

This project is part of the [SecureByte](https://github.com/securebyte-consulting) ecosystem - a compliance automation platform built for South African companies.

**Why We're Open-Sourcing This:**
- Compliance frameworks are public knowledge that should be accessible
- Standardization benefits the entire security community
- Transparency builds trust in compliance tools
- Community contributions improve accuracy and coverage

## 📧 Contact

Questions? Suggestions? Want to contribute?

- **Email:** hello@securebyte.co.za
- **Twitter:** [@securebyte](https://twitter.com/securebyte)
- **LinkedIn:** [SecureByte Consulting](https://linkedin.com/company/securebyte-consulting)

## 📄 License

This repository will be licensed under the [Apache License 2.0](https://opensource.org/licenses/Apache-2.0).

This means you'll be free to:
- Use commercially
- Modify
- Distribute
- Use privately
- Sublicense
- Use patent claims

The only requirements are:
- Include the original copyright and license notice
- State significant changes made
- Include the NOTICE file if provided

## 🌟 Why Apache 2.0?

We chose Apache 2.0 for compliance framework data because:
- **Patent Protection** - Explicit patent grant protects users
- **Commercial Friendly** - Can be used in proprietary products
- **Well Understood** - Widely adopted in the open source community
- **Permissive** - Minimal restrictions on usage
- **Community Standard** - Expected license for data/API projects

---

**Building open compliance infrastructure for everyone** 🔓

*Part of the SecureByte Consulting family of projects*

---

## 🗺️ Roadmap

### Phase 1: Core Frameworks (Q3 2026)
- [ ] POPIA framework and controls
- [ ] SOC 2 Type II Trust Services Criteria
- [ ] ISO 27001:2022 Annex A controls
- [ ] CIS Controls v8.1
- [ ] NIST CSF 2.0
- [ ] Basic cross-framework mappings

### Phase 2: Enhanced Mappings (Q4 2026)
- [ ] Detailed mapping rationale
- [ ] Evidence reusability indicators
- [ ] Implementation guidance
- [ ] Mapping confidence scores
- [ ] Automated mapping validation

### Phase 3: Additional Frameworks (Q1 2027)
- [ ] GDPR (EU Privacy)
- [ ] PCI DSS (Payment Security)
- [ ] HIPAA (Healthcare)
- [ ] Cloud security frameworks (AWS, Azure, GCP)
- [ ] African regional regulations

### Phase 4: Tools & Ecosystem (Q2 2027)
- [ ] NPM/PyPI packages
- [ ] CLI tool for querying
- [ ] Visualization tools
- [ ] API service
- [ ] Community contributions

## 🎁 What This Enables

By open-sourcing compliance framework data, we enable:

- **Compliance Tools** - Build automated compliance platforms
- **Security Products** - Integrate compliance into security tools
- **Audit Preparation** - Generate checklists and gap analyses
- **Education** - Learn compliance requirements in structured format
- **Research** - Analyze control relationships and coverage
- **Standardization** - Common data format for the industry

## 📊 Data Sources

All framework data is compiled from official sources:

- **POPIA** - Information Regulator of South Africa official documentation
- **SOC 2** - AICPA Trust Services Criteria
- **ISO 27001** - ISO/IEC 27001:2022 standard
- **CIS Controls** - Center for Internet Security official publications
- **NIST CSF** - NIST Cybersecurity Framework 2.0 official documentation

Framework data is regularly reviewed and updated to reflect latest versions.

---

**Star this repository** to be notified when we launch! ⭐

**Target Release:** Q3 2026
```