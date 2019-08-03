# dynamic-inventory
A take on Ansible Dynamic Inventory.  Pulls information from an IAAS for host information and reads in yamls from specific folders for global variables, environment specific variables and site specific variables.

```
export ANSIBLE_VAULT_PASSWORD_FILE=/path/to/vault/password/file
export CLUSTER_NAME=cluster-name (eg lab-d1)
```
