# IBN gNMI Project
As part of the Intent Based Networking Class of Autumn 25, this repository outlines the steps and code run to get the gNMI lab running on containerlab going. This lab was part of a group project / presentation which contributed to the final grade of this module. This repository will guide you through how to get the lab setup and how to get a better understanding for the ins and outs of gNMI including its configuration. This lab mainly works with the implementation of gNMIc.

## Getting Started
To run this lab a few prerequisits must be met by the host.

### Prerequisits
1. Docker must be installed: https://docs.docker.com/engine/install/
2. Containerlab must be installed: https://containerlab.dev/install/
3. The SRL Telemetry Lab has to be cloned to your machine: https://github.com/srl-labs/srl-telemetry-lab/
4. gNMIc installed on your host

Once all prerequisits are met the LAB can be spun up by running `sudo containerlab deploy` in the directory holding the file https://github.com/srl-labs/srl-telemetry-lab/blob/main/st.clab.yml.
</br>
Verification of the succesfull deployment:
```sh
docker ps
# CONTAINER ID   IMAGE                                       COMMAND                  CREATED        STATUS        PORTS                                          NAMES
# be916b6a7563   ghcr.io/srl-labs/network-multitool:v0.2.1   "/bin/sh /docker/ent…"   25 hours ago   Up 25 hours   22/tcp, 80/tcp, 443/tcp, 1180/tcp, 11443/tcp   server03
# 7e0ec3e768d2   ghcr.io/nokia/srlinux:24.10.3               "/tini -- fixuid -q …"   25 hours ago   Up 25 hours                                                  spine02
# deab2f37ca0b   ghcr.io/srl-labs/network-multitool:v0.2.1   "/bin/sh /docker/ent…"   25 hours ago   Up 25 hours   22/tcp, 80/tcp, 443/tcp, 1180/tcp, 11443/tcp   server02
# acbb235b9864   ghcr.io/srl-labs/network-multitool:v0.2.1   "/bin/sh /docker/ent…"   25 hours ago   Up 25 hours   22/tcp, 80/tcp, 443/tcp, 1180/tcp, 11443/tcp   server01
# f34c2d934666   grafana/grafana:11.5.2                      "/run.sh"                25 hours ago   Up 25 hours   0.0.0.0:3000->3000/tcp, [::]:3000->3000/tcp    grafana
# 44541b3a8b8c   quay.io/prometheus/prometheus:v3.2.1        "/bin/prometheus --c…"   25 hours ago   Up 25 hours   0.0.0.0:9090->9090/tcp, [::]:9090->9090/tcp    prometheus
# fb4ef9ce9f74   ghcr.io/nokia/srlinux:24.10.3               "/tini -- fixuid -q …"   25 hours ago   Up 25 hours                                                  leaf02
# 80e5e41c517a   ghcr.io/nokia/srlinux:24.10.3               "/tini -- fixuid -q …"   25 hours ago   Up 25 hours                                                  spine01
# b3c05a391694   ghcr.io/nokia/srlinux:24.10.3               "/tini -- fixuid -q …"   25 hours ago   Up 25 hours                                                  leaf03
# 763bc18b225e   ghcr.io/nokia/srlinux:24.10.3               "/tini -- fixuid -q …"   25 hours ago   Up 25 hours                                                  leaf01
```
Once verified proceed with applying the configuration stored in `gnmi-config.yaml` by running `gnmic --config ./gnmi-config.yaml subscribe` on the host. You can verify this by going the hosts IP `ip -c a` and going to port 3000. You should be able to open a Grafan Dashboard that now should be ingesting information properly.

## Request Model and Remote Procedure Calls
In this lab we work with gNMIc implementation of the gNMI protocol. Most if not all commands used in this lab are also interchangeable with the gNMI_CLI cli tool written in go. Further information on the installation can be found here: https://github.com/openconfig/gnmi

### gNMI Encoding
The encoding for gNMI is outlined in the RFC-7951 on JSON Encoding of Data Modeled with YANG. (https://datatracker.ietf.org/doc/html/rfc7951). This RFC defines the Tree and Leaf structure used to model data in json format and how to map this json format to the paths used in the YANG model.

### Get RPC
To retrieve data from a device using the GetRequest method we work with the paths specified by the YANG Model. In the provided example we retrieve the oper-state which can be of value `0`or `1` for all interfaces as shown by the path `"/interface[name=*]/oper-state"` Also as we have learnt in the previous section the econding can be of a multitude of types not only limited to json but also to protobuf etc. The GetRequest using the GET RPC will return a GetResponse. (https://github.com/openconfig/gnmi/blob/master/proto/gnmi/gnmi.proto#L57)
```sh
gnmic get --skip-verify --username admin --password NokiaSrl1! 3 --address leaf01 --path "/interface[name=*]/oper-state" 4 --encoding json_ietf
```
### Set RPC
```sh
```

### Capabilities RPC
```sh
```

### Subscribe RPC
```sh
```

### Error Messages​
```sh
```
