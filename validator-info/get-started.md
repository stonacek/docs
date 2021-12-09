# Get Started

{% hint style="info" %}
If you are interested in running a node in the future, please [fill out this form](https://airtable.com/shrrzJsRLa767gpcQ) and we will contact you to start the setup.
{% endhint %}

## Chain Currently in Alpha Deployment Phase

### -Instructions in Development -&#x20;

{% hint style="danger" %}
Instructions are in process and not yet complete. If you are not currently working with the team to run a validator, please fill out the form above and we will contact you with more information.
{% endhint %}

## 1) Setup and run a Gnosis Chain (formerly xDai) node&#x20;

You can select either OpenEthereum or Nethermind as your client of choice. Follow these instructions to get started:

* [Nethermind](../clients/gnosis-chain-node-openethereum-and-nethermind/nethermind-node-setup.md)
* [OpenEthereum](../clients/gnosis-chain-node-openethereum-and-nethermind/openethereum-node-setup.md)

## 2) Generate a validator account using the deposit CLI

These instructions use native python, see the `Readme` for other options.

1. git clone  [https://github.com/gnosischain/deposit-cli](https://github.com/gnosischain/deposit-cli) and cd into sbc-deposit-cli root folder.&#x20;
2.  Check you are using Python Version >= Python3.7

    ```
    python3 -V
    ```
3.  Run the helper script to install dependencies

    ```
    ./deposit.sh install
    ```
4.  Run the following command to access the interactive CLI

    ```
    ./deposit.sh new-mnemonic --chain stake
    ```
5. Generate your keys following the prompts.
   1. Choose how many validators you want to run.
   2. Choose a password to store validator keystore(s) (you will need this password later for beacon client implementation, so save securely).
   3. Write down your 24 word mnemonic (KEEP OFFLINE).
   4. Confirm you mnemonic.
   5. Deposit data and keystore.json files will be created in a newly created validator\_keys folder.

## 3) Choose Beacon Chain Client and Setup a Validator Node

Current instructions use Sokol testnet implementation_._&#x20;

{% hint style="warning" %}
**Node should be completely synced before proceeding to step 4: Deposit Staking Token.** _Sync check instructions below._
{% endhint %}

### Prysm

* Follow the instructions here: \
  [https://github.com/gnosischain/prysm-launch/tree/master](https://github.com/gnosischain/prysm-launch/tree/master)
* [Prysm Discord for questions](https://discord.gg/z9efH7e)

Once complete, check the sync status of your node:

```
curl http://localhost:3500/eth/v1alpha1/node/syncing
```

&#x20;If your node is done synchronizing, you will see the response:

```
 {"syncing":false}
```

### Lighthouse

* Follow the instructions here: \
  [https://github.com/gnosischain/lighthouse-launch](https://github.com/gnosischain/lighthouse-launch)
* [Lighthouse Discord server for questions](https://discord.gg/uC7TuaH)

### **Verify your connection**

Verify the connection between your SBC beacon node and client.

```json
 curl -H "Content-Type: application/json" -X POST --data
'{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":67}' 
http://<YourServerLocation>:8545
```

## 4) Deposit staking token&#x20;

{% hint style="info" %}
Staking contract UI in process
{% endhint %}

Staking will require two transactions. The first wraps GNO deposit tokens into 32 mGNO metaTokens. The second deposits mGNO using the  `transferAndCall` method).

## 5) Check status

&#x20;[https://beacon.blockscout.com/ ](https://beacon.blockscout.com)

Install Prometheus and Grafana Monitoring:

* Lighthouse [https://github.com/sigp/lighthouse-metrics](https://github.com/sigp/lighthouse-metrics)
* Prysm [https://docs.prylabs.network/docs/prysm-usage/monitoring/grafana-dashboard/](https://docs.prylabs.network/docs/prysm-usage/monitoring/grafana-dashboard/)
