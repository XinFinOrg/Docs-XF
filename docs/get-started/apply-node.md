Once your full node is up and running, you need to apply 
it to make it eligible as a masternode.
[This page](https://xinfin.org/setup-masternode.php) shows a tutorial for beginners to setup a full node.

## Getting sufficient XDC
As 1,00,00'000 XDC are required to apply: 

* If you plan to run your node on testnet, you need to 
fill out the following [Link](http://xinfin.network/#getTestXDC):
to get 1,00,00,000 XDC for testnet.
*Note: Those testnet XDC are only usable in testnet, they have absolutely no trading value*

* If you plan to run your node on mainnet, you need to acquire at least 10Million XDC on 
exchanges that list XDC. 
Please refer to [this page](https://xinfin.io/) for which exchanges listing TOMO.

* Setp Masternode on Testnet [Link](http://xinfin.network)


## Resigning your masternode
In case you want to stop your node, you need to resign it from TomoMaster first 
in order to retrieve your locked funds.
Access TomoMaster for [testnet](https://master.testnet.xinfin.org) or 
[mainnet](https://master.xinfin.org), go to your candidate detail page, 
and click the `Resign` button.
Your funds will be available to withdraw 1440 epochs (around 30 days) after the resignation.

After resigning successfully, you can stop your node. If you ran it with `tmn`, simply run:
```
tmn remove
```

At this point, your masternode is completly terminated.
