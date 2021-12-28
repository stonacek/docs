# FAQ

{% hint style="info" %}
FAQs are in progress.
{% endhint %}

## General

### What is a validator?

Validators propose and vote on blocks to include in the chain. The chain is secured by a staked amount of mGNO. Validators stake mGNO and receive additional mGNO as rewards for correct behavior (proposing and attesting blocks) and a slashed balance as penalties for incorrect behavior (offline node, attesting invalid blocks). &#x20;

### What is the deposit contract?&#x20;

The deposit contract keeps track of validators and staking amounts. The GBC deposit contract is based on [the original Ethereum 2.0 deposit contract](https://github.com/ethereum/consensus-specs/blob/master/solidity\_deposit\_contract/deposit\_contract.sol), with [some additional functionality](security-audit.md).

* Contract Security Audit by Chainsecurity: [https://chainsecurity.com/security-audit/poa-network-stake-beacon-chain-sbc-deposit/](https://chainsecurity.com/security-audit/poa-network-stake-beacon-chain-sbc-deposit/)&#x20;
* GBC Contract Address: [0x0B98057eA310F4d31F2a452B414647007d1645d9](https://blockscout.com/xdai/mainnet/address/0x0B98057eA310F4d31F2a452B414647007d1645d9)

### How much do validators earn in rewards?

This varies based on how many validators are participating. As the number of validators increases, the reward for validation is reduced as security becomes increasingly decentralized. Additional info is available on the [incentives page](incentives.md).

### How many validator processes can run per node?

It is possible to run multiple validator processes on a single node with GBC. A 4CPU/8GB node handled 256 validators during testing processes, although for higher decentralization it is recommended to run multiple nodes, and in an ideal situation 1 per validator.

## mGNO

### What is mGNO?

mGNO is a metatoken for GNO, similar to a wrapped token like WETH. However, where WETH is wrapped 1:1 with ETH, mGNO is wrapped 32:1 with GNO. **There are 32 mGNO to each GNO.**

mGNO is the staking token used by validators in the Gnosis Beacon Chain.&#x20;

### How do I get mGNO?

A UI is in process. Future functionality will also make the swap more seamless, so that validators will only need to provide GNO and the swap from GNO to mGNO will happen behind the scenes.

For now, you can get mGNO by [interacting with the contract on BlockScout](validator-info/validator-deposits.md#1-convert-gno-to-mgno). You must have GNO on the Gnosis Chain (not on the Ethereum mainnet) to convert them to mGNO. You can move GNO from Ethereum to xDai using the [OmniBridge](https://omni.xdaichain.com/bridge).&#x20;

### How much mGNO do I need to stake to become a validator?

32 mGNO are staked for each validator. This is the equivalent of 1 GNO. 32 is used to remain consistent with the Ethereum Beacon Chain, where 32 ETH are required to run a validator.

### Can I swap mGNO back to GNO

No, not currently. Once withdrawals are activated, users will be prompted to swap during the withdrawal process.

## Nodes & Clients&#x20;

### Which clients are supported by GBC?

Modified versions of [Lighthouse](clients/lighthouse.md) and [Prysm](clients/prysm.md).  DAppNode will initially support the Prysm implementation only.

### How long does it take to sync the Gnosis Chain?

Along with running the GBC client you should also consider running a Gnosis Chain Node to connect to (not required but recommended).

Syncing the [Gnosis Chain using Nethermind or OpenEthereum](clients/gnosis-chain-node-openethereum-and-nethermind/) requires \~40GB (and growing) of data to download. You may encounter some errors during synching. Depending on your setup, you can expect it to take anywhere from a few hours to up to a day.

### Can I use a node provider to run a Gnosis Chain node?

Yes you can. Providers who currently support Gnosis Chain:

* **QuikNode**  [https://blog.quiknode.io/xdai-network-is-live-on-quiknode/](https://blog.quicknode.com/xdai-network-is-live-on-quiknode/)****
* **Ankr** [https://www.ankr.com/](https://www.ankr.com)****
* **GetBlock.io** [https://getblock.io/nodes/stake](https://getblock.io/nodes/stake)****
* **AnyBlock Analytics** [https://www.anyblockanalytics.com/json-rpc](https://www.anyblockanalytics.com/json-rpc/)****
* **Pocket** [https://www.portal.pokt.network](https://www.portal.pokt.network/#1)

## Can I use DappNode?

Yes! DappNode is a partner and full-featured service provider for the Gnosis Beacon Chain. If you would like to use their services for validation, please see the [guide and instructions here.](https://forum.dappnode.io/t/how-to-setup-a-gnosis-beacon-chain-gbc-validator-on-dappnode/1351)

## Withdrawals

### When will withdrawals be active?

Following the merge between Gnosis Beacon Chain and Gnosis Chain. This is currently scheduled to occur \~1 week prior to the ETH2 merge (Scheduled for June, 2022).

### **What are withdrawal credentials?**

[Withdrawal Credentials](https://github.com/ethereum/eth2.0-specs/blob/master/specs/phase0/validator.md#withdrawal-credentials) are specified during the key generation process. Currently, there are two types of withdrawals: BLS withdrawal and Eth1 address withdrawal. An Eth1 address is an 0x address you use on current EVM chains such as Gnosis Chain, Ethereum, BSC etc.

1. Eth1 address withdrawal: If you want to withdraw to an EVM chain after the merge, set `--eth1_withdrawal_address <YOUR 0x ADDRESS>` when running the deposit script. **Make sure you control this Eth1 EVM address, as you will use it to initiate a withdrawal.**
2. BLS withdrawal: If an Eth1 withdrawal address is not specified, the, deposit script generates withdrawal credentials with the withdrawal key derived via mnemonics in [EIP2334](https://eips.ethereum.org/EIPS/eip-2334)  (Eth2 address format) format. You will use this mnemonic during the withdrawal process, so be sure to keep it secure.

### Can I withdraw rewards I have earned (without withdrawing my entire 32mGNO stake)?

Current plans do not include partial withdrawals of rewards only. You will be able to withdraw your full validator balance with all accumulated rewards once withdrawals are implemented.

### Can I withdraw deposit mistakes now (duplicate deposits)?

Withdrawals are currently not available, even if you've accidentally sent extra mGNO to a validator. If you mistakenly made a duplicate deposit to a validator using the same public key, you will still be able to perform a full withdrawal once withdrawals are enabled.

### What types of addresses can be used for withdrawals? EOA, contact, Gnosis Safe, proxy, stub?

Yes! It should be safe to use any type of supported withdrawal credentials,  either an ETH1 address (i.e. Gnosis Chain address) or a BLS credential.

For BLS withdrawal credentials, make sure to keep the mnemonic phrase from the key generation process. Once withdrawals are enabled, you will need to use it to sign a withdrawal request message.&#x20;

For ETH1 withdrawal credentials, make sure you have  full control over the specified address and can execute transactions on behalf of this address. Three common options for ETH1 withdrawal credentials:

* **EOA address**. Make sure to keep its private key / mnemonic in a secure place, so that you will have access to it once withdrawals are enabled.
* **Gnosis Safe multisig**. Make sure you can execute calls on behalf of the safe address once withdrawals are enabled.
* **Stub proxy**. For advanced users and service providers, another option is to deploy a proxy contract with an empty implementation. Once all details about the withdrawals are known, you can upgrade your proxy to any implementation that suits you needs. Just make sure you have full control over the upgradeability procedure, so that you will be able to update an implementation address once withdrawals are enabled.

