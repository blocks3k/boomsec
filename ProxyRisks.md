#Proxy Monitoring to detect upgrade risks

There exists many proxy designs, but they all involve some functioanlity to upgrade your smart contract. This is a very powerful primitive that has many risks to the end user and the developer. 

1 ) Can upgrades lead to storage slot overwrites ? 
    I propose we look the diff of storage slot updates in a simulation before the contract can be upgraded.
    This happens if you mix upgradable contracts with non-upgradable ones.
