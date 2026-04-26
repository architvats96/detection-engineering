
# Detection Engineering
[![TOML/MITRE Validation](https://github.com/architvats96/detection-engineering/actions/workflows/toml_mitre_validation.yml/badge.svg)](https://github.com/architvats96/detection-engineering/actions/workflows/toml_mitre_validation.yml)  [![All Detections To Elastic](https://github.com/architvats96/detection-engineering/actions/workflows/all_detections_to_elastic.yml/badge.svg)](https://github.com/architvats96/detection-engineering/actions/workflows/all_detections_to_elastic.yml) [![Metrics](https://github.com/architvats96/detection-engineering/actions/workflows/metrics.yml/badge.svg)](https://github.com/architvats96/detection-engineering/actions/workflows/metrics.yml)

## Overview
This project demonstrates an end-to-end **Detection Engineering Lifecycle**, bridging the gap between manual threat hunting and automated security operations. I created a lab environment to simulate sophisticated attack chains (including custom PowerShell droppers and exfiltration), developed detection rules, and built a **CI/CD pipeline** to validate and deploy these rules to an Elastic Cloud instance via **Elastic Security API**.

## Features
- **Validations**: The detection rules written in TOML are verified with a custom script ensuring proper syntax and MITRE info before they are imported into Elastic.
- **Metrics**: Progress is tracked with the help of CSV and MD reports along with a JSON file which can be directly imported into MITRE Navigator.
- **GitHub Actions**: The validation and metric scripts are bundled in a CI/CD pipeline which runs upon importing any new detections which are then sent to the SIEM via Elastic Security API.
- **Branch Protection Rule**: The main branch is enabled with a protection rule ensuring that code can only be pushed into it from the testing branch after all checks have successfully passed.

## Project Structure
```
├── .github/workflows/      # CI/CD Pipeline definitions

├── detections/             # TOML Detection rules

├── development/            # Lab setup and custom python scripts
	└── validation.py			## Checks that the TOML detections have a proper syntax
	└── mitre.py				## Checks that the TOML detections have the right MITRE info
	└── toml_to_json.py			## Pushes the detections to Elastic instance
	└── toml_to_csv.py			## Creates a CSV report of all detections
	└── toml_to_md.py			## Creates a progress tracker report for all detections
	└── toml_to_report.py		## Creates a MITRE navigation report
	
├── reports/                # Metrics in MD & CSV formats along with MITRE Navigator layers

```
## Architecture Diagram

![workflow](https://github.com/architvats96/detection-engineering/blob/e852718d958b7796d5f06ea447deeaff50a113a7/assets/Architecture%20Diagram.png)

## Impact

This project transitions detection work from a manual, error-prone process to a scalable, version-controlled system. It demonstrates the ability to not only identify threats but to build the infrastructure required to defend an enterprise environment at scale

# License
This project is licensed under the MIT License. See the LICENSE file for details.

# Author
Developed by **Archit Vats**
