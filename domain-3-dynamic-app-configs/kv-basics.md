
#### Store & Retreive Data in KV:
```sh
consul kv put max_memory 512M
consul kv get max_memory
```
#### List all the keys in the store using the recurse:
```sh
consul kv get -recurse
```
#### Updating Existing Values:
```sh
consul kv put max_memory 1024M
consul kv get max_memory
```
#### Deleting Keys:
```sh
consul kv delete max_memory
```
