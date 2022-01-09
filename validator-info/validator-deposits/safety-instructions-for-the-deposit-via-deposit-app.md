# Safety Instructions for the Deposit via Deposit App

#### Make sure you aren't being phished

You are responsible for the transaction. Fraudulent websites might try to lure you into sending funds to them, instead of the official deposit contract. Make sure that you are sending the transaction with the correct data.

1. Check that transaction makes a call to mGNO token contract on Gnosis Chain: [0x722fc4DAABFEaff81b97894fC623f91814a1BF68](https://blockscout.com/xdai/mainnet/address/0x722fc4DAABFEaff81b97894fC623f91814a1BF68/transactions)\
   \
   &#x20;![](../../.gitbook/assets/MM\_1.png)\

2. Check that the transaction uses the `transferAndCall` method.\
   \
   &#x20;![](../../.gitbook/assets/MM\_2.png)\

3. Check that transaction data (HEX tab) includes GBC Deposit Contract address [0x0B98057eA310F4d31F2a452B414647007d1645d9](https://blockscout.com/xdai/mainnet/address/0x0B98057eA310F4d31F2a452B414647007d1645d9/transactions) in this form: \
   `0x4000aea00000000000000000000000000b98057ea310f4d31f2a452b414647007d1645d9` \
   \
   ![](../../.gitbook/assets/MM\_3.png)

