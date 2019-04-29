Testing repository for RoutWire
===============================

SDN based on WireGuard, VxLan, Babel and MQTT
 - MQTT is used to orchestrate the nodes (Nodes to Orchestrator communications).
 - WireGuard is used to create a secure mesh.
 - VxLan provides a "normal" interface on top of WireGuard.
 - Babel routes local subnets between nodes.  
   - All Bridges with IPs are redistributed as subnets at the moment.
   - Including Docker subnets (Won't work if they are the same on all nodes)
  
## Pre-requisites
Tested only on 18.04  
  
The Clients/Nodes require:  
`add-apt-repository ppa:wireguard/wireguard -y`  
`apt update && sudo apt -y install wireguard mosquitto-clients babeld`  
  
The Server/Orchestrator only requires (Can be one of the Nodes):  
`sudo apt -y install mosquitto-clients`  
  
Optional, your own MQTT Broker.  
This works for example:  
`docker run -d --restart=unless-stopped --name eclipse-mosquitto -p 1883:1883 -p 9001:9001 eclipse-mosquitto`  
  
## Setup
On Nodes and Orchestrator run:  
`curl https://raw.githubusercontent.com/lorenzo95/RoutWire/master/routwire --output routwire && chmod +x routwire`  

#### Change the config flags and passwords!!! 
`nano routwire`  
  
Run the Orchestrator (Can be one of the Nodes):  
`./routwire server`  
  
Run the Nodes:  
`sudo ./routwire client`
  
To clean up after the Nodes script:  
`sudo ./routwire stop` can be run.  
