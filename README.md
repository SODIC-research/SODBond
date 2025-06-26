# SODBond

**Semantic-Orchestration Derivation Bond between BPMN and RDF**

---

## Overview

SODBond is a toolkit that bridges Camunda BPMN 2.0 process definitions and runtime instances with RDF knowledge graphs via an ontology-driven approach. It retrieves BPMN models and instance data from Camunda through the REST API and transforms them into semantically rich RDF/OWL representations based on a BPMN-based ontology (e.g., BBO). SODBond supports:

- Integration with Linked Data resources
- Provenance capture (PROV-O)
- SPARQL-based querying of process information

---

## Features

- **Model Extraction**: Fetch BPMN XML and process instance data via Camunda REST API.
- **Ontology-Driven Transformation**: Map BPMN elements (tasks, gateways, events, data objects) to RDF/OWL classes and properties using XSLT/ATL and RDFLib.
- **Provenance & Traceability**: Capture who/what/when workflow details using PROV-O.
- **Linked Data Bonding**: Enrich process entities with external Linked Data vocabularies.
- **Semantic Completeness Evaluation**: Compute recall/precision metrics (target ≥95% alignment).
- **Performance Analysis**: Benchmark SPARQL queries vs. native Camunda API calls (target ≤20% overhead).
- **Case Study Support**: Example workflow for Open Government Dataset publication (metadata validation, license checks, versioning, deployment).
- **Validation & SHACL**: Optional SHACL shapes for graph conformance.
- **Extensibility**: Plugin points for custom mappings, SHACL rules, optimization modules.
- **Toolbox Structure**: Modular architecture (extractor, transformer, linker, validator, benchmarker, SPARQL utilities).

---

## Architecture

```
Camunda BPMN 2.0  --> [ SODBond Extractor ] --> [ Ontology-Driven Transformer ] --> RDF Knowledge Graph --> SPARQL Endpoint --> Client/Analytics
```

---

## Installation

1. **Clone repository**
   ```bash
   git clone https://github.com/SODIC-research/SODBond.git
   cd SODBond
   ```
2. **Set up Python environment**
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```
3. **Configuration**Copy `config_example.yaml` to `config.yaml` and configure:
   - Camunda REST endpoint and credentials
   - Ontology mapping scripts (XSLT/ATL)
   - Namespace prefixes
   - SPARQL endpoint details

---

## Quick Start

```bash
# Extract BPMN definitions
python sodbond/extract.py --process-key <PROCESS_KEY> --output-dir data/

# Transform to RDF
python sodbond/transform.py --bpmn-file data/<PROCESS_KEY>.bpmn --output data/<PROCESS_KEY>.ttl

# Load into store or SPARQL endpoint
python sodbond/load.py --ttl-file data/<PROCESS_KEY>.ttl --store sqlite

# Query with SPARQL
# Use a SPARQL client against the configured endpoint
```

---

## 📖 Citation

```
@misc{SODBond2025,
  title        = {SODBond: Semantic-Orchestration Derivation Bond between BPMN and RDF},
  author       = {Florian Hahn in the SODIC Research Group},
  year         = {2025},
  howpublished = {\url{https://github.com/SOIDC-research/SODBond}},
  note         = {Accessed: June 26, 2025}
}
```

---

## ⚖️ License

Released under the MIT License. See `LICENSE` for details. 


## 👩‍🔬 Maintainer

**Florian Hahn**  
SODIC Research Group, TU Chemnitz  
[Website](https:/tu-chemnitz.de/informatik/dm/team/fh.php) — Contact: `florian.hahn@informatik.tu-chemnitz.de`

