# Limit-Order-Bot CosmWasm smart contract for Curve on Paloma

This is a CosmWasm smart contract to manage limit-orders on a limit-order-bot smart contract on EVM chain written in Vyper.

Users can deposit their token or coin into a Vyper smart contract on EVM chain.

There is a view function in the smart contract that returns deposit_id list that can be swapped on Uniswap V2 or a DEX that works just like it.

A scheduler or script fetch the list from the Vyper smart contract and run `multiple_withdraw` function with the list via Compass-EVM.

And then, the Vyper smart contract will swap the assets and sent them to the depositors.

## ExecuteMsg

### PutWithdraw

Run `withdraw` function on Vyper smart contract.

| Key                        | Type        | Description                                                           |
|----------------------------|-------------|-----------------------------------------------------------------------|
| deposit_ids                | Vec\<u32\>  | Deposit ids that can swap on a Vyper smart contract                   |
| profit_taking_or_stop_loss | Vec\<bool\> | Vector of boolean that True for profit taking and False for stop loss |

## QueryMsg

### GetJobId

Get `job_id` of Paloma message to run `multiple_withdraw` function on a Vyper smart contract.

| Key | Type | Description |
|-----|------|-------------|
| -   | -    | -           |

#### Response

| Key    | Type   | Description      |
|--------|--------|------------------|
| job_id | String | Job Id on Paloma |
