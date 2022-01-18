# Convert mGNO to GNO

If you need some extra mGNO (for example to top off a balance or for other reasons), you can use the previous swap UI to convert GNO on the Gnosis Chain to mGNO. Note that currently there is not a mechanism to swap mGNO back to GNO.&#x20;

Previous UI: [https://gbc-deposit-old.herokuapp.com/](https://gbc-deposit-old.herokuapp.com)

1\) Go to [https://gbc-deposit-old.herokuapp.com/](https://gbc-deposit-old.herokuapp.com) and connect your web3 wallet on the Gnosis Chain to the application. \
\
In this example we use MetaMask.

![](<../../.gitbook/assets/UI-1 (1).png>)

![](<../../.gitbook/assets/UI-2 (1).png>)

2\) Select the Swap tab. Enter the amount you would like to convert and click **Convert**. You can convert any amount, be sure to **start with a leading 0 to convert less than 1 GNO. For example, 0.1 GNO will be converted to 3.2 mGNO.**

![](../../.gitbook/assets/swap-1.png)

3\) Sign 2 transactions in your wallet. The first is a free signature request to allow the application to make the conversion.

![](../../.gitbook/assets/pt2.png)

The second processes the transaction. This will require a small amount of xDai to complete.

![](../../.gitbook/assets/2tx.png)

&#x20;4\) The transaction should be initiated and completed within a few seconds. Once completed you can click the link to see the tx in BlockScout and add mGNO to your MetaMask wallet. The mGNO contract address is 0x722fc4DAABFEaff81b97894fC623f91814a1BF68.
