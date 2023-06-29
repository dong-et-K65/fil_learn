# Networking architecture
- OpenStack Networking is a standalone service that often deploys several processes across a number of nodes. These processes interact with each other and other OpenStack services (e.g. Nova, ...).  
- The main process of the OpenStack Networking service is ***neutron-server***.  
- ***neutron-server*** is a Python daemon that exposes the *OpenStack Networking API* and passes tenant requests to a suite of plug-ins for additional processing.
## The OpenStack Networking Components
### **neutron server (neutron-server and neutron-*-plugin)**
This service runs on the network node to service the Networking API and its extensions. It also enforces the network model and IP addressing of each port. The neutron-server requires indirect access to a persistent database. This is accomplished through plugins, which communicate with the database using AMQP (Advanced Message Queuing Protocol).
### __plugin agent (neutron-*-agent)__
Runs on each compute node to manage local virtual switch (vswitch) configuration. The plug-in that you use determine which agents run. This service requires message queue access and depends on the plugin used. Some plugins like OpenDaylight(ODL) and Open Virtual Network (OVN) do not require any python agents on compute nodes.
### __DHCP agent (neutron-dhcp-agent)__
Provides DHCP services to tenant networks. This agent is the same across all plug-ins and is responsible for maintaining DHCP configuration. The neutron-dhcp-agent requires message queue access. Optional depending on plug-in.
### __L3 agent(neutron-l3-agent)__ 
Provides L3/NAT forwarding for external network access of VMs on tenant networks. Requires message queue access. Optional depending on plug-in.
### __network provider services (SDN server/services)__
Provides additional networking services to tenant networks. These SDN services may interact with _neutron-server_, _neutron-plugin_, and plugin-agents through communication channels such as REST APIs.
