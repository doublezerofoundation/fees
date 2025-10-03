This repo is designed to help Solana validators understand the fees they would pay to DoubleZero, which are assessed at 5% of block rewards per epoch.

Fees go into effect starting in epoch 859 on Solana. Shortly after each epoch ends, we will post a table here with the required payment by pubkey in case you have difficulty computing your block rewards for that epoch. Please make the payment sometime in the subsequent epoch, e.g. make the payment in epoch 860 for being connecting to DoubleZero over 859, epoch 861 for being connected over epoch 860, etc.

In addition, there is some historical data to help users better understand their fee profile. In the historical/ folder, there are three files. First, consider block_rewards_data.csv which has historical block rewards data, by pubkey, for epochs 830 - 857, as well as average block rewards and the hypothetical average DoubleZero fee over this period. Second, consider two deep dives into epochs 842 and 855 for all validator earnings. That is, for each active validator in the subsequent epoch, the files earnings_epoch842.csv and earnings_epoch855.csv lists the pubkeys, current commission rates, total inflation earned in that epoch, total MEV rewards earned in that epoch, and total block rewards earned in that epoch, as well as the hypothetical DoubleZero fee. To be clear, no payment is due for any of these epochs, as fees do not start being levied till epoch 859. This data is provided purely for understanding hypothetical payments.

<br>You can also run the following curl command to fetch this data:
```
curl -s "https://api.trillium.so/validator_rewards/<EPOCH>" | \
jq --arg pubkey "<IDENTITY_PUBKEY>" \
'.[] | 
select(.identity_pubkey == $pubkey) | 
{
  "name": .name,
  "pubkey": .identity_pubkey,
  "votekey": .vote_account_pubkey,
  "epoch": .epoch,
  "stake": (.total_from_stake_pools + .total_not_from_stake_pools),
  "commission": .commission,
  "mev_commission": (.mev_commission / 100),
  "inflation": .total_inflation_reward,
  "mev_rewards": .mev_earned,
  "block_rewards": .rewards,
  "dz_fee": (.rewards / 20)
}'
```

<br>Please replace <EPOCH> and <IDENTITY_PUBKEY> with suitable values as below:
```
curl -s "https://api.trillium.so/validator_rewards/855" | \
jq --arg pubkey "DRpbCBMxVnDK7maPM5tGv6MvB3v1sRMC86PZ8okm21hy" \
'.[] | 
select(.identity_pubkey == $pubkey) | 
{
  "name": .name,
  "pubkey": .identity_pubkey,
  "votekey": .vote_account_pubkey,
  "epoch": .epoch,
  "stake": (.total_from_stake_pools + .total_not_from_stake_pools),
  "commission": .commission,
  "mev_commission": (.mev_commission / 100),
  "inflation": .total_inflation_reward,
  "mev_rewards": .mev_earned,
  "block_rewards": .rewards,
  "dz_fee": (.rewards / 20)
}'
```

<br>Response:
```
{
  "name": "binance staking",
  "pubkey": "DRpbCBMxVnDK7maPM5tGv6MvB3v1sRMC86PZ8okm21hy",
  "votekey": "3N7s9zXMZ4QqvHQR15t5GNHyqc89KduzMP7423eWiD5g",
  "epoch": 855,
  "stake": 14412440.45296,
  "commission": 1,
  "mev_commission": 10,
  "inflation": 5024.60048,
  "mev_rewards": 50.97801,
  "block_rewards": 209.71803,
  "dz_fee": 10.4859015
}
```

<br>Please contact nihar@doublezero.us with questions.
