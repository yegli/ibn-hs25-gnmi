 # IBN gNMI demo commands
In this file you can find the commands that are used for the demo during the presentation of gNMI.

### 1. Get command to show interface description
```sh
gnmic get --skip-verify --username admin --password NokiaSrl1! --address leaf01 --path "/interface[name=ethernet-1/49]/description" --encoding proto --format flat
```

### 2. Set interface description with update
```sh
gnmic set --skip-verify --username admin --password NokiaSrl1! --address leaf01 --update-path "/interface[name=ethernet-1/49]/description" --update-value "to spine01 eth-1/1 with update"
```

### 3. Check interface description with get
```sh
gnmic get --skip-verify --username admin --password NokiaSrl1! --address leaf01 --path "/interface[name=ethernet-1/49]/description" --encoding proto --format flat
```

### 4. Set interface description with replace
```sh
gnmic set --skip-verify --username admin --password NokiaSrl1! --address leaf01 --replace-path "/interface[name=ethernet-1/49]" \
--replace-value '{"name": "ethernet-1/49", "description": "to spine01 eth-1/1 with replace", "subinterface": [{"index": 0}] }'
```

### 5. Check interface description with get
```sh
gnmic get --skip-verify --username admin --password NokiaSrl1! --address leaf01 --path "/interface[name=ethernet-1/49]/description" --encoding proto --format flat
```

### 6. Remove interface description with delete
```sh
gnmic set --skip-verify --username admin --password NokiaSrl1! --address leaf01 --delete "/interface[name=ethernet-1/49]/description"
```

### 7. Check interface description with get
```sh
gnmic get --skip-verify --username admin --password NokiaSrl1! --address leaf01 --path "/interface[name=ethernet-1/49]/description" --encoding proto --format flat
```

### 8. Delete subinterface from network instance default
```sh
gnmic set --skip-verify --address leaf01 --username admin --password NokiaSrl1! --delete "/network-instance[name=default]/interface[name=ethernet-1/49.0]"
```

### 9. Delete subinterface
```sh
gnmic set --skip-verify --address leaf01 --username admin --password NokiaSrl1! --delete "/interface[name=ethernet-1/49]/subinterface[index=0]"
```

### 10. Create interface configuration again
```sh
gnmic set --skip-verify --address leaf01 --username admin --password NokiaSrl1! \
--update-path "/interface[name=ethernet-1/49]/subinterface[index=0]/admin-state" \
--update-value "enable" \
--update-path "/interface[name=ethernet-1/49]/subinterface[index=0]/ip-mtu" \
--update-value "9000" \
--update-path "/interface[name=ethernet-1/49]/subinterface[index=0]/ipv4/admin-state" \
--update-value "enable" \
--update-path "/interface[name=ethernet-1/49]/subinterface[index=0]/ipv4/address[ip-prefix=192.168.11.1/31]" \
--update-value "{}"
```

### 11. Show capabilities
```sh
gnmic capabilities  --address leaf01  --username admin  --password NokiaSrl1! --skip-verify
```