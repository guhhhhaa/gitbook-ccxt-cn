---
description: requirements
---

# 要求

## 要求

为了实现与CCXT的集成，需要交换以实现以下方法和结构列表。

## 公开API <a id="public-api"></a>

### 交易所信息，费用表和交易规则 <a id="exchange-information-fee-schedule-and-trading-rules"></a>

* -交易对列表及其状态+ [市场结构](https://github.com/ccxt/ccxt/wiki/Manual#market-structure)[`fetchMarkets`](https://github.com/ccxt/ccxt/wiki/Manual#loading-markets)
* -令牌或资产及其状态+列表[币种结构](https://github.com/ccxt/ccxt/wiki/Manual#currency-structure)[`fetchCurrencies`](https://github.com/ccxt/ccxt/wiki/Manual#loading-markets)
* `fetchTradingLimits` –最小/最大订单量，价格，成本，精度等...
* `fetchTradingFees` –公共或个人交易费
* `fetchFundingLimits` –提款限额清单

### 市场数据 <a id="market-data"></a>

* - 24小时的体积和统计信息+ [股票结构](https://github.com/ccxt/ccxt/wiki/Manual#ticker-structure)[`fetchTicker`](https://github.com/ccxt/ccxt/wiki/Manual#price-tickers)
* - L2 / L3 + [手持订单结构](https://github.com/ccxt/ccxt/wiki/Manual#order-book-structure)[`fetchOrderBook`](https://github.com/ccxt/ccxt/wiki/Manual#order-book)
* -近期公共交易+清单[贸易结构](https://github.com/ccxt/ccxt/wiki/Manual#trade-structure)[`fetchTrades`](https://github.com/ccxt/ccxt/wiki/Manual#trades-executions-transactions)
* -在不同的时段蜡烛或克莱恩数据的交易量清单1M，15M，1H，1D，... + [OHLCV结构](https://github.com/ccxt/ccxt/wiki/Manual#ohlcv-structure)[`fetchOHLCV`](https://github.com/ccxt/ccxt/wiki/Manual#ohlcv-candlestick-charts)

## 私人API <a id="private-api"></a>

### 贸易 <a id="trading"></a>

* -适用于所有类型的账户+ [平衡结构](https://github.com/ccxt/ccxt/wiki/Manual#balance-structure)[`fetchBalance`](https://github.com/ccxt/ccxt/wiki/Manual#querying-account-balance)
* `fetchAccounts` –如果交易所有多个帐户或子帐户，则为必填
* - _极限/市场_订单+ [订单结构](https://github.com/ccxt/ccxt/wiki/Manual#order-structure)[`createOrder`](https://github.com/ccxt/ccxt/wiki/Manual#placing-orders)
* ​[`cancelOrder`](https://github.com/ccxt/ccxt/wiki/Manual#canceling-orders)​
* `editOrder` –更改未结订单的价格和/或金额

### 交易历史 <a id="trading-history"></a>

* -一个为了通过订单ID + [订单结构](https://github.com/ccxt/ccxt/wiki/Manual#order-structure)[`fetchOrder`](https://github.com/ccxt/ccxt/wiki/Manual#querying-orders)
* -所有打开的订单列表[`fetchOpenOrders`](https://github.com/ccxt/ccxt/wiki/Manual#querying-orders)
* -所有订单列表[`fetchAllOrders`](https://github.com/ccxt/ccxt/wiki/Manual#querying-orders)
* -填补交易的个人历史账户+ [贸易结构](https://github.com/ccxt/ccxt/wiki/Manual#trade-structure)[`fetchMyTrades`](https://github.com/ccxt/ccxt/wiki/Manual#personal-trades)

### 资金 <a id="funding"></a>

* -存款地址（ES）+ [地址结构](https://github.com/ccxt/ccxt/wiki/Manual#address-structure)[`fetchDepositAddress`](https://github.com/ccxt/ccxt/wiki/Manual#funding-your-account)
* ​[`fetchDeposits`](https://github.com/ccxt/ccxt/wiki/Manual#transactions)​
* ​[`fetchWithdrawals`](https://github.com/ccxt/ccxt/wiki/Manual#transactions)​
* + [交易结构](https://github.com/ccxt/ccxt/wiki/Manual#transaction-structure)[`fetchTransactions`](https://github.com/ccxt/ccxt/wiki/Manual#transactions)
* -交易，转让，转介，返现+ [总账条目结构](https://github.com/ccxt/ccxt/wiki/Manual#ledger-entry-structure)[`fetchLedger`](https://github.com/ccxt/ccxt/wiki/Manual#ledger)
* ​[`withdraw`](https://github.com/ccxt/ccxt/wiki/Manual#withdraw)​
* `transfer` –如果交易所有多个帐户或子帐户，则为必填

