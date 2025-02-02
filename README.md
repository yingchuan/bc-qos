# Bandwidth Conscious QoS
## Environment - Edge Computing Gateway
![Edge Computing Gateway](bc-qos/edge-computing-gateway.drawio.png)

## Requrements
| SSID        | VLAN ID | Priority | Description           |
|-------------|---------|-----------|----------------------|
| SSID 1      | VLAN 10 | 1         | Management Network   |
| SSID 2      | VLAN 20 | 2         | IoT Devices Network  |
| SSID 3      | VLAN 30 | 3         | Staff Network        |
| SSID 4      | VLAN 40 | 4         | Guest Network        |

## Hirarchical Queuing Discipline
![HTB Queue](bc-qos/htb-queue.drawio.png)

### The Flow Queue CoDel Packet Scheduler
![fq_codel](bc-qos/fq_codel.drawio.png)

## Bandwidth Detection
![bandwidth-detection](bc-qos/bandwidth-detection.drawio.png)

### ECHO Request Message
| Counters | Description                                        |
|---------------|---------------------------------------------------|
|S                | the TX counter when ECHO-Req1 to be sent |
|R                |  the RX counter when ECHO-Req1 to be received |
|S'               | the TX counter when ECHO-Req2 to be sent |
|R'              | the RX counter when ECHO-Req2 ro be received |

### ECHO Response Message
![data-rate](bc-qos/data-rate.png)

## Results
### tap0 with `qdisc pfifo` (default) +  4 tcp flows
![TCP performance: upstream](bc-qos/53308970_10205319027652084_4430110533617713152_n.jpg)

### tap0 with `qdisc htb + 4 classes (fq_codel)` + 4 tcp flows
![TCP performance: upstream](bc-qos/53643505_10205319037172322_5707731491631398912_n.jpg)
