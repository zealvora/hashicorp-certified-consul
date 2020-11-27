
#### List current set of keys
```sh
consul keyring -list
```
#### Generate new encryption key
```sh
consul keygen
```
#### Add new key to the keyring
```sh
consul keyring -install [NEW-CONSUL-KEY]
```
#### Verify if new key is installed
```sh
consul keyring -list
```
#### Promote new key to primary
```sh
consul keyring -use NEW-KEY
```

#### Remove Older key
```sh
consul keyring -remove [OLD-KEY]
```
