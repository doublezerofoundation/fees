**TLDR: Fees go into effect starting Epoch 859; please pay those fees sometime during Epoch 860.**

This repo is designed to help Solana validators understand the fees they would pay to DoubleZero, which are assessed at 5% of block rewards per epoch.

Fees go into effect starting in epoch 859 on Solana. Shortly after each epoch ends, we will post a table here with the required payment by pubkey in case you have difficulty computing your block rewards for that epoch. Please make the payment sometime in the subsequent epoch, e.g. make the payment in epoch 860 for being connecting to DoubleZero over 859, epoch 861 for being connected over epoch 860, etc.

In addition, there is some historical data to help users better understand their fee profile. No payment is required for those historical epochs; this is just for estimation purposes. Specifically, in the historical/ folder, there are three files. First, consider block_rewards_data.csv which has historical block rewards data, by pubkey, for epochs 830 - 858, as well as average block rewards and the hypothetical average DoubleZero fee over this period. Second, consider two deep dives into epochs 842 and 855 for all validator earnings. That is, for each active validator in the subsequent epoch, the files earnings_epoch842.csv and earnings_epoch855.csv lists the pubkeys, current commission rates, total inflation earned in that epoch, total MEV rewards earned in that epoch, and total block rewards earned in that epoch, as well as the hypothetical DoubleZero fee. Again, no payment is due for any of these epochs, as fees do not start being levied till epoch 859. This data is provided purely for understanding hypothetical payments.

Please contact nihar@doublezero.us with questions.
