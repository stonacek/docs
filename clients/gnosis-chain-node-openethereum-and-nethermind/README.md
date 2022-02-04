# Gnosis Chain Node (OpenEthereum & Nethermind)

{% hint style="info" %}
This process is optional and suggested for experienced node runners only.
{% endhint %}

In addition to running a GBC client, we also recommend running a separate Gnosis Chain Node execution layer client. Gnosis Chain (formerly xDai Chain) will be used to process validator deposits and later incorporated as a shard.

While it is possible to link GBC to an existing node using a JSON RPC endpoint, running your own node promotes decentralization. Gnosis Nodes can be run with your choice of OpenEthereum or Nethermind with the following recommended minimum specs:

* OS: Ubuntu (Nethermind & OE), Windows & MacOs (Nethermind only)
* CPU: 2 cores
* RAM: 4GB
* Disk: 100gb SSD
* Git installed `git --version`

The following instructions are for the xDai chain setup. Instructions will be updated at some point to reflect the naming change, for now instructions are followed as is.

[-> Nethermind Node Setup](nethermind-node-setup.md)

[-> OpenEthereum Node Setup](openethereum-node-setup.md)
