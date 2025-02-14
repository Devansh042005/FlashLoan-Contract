FlashLoan Arbitrage Contract

Overview

This Solidity contract facilitates flash loan-based triangular arbitrage on the Ethereum blockchain. It's designed to leverage price differences between assets on PancakeSwap, aiming to generate profits through successive trades within a single transaction block.

Contract Functionality

InitateArbitrage

Description: Initiates the arbitrage by swapping borrowed BUSD for WBNB in the liquidity pool.

Parameters:
_busdBorrow: Address of the borrowed BUSD token.
_amount: Amount of BUSD to borrow for the arbitrage.

Actions:

Approves BUSD, CROX, and CAKE token spending on the PancakeSwap Router.
Identifies the liquidity pool between BUSD and WBNB.
Swaps BUSD for WBNB in the liquidity pool, initiating the arbitrage process.

pancakeCall

Description: Executes the arbitrage steps and handles repayment to the flash loan pool.

Parameters:

_sender: Address initiating the call.
_amount0: Amount of the first token in the pair.
_amount1: Amount of the second token in the pair.
_data: Encoded data containing details for the arbitrage.

Actions:

Checks and validates the sender and contract alignment.
Decodes the data to retrieve loan details (borrowed token, amount, borrower's address).
Executes the series of trades for triangular arbitrage (BUSD → CROX → CAKE → BUSD).
Verifies the profitability of the arbitrage.
Transfers profits to the initiator and repays the flash loan.

Other Functions

getBalanceOfToken: Retrieves the contract's balance of a specific token.
placeTrade: Executes token swaps through PancakeSwap based on specified tokens and amounts.
checkResult: Helper function to check if the arbitrage yields profits.
