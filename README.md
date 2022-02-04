# Ansible collection
Collection of cool ansible plugins

## generate-from-vault
Ansible filter plugin for generating env variables from the HashiCorp vault.
```yaml:
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: "my-service-cm"
  namespace: "default"
  labels:
    name: "my-service"
data:
  "{{ my_service.secret | xmargin_devops.plugins.generate_from_vault('secret') | to_nice_yaml }}"
``` 
This plugin will allow you to link multiple key's between services and use hashicorp vault as a central place for storing all env variables. More details in this article [...]


## list-vault-path
Ansible lookup plugin for generating list of folders from specified HashiCorp vault path. Sometime you need to list folder structure within the vault path. 
``` "{{ lookup('xmargin_devops.plugins.list_from_vault', 'my_secret/path/', mount_point='test', wantlist=True) }}" ```

## get-vault-version 
Ansible filter plugin to generate secret versions based on the source path. If you need to gather versions for all the folders in some vault path and print it as json.
``` "{{ lookup('xmargin_devops.plugins.get_vault_version', 'my_secret/path/', mount_point='test', wantlist=True) }}" ```
