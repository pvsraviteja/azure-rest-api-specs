# Commerce

> see https://aka.ms/autorest

This is the AutoRest configuration file for Commerce.



---
## Getting Started
To build the SDK for Commerce, simply [Install AutoRest](https://aka.ms/autorest/install) and in this folder, run:

> `autorest`

To see additional help and options, run:

> `autorest --help`
---

## Configuration



### Basic Information
These are the global settings for the Commerce API.

``` yaml
openapi-type: arm
tag: package-2015-06-preview
```


### Tag: package-2015-06-preview

These settings apply only when `--tag=package-2015-06-preview` is specified on the command line.

``` yaml $(tag) == 'package-2015-06-preview'
input-file:
- Microsoft.Commerce/preview/2015-06-01-preview/commerce.json
```

---
# Code Generation


## Swagger to SDK

This section describes what SDK should be generated by the automatic system.
This is not used by Autorest itself.

``` yaml $(swagger-to-sdk)
swagger-to-sdk:
  - repo: azure-sdk-for-python
  - repo: azure-sdk-for-java
  - repo: azure-sdk-for-go
  - repo: azure-sdk-for-js
  - repo: azure-sdk-for-node
  - repo: azure-sdk-for-ruby
    after_scripts:
      - bundle install && rake arm:regen_all_profiles['azure_mgmt_commerce']
```


## Python

These settings apply only when `--python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.
Use `--python-mode=update` if you already have a setup.py and just want to update the code itself.

``` yaml $(python)
python-mode: create
python:
  azure-arm: true
  license-header: MICROSOFT_MIT_NO_VERSION
  payload-flattening-threshold: 2
  namespace: azure.mgmt.commerce
  package-name: azure-mgmt-commerce
  clear-output-folder: true
```
``` yaml $(python) && $(python-mode) == 'update'
python:
  no-namespace-folders: true
  output-folder: $(python-sdks-folder)/commerce/azure-mgmt-commerce/azure/mgmt/commerce
```
``` yaml $(python) && $(python-mode) == 'create'
python:
  basic-setup-py: true
  output-folder: $(python-sdks-folder)/commerce/azure-mgmt-commerce
```

## Go

See configuration in [readme.go.md](./readme.go.md)

## Java

These settings apply only when `--java` is specified on the command line.
Please also specify `--azure-libraries-for-java-folder=<path to the root directory of your azure-libraries-for-java clone>`.

``` yaml $(java)
azure-arm: true
fluent: true
namespace: com.microsoft.azure.management.commerce
license-header: MICROSOFT_MIT_NO_CODEGEN
payload-flattening-threshold: 1
output-folder: $(azure-libraries-for-java-folder)/azure-mgmt-commerce
```

### Java multi-api

``` yaml $(java) && $(multiapi)
batch:
  - tag: package-2015-06-preview
```

### Tag: package-2015-06-preview and java

These settings apply only when `--tag=package-2015-06-preview --java` is specified on the command line.
Please also specify `--azure-libraries-for-java=<path to the root directory of your azure-sdk-for-java clone>`.

``` yaml $(tag) == 'package-2015-06-preview' && $(java) && $(multiapi)
java:
  namespace: com.microsoft.azure.management.commerce.v2015_06_01_preview
  output-folder: $(azure-libraries-for-java-folder)/sdk/commerce/mgmt-v2015_06_01_preview
regenerate-manager: true
generate-interface: true
```



## Multi-API/Profile support for AutoRest v3 generators 

AutoRest V3 generators require the use of `--tag=all-api-versions` to select api files.

This block is updated by an automatic script. Edits may be lost!

``` yaml $(tag) == 'all-api-versions' /* autogenerated */
# include the azure profile definitions from the standard location
require: $(this-folder)/../../../profiles/readme.md

# all the input files across all versions
input-file:
  - $(this-folder)/Microsoft.Commerce/preview/2015-06-01-preview/commerce.json

```

If there are files that should not be in the `all-api-versions` set, 
uncomment the  `exclude-file` section below and add the file paths.

``` yaml $(tag) == 'all-api-versions'
#exclude-file: 
#  - $(this-folder)/Microsoft.Example/stable/2010-01-01/somefile.json
```

