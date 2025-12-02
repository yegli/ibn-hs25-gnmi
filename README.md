# IBN gNMI Project

## How to get started with this LAB
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
Once verified let us proceed with the gNMI Request Model and Data Handling section. 

## Request Model and Data Handling

### gNMI Encoding

### Get Request

### Namespaces

### Wildcard

### Error Messages​