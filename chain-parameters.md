# Chain Parameters

**Initial Parameters (subject to change):**

| Variable                                        | Value                                                                                                                                                                      |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Staking amount                                  | 32 mGNO (equivalent to 1 GNO)                                                                                                                                              |
| Block time                                      | 5 seconds                                                                                                                                                                  |
| Validator slots per epoch                       | 16 (with further reduction possible, [N > 1 honest proposer/epoch as per V. Buterin](https://notes.ethereum.org/@vbuterin/rkhCgQteN?type=view#Why-32-ETH-validator-sizes)) |
| Validators per slot                             | 128 ([see more on minimum committee size](https://medium.com/@chihchengliang/minimum-committee-size-explained-67047111fa20))                                               |
| Epoch time                                      | 80 seconds                                                                                                                                                                 |
| Slashing                                        | Reductions to 16 mGNO, then removal                                                                                                                                        |
| Clients                                         | Prysm, Lighthouse                                                                                                                                                          |
| Custom Deposit Contract                         | <p></p><ul><li>mGNO deposit (ERC20 enabled)</li><li>Upgradeable</li><li>Claiming on accidental locks</li><li>Custom network keys generation (deposit-cli)</li></ul>        |
| Explorer                                        | Modified beaconchain explorer                                                                                                                                              |
| MVP for launch (pending system tolerance tests) | <p>4096 validators<br>131,072 mGNO </p><p>83% APY</p>                                                                                                                      |
| Security Goal Prior to Merge                    | <p>50K+ validators</p><p>1.6M+ mGNO equivalent</p><p>23% APY</p>                                                                                                           |
