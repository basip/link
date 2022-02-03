## Upgrading Link instances from v1.2.9 to v1.2.24

### Use new broker

BAS-IP Link application use new broker image, you have to create additional docker volume broker-data.

It can be done with command:
```bash
docker volume create broker-data
```

### Thanks
