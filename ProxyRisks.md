#Proxy Monitoring to detect upgrade risks

There exists many proxy designs, but they all involve some functioanlity to upgrade your smart contract. This is a very powerful primitive that has many risks to the end user and the developer. 

1 ) Can upgrades lead to storage slot overwrites ? 
    I propose we look the diff of storage slot updates in a simulation before the contract can be upgraded.
    This happens if you mix upgradable contracts with non-upgradable ones.

2 ) Can upgrade be done instantly?
       This is a rug pull risk, You can mitigate this by requiring a time lock, but this is not a perfect solution. Use designs like a trusted multisig for mitigating security issues.
       
3 ) Inititialize proxy implimentations and Logic
        This is one of the dev op's issues that affect a lot of projects in this space, make sure your code is initialized since constructors won't be used with upgradable contracts. It's also a good idea to initialize your implimentation contract of the proxy
        
4 ) SELFDESTRUCRT reachable from a delegatecall
        This is a powerful combo that can lead to funds being stuck in the contract with no path to recovery, one should be careful with allowing delegatecalls.
        
5 ) DiamondProxy
        This is a great tool for developers to write extensible and modular upgrade logic, but this can go wrong really fast as this feature allows modular upgradability and extensiblity. 
        
7 ) Function call collusions can happen in proxy implimentations leading to un-inted consequenses.

8 ) Ensure that Initializer modifier is used correctly with your initialization functions.
