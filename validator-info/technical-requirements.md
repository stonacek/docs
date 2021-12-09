# Technical Requirements

## The Basics

Since GBC is a smaller-stakes environment, it is a great place to refine new skills. Be sure to read instructions carefully and ask questions (dedicated discord channel coming soon) as needed.

* **Using the Terminal**:  You will be required to enter commands into a terminal window. These will be simple copy-paste instructions, but familiarity with using a terminal is helpful.&#x20;
* **Key Management**: You will use the command line to derive a key-pair for validating blocks as well as a mnemonic you will use later to derive a withdrawal pair. It is important to store these safely (offline highly recommended).

### Connectivity

A reliable internet connection is key - bandwidth should not be throttled or capped. Upload bandwidth should be a minimum of 700 MB/hour with increases likely. Brief periods offline may result in small inactivity penalties, but this will be recouped quickly as long as the outage is short.

Note that synching Gnosis Chain (formerly xDai) may take up to 12 hours depending on your setup.&#x20;

### Security

When setting up hardware or a VM, use proper security measures including securing the root account, setting up a firewall, and forwarding necessary ports to the correct machines from the router based on the client you choose for running Gnosis Chain (formerly xDai) and the beacon chain.

* OpenEthereum: 30303 TCP/UDP
* Nethermind: 30303 TCP/UDP
* Lighthouse: 9000 TCP/UDP
* Prysm: 12000 UDP, 13000 TCP

### Time Sync

Your clock should by synchronized to prevent skipping block sealing.

&#x20;Enter`timedatectl status` , you should see similar output:

```bash
Local time: Tue 2020-06-30 17:16:19 UTC
Universal time: Tue 2020-06-30 17:16:19 UTC
RTC time: Tue 2020-06-30 17:16:19
Time zone: Etc/UTC (UTC, +0000)
System clock synchronized: yes
systemd-timesyncd.service active: yes
RTC in local TZ: no
```

If **`System clock synchronized`** displays **`yes`**   you are good to go.

If not, you can either:

* [x] synchronize clock with NTP servers (allow **UDP** port **123** for both incoming and outgoing traffic) or
* [x] use the following script to sync with google.com:

Create `fixtime.sh` script and run it with `watch -n 60` command in a `screen`

```bash
echo sudo date -s '"$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"' > fixtime.sh
chmod +x fixtime.sh
screen -S time
watch -n 60 ./fixtime.sh
```

Press `Ctrl+A+D` to leave the `screen`

## Node Requirements

{% hint style="info" %}
Recommended requirements are met when using DappNode preconfigured hardware or a liquid staking service.
{% endhint %}

### Gnosis (formerly xDai) Node Requirements

To process validator deposits it is recommended to run your own Gnosis node. It will be possible to link GBC to an existing node through a JSON RPC endpoint, however we recommend running your own node to enhance decentralization. Gnosis Nodes can be run with you choice of 2 clients (OpenEthereum and Nethermind) and the following recommended minimum specs:

* OS: Ubuntu (Nethermind & OE), Windows & MacOs (Nethermind only)
* CPU: 2 cores
* RAM: 4GB
* Disk: 50gb SSD
* Git installed `git --version`

[-> Nethermind Node Setup](../clients/gnosis-chain-node-openethereum-and-nethermind/nethermind-node-setup.md)

[-> OpenEthereum Node Setup ](../clients/gnosis-chain-node-openethereum-and-nethermind/openethereum-node-setup.md)

### Beacon Chain Node Requirements

Minimum & Recommended specifications for running Prysm or Lighthouse clients:

### Prysm Client

**Prysm Minimum**

* Operating System: 64-bit Linux, Mac OS X 10.14+, Windows 64-bit
* Processor: Intel Core i5–760 or AMD FX-8100 or better
* Memory: 8GB RAM
* Storage: 20GB available space SSD
* Internet: Broadband connection

**Prysm Recommended**

* Processor: Intel Core i7–4770 or AMD FX-8310 or better
* Memory: 16GB RAM
* Storage: 100GB available space SSD
* Internet: Broadband connection

### Lighthouse Client

**Lighthouse Minimum**

* Dual-core CPU, 2015 or newer
* 8 GB RAM
* 128 GB solid state storage
* 10 Mb/s download, 5 Mb/s upload broadband connection

**Lighthouse Recommended**

* Quad-core AMD Ryzen, Intel Broadwell, ARMv8 or newer
* 16 GB RAM
* 256 GB solid state storage
* 100 Mb/s download, 20 Mb/s upload broadband connection

## Ready to Get Started?

{% hint style="info" %}
If you are interested in running a node in the future, please [fill out this form](https://airtable.com/shrrzJsRLa767gpcQ) and we will contact you to start the setup.
{% endhint %}
