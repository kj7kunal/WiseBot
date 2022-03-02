# WiseBot

WiseBot is an application for tracking better rates and booking transfers using Wise API


## Contents

- [Requirement](#requirement)
- [Process](#process)


## Requirement
[Wise (transferwise)](https://wise.com/) is essentially an online international money transfer service. They use the mid-market exchange rate unlike many banks that charge above-market in addition to adding their own fees. Moreover, they lock this *guaranteed rate* before you hit send so the rate doesn’t go up before your money reaches them. 

The Wise Platform is remarkably simple and easy to use, but I want to go one step further and track the best rate and automatically setup/cancel payments, instead of setting rate alerts that go off in the middle of the night. The [Wise Platform API](https://api-docs.transferwise.com/#wise-platform-api) provides functions to automate payments, connect your business tools, and create ways to manage your finances.

*I am very desperate to transfer my yens.*

## Process

There are four steps to execute payouts:
1. [**Create a quote**](https://api-docs.transferwise.com/payouts#wise-payouts-api-documentation-create-quote): Quote fetches current mid-market exchange rate that will be used for your transfer. Quote also calculates the fee and estimated delivery time.
2. [**Create a recipient account**](https://api-docs.transferwise.com/payouts#wise-payouts-api-documentation-create-recipient-account): Recipient is a person or institution who is the ultimate beneficiary of your payment. Recipient bank account details are different for different currencies.
3. [**Create a transfer**](https://api-docs.transferwise.com/payouts#wise-payouts-api-documentation-create-transfer): A transfer is a payout order you make to a recipient account based on a quote. Once created, a transfer will need to be funded within a specific time period. Otherwise, it will be automatically canceled. 
4. [**Fund a transfer**](https://api-docs.transferwise.com/payouts#wise-payouts-api-documentation-fund-transfer): Wise can now debit funds from your multi-currency account and start processing your transfer. 

The idea is to execute the first 3 steps, till creating a transfer at the best possible quote (and cancel past mediocre ones) in a given timeframe. Funds can be manually transfer later on. 

Wise provides a quota of three guaranteed rate tranfers, however, by cancelling subpar transfers, we should never exceed that quota.
