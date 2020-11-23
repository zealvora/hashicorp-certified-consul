
#### Pre-Requisite:

We had stored this data via GUI in demo. This is an equivalent command.
```sh
consul kv put name backup1
```
#### Step 1: Take a backup
```sh
consul snapshot save backup.snap
consul kv delete name
```
#### Step 2: Restore From Backup
```sh
consul snapshot restore backup.snap
consul kv get name
```
