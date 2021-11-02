# Overview
The setup-atg-demo.sh script does the following:
- Create the project/namespace
- Creates catalog sources for:
  - IAF/CS
  - Navigator
  - WML Training
  - DP/APIC
- Installs operators for:
  - Elastic Search (needed for Jaeger)
  - Jaeger
  - Navigator
  - APIC
- Installs Navigator/APIC
- Installs Jaeger
- Install Bookshop
- Calls configure-apic-atg.sh:
  - Waits for APIC to be ready
  - Enables the api-manager-lur provider
  - Creates the "atg-org" organization
  - Adds the CS admin user to the org as an administrator
  - Creates the "atg-cat" catalog
  - Invites the "atg-test" user to the org
  - Publishes the bookshop API
  - Creates a CRON job to run the bookshop client that will add 5 traces per minute
  - Outputs settings required to run ATG

# How to use
## Create a ROKS cluster
1) Use automation to create a medium ROKS cluster with ICSP and no CS/IAF.

## Install the ATG demo
### Via 1-click
Using a private 1-click catalog install using this branch (`test-atg`)

### Manually
Clone this repo/branch and run the `setup-atg-demo.sh` script. It defaults to the `cp4i` namespace,
override with `-n <namespace>`. To override the catalog sources use `-a <apic catalog source image>`
and `-d <datapower catalog source image>`.