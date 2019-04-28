# RoutWire
SDN based on WireGuard, VxLan, Babel and MQTT
 - MQTT is used to orchestrate the nodes
 - WireGuard is used to create a secure mesh
 - VxLan provides a "normal" interface on top of WireGuard
 - Babel routes local subnets between nodes (By default all bridges i.e. docker)
  
### Pre-requesites
Tested only on 18.04  
  
`add-apt-repository ppa:wireguard/wireguard -y`  
`apt update && sudo apt -y install wireguard mosquitto-clients babeld`  
  
### Setup
