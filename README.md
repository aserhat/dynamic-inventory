# dynamic-inventory
A take on Ansible Dynamic Inventory.  Pulls information from an IAAS for host information and reads in yamls from specific folders for common variables, environment specific variables and site specific variables.   Using the yamls stored in a git repository allows for versioning changes in files.

```
export ANSIBLE_VAULT_PASSWORD_FILE=/path/to/vault/password/file (eg $CLONE_DIR/mock/vault/vault-pass-d)
export CLUSTER_NAME=cluster-name (eg lab-d1)
./dynamic/inventory
```

Sample Output
```
{
    "_meta": {
        "hostvars": {
            "master1": {
                "ansible_python_interprete": "/usr/bin/python3"
            }, 
            "node1": {
                "ansible_python_interprete": "/usr/bin/python3"
            }, 
            "node2": {
                "ansible_python_interprete": "/usr/bin/python3"
            }, 
            "node3": {
                "ansible_python_interprete": "/usr/bin/python3"
            }, 
            "registry1": {
                "ansible_python_interprete": "/usr/bin/python3"
            }
        }
    }, 
    "all": {
        "vars": {
            "common": "only in common", 
            "development_variable": "i am a developer", 
            "development_variable_vaulted": "i am an vaulted developer", 
            "hello": "world-site", 
            "site": "only in d1 site", 
            "site_vaulted": "only in vaulted d1 site"
        }
    }, 
    "ingress": {
        "hosts": []
    }, 
    "kubecluster": {
        "children": [
            "masters", 
            "nodes"
        ]
    }, 
    "masters": {
        "hosts": [
            "master1"
        ]
    }, 
    "nodes": {
        "hosts": [
            "node1", 
            "node3", 
            "node2"
        ]
    }, 
    "registry": {
        "hosts": [
            "registry1"
        ]
    }
}
```
