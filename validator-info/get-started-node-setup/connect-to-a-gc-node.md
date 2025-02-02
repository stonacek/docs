# Connect to a GC Node

If you choose not to use the public RPC and want to connect to your own GC node, follow these instructions:

* If using a 3rd party node provider, set `XDAI_RPC_URL`=https://\<your-endpoint>&#x20;
* If you are running a GC node on the same machine as your Prysm setup, you can include a host gateway parameter into your docker-compose file then set `XDAI_RPC_URL=`http://host.docker.internal:8545 to access. **See details below**

### **Extra Hosts Parameter**

If you are running a GC node on the same machine as your Beacon Chain client, add the `extra_hosts` parameter to your `docker-compose.yml` file to expose the container and connect to the node.&#x20;

Example:

```
version: '3.8'
services:
  node:
    image: ghcr.io/gnosischain/gbc-lighthouse:v2.0.1-gbc
    command: |
      lighthouse beacon_node
      --testnet-dir /root/sbc/config
      --discovery-port 12000
      --port 13000
      --eth1-endpoints $XDAI_RPC_URL
      --datadir /home/.eth2/beaconchaindata
      --http-address 127.0.0.1
      --http
      --enr-address $PUBLIC_IP
      --enr-udp-port 12000
      --debug-level $LOG_LEVEL
    network_mode: host
    volumes:
      - ./config:/root/sbc/config
      - ./node_db:/home/.eth2/beaconchaindata
    logging:
      driver: "json-file"
      options:
        max-size: "100m"
        max-file: "1"
     extra_hosts:
       - "host.docker.internal:host-gateway"
```

You can then set the `XDAI_RPC_URL=`http://host.docker.internal:8545 in your .env file.

If using Lighthouse, you can also set fallback IP(s). Use comma-separated RPC urls for the `XDAI_RPC_URL` variable. This is useful if your node goes offline. For example:

* `XDAI_RPC_URL`=https://\<your-endpoint>, [https://rpc.gnosischain.com](https://rpc.gnosischain.com)&#x20;
