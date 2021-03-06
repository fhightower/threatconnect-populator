# ThreatConnect Populator

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/531c2054c4874013b78ff7cebc46a6b2)](https://www.codacy.com/app/fhightower/threatconnect-populator)

This script will create one of every possible object in ThreatConnect for testing or whatever other use you can find for it.

## Prerequisites

This script assumes that the following things are true of the owner in which you are creating the content:

- There are two security labels:
  - `TLP White`
  - `TLP Green`

## Installation

**Disclaimer:** This script was designed only for testing ThreatConnect. Your use of this script acknowledges that you accept any and all risk and unintended consequences of using the script.

In terminal/bash do the following:

```
# clone the repo.
git clone https://github.com/fhightower/threatconnect-populator.git

# move into the repo's directory
cd threatconnect-populator

# setup a tc.conf file
vi ./tc.conf  
# ^ paste your creds and config. settings into the file (see: https://docs.threatconnect.com/en/latest/python/python_sdk.html#configuration)

# install the script
python3 setup.py install --user
```

## Usage

The script expects the path to a tc.conf file (see https://docs.threatconnect.com/en/latest/python/python_sdk.html#configuration for more details on what this file should look like) and the owner into which the data will be created:

```
Usage:
  tc_populate [-c|--cleanup] <path_to_api_conf_file> <owner> 
  tc_populate -h | --help
  tc_populate --version

Options:
  -h, --help     Show this screen.
  --version     Show version.
  -c, --cleanup  Delete items after creation
```

Simple example:

`tc_populate ./tc.conf "Example Community"`

The script works in python 2.x and 3.x .

## Cleanup

If you want to delete all of the test data created when running this script, you can do this by including -c when calling the script as shown below:

`tc_populate -c ./tc.conf "Example Community"`

This will create all of the object and then delete them if everything was created.

Alternatively, if you want to create the objects using this script and delete everything later, you can do this in the UI by finding the `TC Populator Example` tag in the browse screen (e.g. [https://app.threatconnect.com/auth/browse/index.xhtml?filters=&intelType=tags](https://app.threatconnect.com/auth/browse/index.xhtml?filters=&intelType=tags)) and deleting all of the objects associated with it.
