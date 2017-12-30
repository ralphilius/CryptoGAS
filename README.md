# CryptoGAS
This Google Apps Script library provide functions to retrieve values from cryptocurrency marketplace in order to build a portfolio.

## Installation
1. Create or open desired Google Sheets
2. Open Tools >> Script Edit 
3. Create `jsSHA.gs` and `CryptoGAS.gs` files with content from this repo

## Supported Sites
Currently, CryptoGAS has API integration with below trading platforms:
- Bittrex
- HitBTC
- Bitsane

## Usage
### 1. Bittrex
Open a sheet then type following function with all required parameters 
`=Bittrex(apiMethod,apiKey,apiSecret, query, parseOptions)`

|Parameter|Required|Description|
|---------|:------:|-----------|
|apiMethod|:heavy_check_mark:|See below for all supported methods|
|apiKey   |:heavy_check_mark:|API Key obtained in the Settings|
|apiSecret|:heavy_check_mark:|Secret passphrase to sign request|
|query    |:x:|A comma-separated list of fields to import, decided by the path of the header. Use `rawHeaders` option below to get the path info|
|parseOptions|:x:|A comma-separated list of these options: `noInherit`, `noTruncate`, `rawHeaders`, `noHeaders`, `noParseNumbers`, `debugLocation`|

**Example:** `=Bittrex('account/getbalances','myApiKey','mySecretKey')`

#### apiMethod
|Method|Status|Description|
|------|:----:|-----------|
|public/getmarkets|:heavy_check_mark:|Used to get the open and available trading markets at Bittrex along with other meta data.|
|public/getcurrencies|:heavy_check_mark:|Used to get all supported currencies at Bittrex along with other meta data.|
|public/getticker|:x:|Used to get the current tick values for a market.|
|public/getmarketsummaries|:heavy_check_mark:|Used to get the last 24 hour summary of all active exchanges|
|public/getmarketsummary|:x:|Used to get the last 24 hour summary of all active exchanges for a given market|
|public/getorderbook|:x:|Used to get retrieve the orderbook for a given market|
|public/getmarkethistory|:x:|Used to retrieve the latest trades that have occured for a specific market.|
|market/getopenorders|:x:|Get all orders that you currently have opened. A specific market can be requested (in development)|
|account/getbalances|:heavy_check_mark:|Used to retrieve all balances from your account|
|account/getbalance|:x:|Used to retrieve the balance from your account for a specific currency.|
|account/getdepositaddress|:x:|Used to retrieve or generate an address for a specific currency. If one does not exist, the call will fail and return ADDRESS_GENERATING until one is available.|
|account/getorder|:x:|Used to retrieve a single order by uuid.|
|account/getorderhistory|:heavy_check_mark:|Used to retrieve your order history.|
|account/getwithdrawalhistory|:heavy_check_mark:|Used to retrieve your withdrawal history.|
|account/getdeposithistory|:heavy_check_mark:|Used to retrieve your deposit history.|

Methods with :x: required additional parameters which are not supported yet.
API Reference: https://bittrex.com/Home/Api


#### parseOptions
|Option|Description|
|------|-----------|
|noInherit|Don't inherit values from parent elements|
|noTruncate|Don't truncate values|
|rawHeaders|Don't prettify headers|
|noHeaders|Don't include headers, only the data|
|noParseNumbers|Don't parse number from string, leave it as it is|
|debugLocation|Prepend each value with the row & column it belongs in|

### 2. HitBTC
Open a sheet then type following function with all required parameters 
`=HitBTC(apiMethod,apiKey,apiSecret, query, parseOptions)`

|Parameter|Required|Description|
|---------|:------:|-----------|
|apiMethod|:heavy_check_mark:|See below for all supported methods|
|apiKey   |:heavy_check_mark:|API Key obtained in the Settings|
|apiSecret|:heavy_check_mark:|Secret passphrase to sign request|
|query    |:x:|A comma-separated list of fields to import, decided by the path of the header. Use `rawHeaders` option below to get the path info|
|parseOptions|:x:|A comma-separated list of these options: `noInherit`, `noTruncate`, `rawHeaders`, `noHeaders`, `noParseNumbers`, `debugLocation`|

**Example:** `=HitBTC('account/balance','myApiKey','mySecretKey')`

#### apiMethod
|Method|Status|Description|
|------|:----:|-----------|
|public/currency|:heavy_check_mark:|Return the actual list of available currencies, tokens, ICO etc.|
|public/currency/{currency}|:heavy_check_mark:|Return the information of a specific currency.|
|public/symbol|:heavy_check_mark:|Return the actual list of currency symbols (currency pairs) traded on HitBTC exchange.|
|public/symbol/{symbol}|:heavy_check_mark:|Return information of a specific symbol|
|public/ticker|:heavy_check_mark:|Return ticker information|
|public/ticker/{symbol}|:heavy_check_mark:|Return ticker information of a specific symbol|
|public/orderbook/{symbol}|:exclamation:|Return an order book which is an electronic list of buy and sell orders for a specific symbol, organized by price level.|
|public/candles/{symbol}|:exclamation:|Return a candles used for OHLC a specific symbol.|
|trading/balance|:heavy_check_mark:|Get trading balance all all currencies|
|order|:heavy_check_mark:|Return array of active orders.|
|order/{clientOrderId}|:heavy_check_mark:|Return information of a specific order|
|trading/fee/{symbol}|:heavy_check_mark:|Get personal trading commission rate.|
|history/order|:exclamation:|Return all order history. All orders older then 24 hours without trades are deleted.|
|history/trades|:exclamation:|Return all trades history.|
|history/order/{orderId}/trades|:heavy_check_mark:|Return all trades history for an order|
|account/balance|:heavy_check_mark:|Get all account balances|
|account/transactions|:exclamation:|Get all transactions history|
|account/transactions/{id}|:exclamation:|Get transaction by transaction ID|

Methods with :exclamation: only support default parameters. They will be functional when the script support additional parameters in the function. Check API Reference for default values: https://api.hitbtc.com

### 3. Bitsane
_In development_

## Roadmap
 - Support API Method parameters
 - Coinbase API
 - GDAX API
 - Bitfinex API

## Donation
 - BTC: 16hDsVgy6VFW2aW8w9z2pogbq5XThToswF
 - ETH: 0x212799fbd9CD3e273E0CB6761b1708B284477e5E
 - LTC: LQtecz6SAbRzJXEfDpNLz8AzkhWKY4qQyv
 - BCH: 13mT5ubjZUKTviGXDSVHxRkrrxDFzzUFd4

## Credits
Thanks to below projects, developing CryptoGAS can be done as fast as possible.
 - [bradjasper/ImportJSON](https://github.com/bradjasper/ImportJSON)
 - [Caligatio/jsSHA](https://github.com/Caligatio/jsSHA/)

## License
Apache 2.0 License
