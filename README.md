# RoutWire
SDN based on WireGuard, VxLan, Babel and MQTT
 - MQTT is used to orchestrate the nodes.
 - WireGuard is used to create a secure mesh.
 - VxLan provides a "normal" interface on top of WireGuard.
 - Babel routes local subnets between nodes (By default all bridges i.e. Docker).
  
### Pre-requisites
Tested only on 18.04  
  
The Clients/Nodes require:  
`add-apt-repository ppa:wireguard/wireguard -y`  
`apt update && sudo apt -y install wireguard mosquitto-clients babeld`  
  
The Server/Orchestrator only requires:  
`sudo apt -y install mosquitto-clients`  
  
Optional, your own MQTT Broker.  
This works for example:  
`docker run -d --restart=unless-stopped --name eclipse-mosquitto -p 1883:1883 -p 9001:9001 eclipse-mosquitto`  
  
### Setup
