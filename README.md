# Azure Machine Learning Services

This repository contains example notebooks and notes for using Azure Machine Learning Python SDK which allows you to build, train, deploy and manage machine learning solutions using Azure.

## Pre-requisite

- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- [Azure CLI: ML](https://docs.microsoft.com/en-us/azure/machine-learning/service/reference-azure-machine-learning-cli)

## Getting Started

- Deploy [ARM template](./arm/ml_environment.json)
  - You can run `AZ_SUBSCRIPTION_ID={your-az-subscription-id} AZ_BASE_NAME='{unique-base-name}' ./build_environment.sh` to build the machine learning environment

- Create "Notebook VM" from [AML Studio \[preview\]](https://ml.azure.com/)

## Todos

- AML: security
- Automation: provision AML notebook vm
- Table of contents

---

### PLEASE NOTE FOR THE ENTIRETY OF THIS REPOSITORY AND ALL ASSETS

1. No warranties or guarantees are made or implied.
2. All assets here are provided by me "as is". Use at your own risk. Validate before use.
3. I am not representing my employer with these assets, and my employer assumes no liability whatsoever, and will not provide support, for any use of these assets.
4. Use of the assets in this repo in your Azure environment may or will incur Azure usage and charges. You are completely responsible for monitoring and managing your Azure usage.

---

Unless otherwise noted, all assets here are authored by me. Feel free to examine, learn from, comment, and re-use (subject to the above) as needed and without intellectual property restrictions.

If anything here helps you, attribution and/or a quick note is much appreciated.