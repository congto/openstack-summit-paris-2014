# Neutron

-	API under HAproxy
-	managing Neutron agents
	-	clean everything on stop start actions:
		-	Interfaces
		-	Child Processes (dnsmasq, metadata proxy)
	-	entities rescheduling after migration
	-	WIP: API handler and rescheduling using internal Neutron mechanism

Note: Speaker - Vladimir Kuklin:

Managing Neutron services is pretty easy when we are talking about API. However, the devil is in the details when you want to safely manage agents. First of all, when you start and stop agents, you need to ensure that they do not leave any artifacts that can affect connectivity, such as orphaned interfaces along with IP addresses or child processes. In order to achieve this, we perform special cleanup actions that destroy previously created interfaces and kill child processes on the nodes. The next thing you need to do is rescheduling of entities, such as routers for l3 agent and networks for DHCP agent after the agent is migrated to another node. For example, this is necessary in case of failover. Current version utilizies Neutron API calls for L3 and dhcp agents. Our Neutron community team is working on moving this functionality to Neutron core. Currently, there is some code for automatic rescheduling, but it showed some issues in case of AMQP failover. Our developers are working to resolve these issues.
