# Testing HA and results

## Testing 
- fuel-devops - tiny piece of libvirt-based orchestrator
- destructive tests:
    -  running virtual environments
    -  running bare-metal environments
    -  performing destructive actions
-  testing that cluster failed over successfully:
    - FUEL OSTF
    - Tempest
    - Rally

Note: Speaker - Sergii Golovatiuk:

Testing HA does not come at easy cost. We are doing this primarily using our own test suite. We spawn environments using our tiny orchestrator which uses python libvirt and other libraries. Then we perform actual destructive actions and check if cluster can failover succesfully using FUEL OSTF as well as other test suites.


## Results

- controller reset 
- all controllers reset
- networking partitioning
- AMQP cluster node failure
- DB node failure
- particular OS service failure 

Note:
Speaker - Vladimir Kuklin

So far, speaking of results that we achieved with HA installations is that we can
easily handle single-failure-at-a-time tolerance for the whole OpenStack cluster
whether these are networking problems, failure of DB, amqp or particular OpenStack services. And this was not only confirmed by our tests but also by our most significant partners and customers including carrier-grade ones running extensive and rigorous testing saying that they still cannot break our HA setup.  

