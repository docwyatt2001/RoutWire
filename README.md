# Testing repository for RoutWire

SDN based on WireGuard, VxLan, Babel and MQTT
 - MQTT is used to orchestrate the nodes.
 - WireGuard is used to create a secure mesh.
 - VxLan provides a "normal" interface on top of WireGuard.
 - Babel routes local subnets between nodes.  
   - All Bridges with IPs are redistributed as subnets at the moment.
   - The default route is currently source-routed.  
     - Can be tested with traceroute -s.  
     - Baled uses table 10 by default: `ip route show table 10`.  
  
### Pre-requisites
Tested only on 18.04  
  
The Clients/Nodes require:  
`add-apt-repository ppa:wireguard/wireguard -y`  
`apt update && sudo apt -y install wireguard mosquitto-clients babeld`  
  
The Server/Orchestrator only requires (Can be one of the Nodes):  
`sudo apt -y install mosquitto-clients`  
  
Optional, your own MQTT Broker.  
This works for example:  
`docker run -d --restart=unless-stopped --name eclipse-mosquitto -p 1883:1883 -p 9001:9001 eclipse-mosquitto`  
  
### Setup
On Nodes and Orchestrator run:  
`curl https://raw.githubusercontent.com/lorenzo95/RoutWire/master/client-test --output client-test && chmod +x client-test`  

#### Change the config flags and passwords!!!  
  
Run the Orchestrator (Can be one of the Nodes):  
`./client-test server`  
  
Run the Nodes:  
`sudo ./client-test client`
