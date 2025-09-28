This repo is designed to help validators estimate the fees they would pay to DoubleZero, which are assessed at 5% of block rewards per epoch.

block_rewards_data.csv has historical block rewards data, by pubkey, for epochs 830 - 856. It then computes average block rewards in the second-to-last column and average DoubleZero fees in the last column. A validator can find its pubkey in the file to understand its fees on a historical basis.

In addition, the repo currently has two deep-dives into epochs 842 and 856 for all validator earnings. That is, for each active validator in the subsequent epoch, the files earnings_epoch842.csv and earnings_epoch856.csv lists the pubkeys, current commission rates, total inflation earned in that epoch, total MEV rewards earned in that epoch, and total block rewards earned in that epoch. It then also notes the associated DoubleZero fee in the last column.

Please contact nihar@doublezero.us with questions.
