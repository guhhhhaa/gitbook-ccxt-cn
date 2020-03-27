---
description: manual
---

# 手册

## 手册

## 总览 <a id="overview"></a>

ccxt库是可用的密码_交换_或交换类的集合。每个类为特定的密码交换实现公共和私有API。所有交换均从基本Exchange类派生，并共享一组通用方法。要从ccxt库访问特定的交换，您需要创建相应交换类的实例。支持的交换经常更新，并定期添加新的交换。

库的结构可以概述如下：



```text
User
    +-------------------------------------------------------------+
    |                            CCXT                             |
    +------------------------------+------------------------------+
    |            Public            |           Private            |
    +=============================================================+
    │                              .                              |
    │                    The Unified CCXT API                     |
    │                              .                              |
    |       loadMarkets            .           fetchBalance       |
    |       fetchMarkets           .            createOrder       |
    |       fetchCurrencies        .            cancelOrder       |
    |       fetchTicker            .             fetchOrder       |
    |       fetchTickers           .            fetchOrders       |
    |       fetchOrderBook         .        fetchOpenOrders       |
    |       fetchOHLCV             .      fetchClosedOrders       |
    |       fetchStatus            .          fetchMyTrades       |
    |       fetchTrades            .                deposit       |
    |                              .               withdraw       |
    │                              .                              |
    +=============================================================+
    │                              .                              |
    |                     Custom Exchange API                     |
    |         (Derived Classes And Their Implicit Methods)        |
    │                              .                              |
    |       publicGet...           .          privateGet...       |
    |       publicPost...          .         privatePost...       |
    |                              .          privatePut...       |
    |                              .       privateDelete...       |
    |                              .                   sign       |
    │                              .                              |
    +=============================================================+
    │                              .                              |
    |                      Base Exchange Class                    |
    │                              .                              |
    +=============================================================+
```

实现了所有交换的完整公共和私有HTTP REST API。[CCXT Pro](https://ccxt.pro/)提供了JavaScript，PHP，Python中的WebSocket和FIX实现，[CCXT Pro](https://ccxt.pro/)是CCXT的专业插件，支持WebSocket流。

* 交流交流
* 市场
* API方法/端点
* 市场数据
* 贸易

## 交流交流 <a id="exchanges"></a>

CCXT库当前支持以下121个加密货币交易市场和交易API：

| 商标 | ID | 名称 | 看 | doc | 认证的 | 亲 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ​[​![\_1btcxe](https://user-images.githubusercontent.com/1294454/27766049-2b294408-5ecc-11e7-85cc-adaff013dc1a.jpg)​](https://1btcxe.com/)​ | \_1btcxe | [1BTCXE](https://1btcxe.com/) | \* | [API](https://1btcxe.com/api-docs.php) | ​ | ​ |
| ​[​![acx](https://user-images.githubusercontent.com/1294454/30247614-1fe61c74-9621-11e7-9e8c-f1a627afa279.jpg)​](https://acx.io/)​ | acx | [ACX](https://acx.io/) | 2 | [API](https://acx.io/documents/api_v2) | ​ | ​ |
| ​[​![&#x4E09;&#x6708;](https://user-images.githubusercontent.com/1294454/49189583-0466a780-f380-11e8-9248-57a631aad2d6.jpg)​](https://adara.io/)​ | 三月 | [三月](https://adara.io/) | 1个 | [API](https://api.adara.io/v1) | ​ | ​ |
| ​[​![Anxpro](https://user-images.githubusercontent.com/1294454/27765983-fd8595da-5ec9-11e7-82e3-adb3ab8c2612.jpg)​](https://anxpro.com/)​ | Anxpro | [ANXPro](https://anxpro.com/) | \* | [API](https://anxv2.docs.apiary.io/) | ​ | ​ |
| ​[​![ce](https://user-images.githubusercontent.com/51840849/77231516-851c6900-6bac-11ea-8fd6-ee5c23eddbd4.jpg)​](https://www.bcex.top/register?invite_code=758978&lang=en)​ | ce | [BCEX](https://www.bcex.top/register?invite_code=758978&lang=en) | 1个 | [API](https://github.com/BCEX-TECHNOLOGY-LIMITED/API_Docs/wiki/Interface) | ​ | ​ |
| ​[​![bequaem](https://user-images.githubusercontent.com/1294454/55248342-a75dfe00-525a-11e9-8aa2-05e9dca943c6.jpg)​](https://bequant.io/)​ | bequaem | [bequaem](https://bequant.io/) | 2 | [API](https://api.bequant.io/) | ​ | ​ |
| ​[​![bibox](https://user-images.githubusercontent.com/51840849/77257418-3262b000-6c85-11ea-8fb8-20bdf20b3592.jpg)​](https://w2.bibox.com/login/register?invite_code=05Kj3I)​ | bibox | [Bibox](https://w2.bibox.com/login/register?invite_code=05Kj3I) | 1个 | [API](https://biboxcom.github.io/en/) | ​ | ​ |
| ​[​![&#x6BD4;&#x683C;](https://user-images.githubusercontent.com/1294454/69354403-1d532180-0c91-11ea-88ed-44c06cefdf87.jpg)​](https://b1.run/users/new?code=D3LLBVFT)​ | 比格 | [bigone](https://b1.run/users/new?code=D3LLBVFT) | 3 | [API](https://open.big.one/docs/api.html) | ​ | ​ |
| ​[​![&#x5E01;&#x5B89;](https://user-images.githubusercontent.com/1294454/29604020-d5483cdc-87ee-11e7-94c7-d1a8d9169293.jpg)​](https://www.binance.com/?ref=10205187)​ | 币安 | [Binance](https://www.binance.com/?ref=10205187) | \* | [API](https://binance-docs.github.io/apidocs/spot/en) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x8FFD;&#x968F;](https://user-images.githubusercontent.com/1294454/54874009-d526eb00-4df3-11e9-928c-ce6a2b914cd1.jpg)​](https://www.binance.je/?ref=35047921)​ | 追随 | [Binance泽西](https://www.binance.je/?ref=35047921) | \* | [API](https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![Binanceus](https://user-images.githubusercontent.com/1294454/65177307-217b7c80-da5f-11e9-876e-0b748ba0a358.jpg)​](https://www.binance.us/?ref=35005074)​ | Binanceus | [Binance美国](https://www.binance.us/?ref=35005074) | \* | [API](https://github.com/binance-us/binance-official-api-docs) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![bit2c](https://user-images.githubusercontent.com/1294454/27766119-3593220e-5ece-11e7-8b3a-5a041f6bcc3f.jpg)​](https://bit2c.co.il/Aff/63bfed10-e359-420c-ab5a-ad368dab0baf)​ | bit2c | [Bit2C](https://bit2c.co.il/Aff/63bfed10-e359-420c-ab5a-ad368dab0baf) | \* | [API](https://www.bit2c.co.il/home/api) | ​ | ​ |
| ​[​![&#x4F4D;&#x5E93;](https://user-images.githubusercontent.com/1294454/37808081-b87f2d9c-2e59-11e8-894d-c1900b7584fe.jpg)​](https://bitbank.cc/)​ | 位库 | [bitbank](https://bitbank.cc/) | 1个 | [API](https://docs.bitbank.cc/) | ​ | ​ |
| ​[​![bitbay](https://user-images.githubusercontent.com/1294454/27766132-978a7bd8-5ece-11e7-9540-bc96d1e9bbb8.jpg)​](https://auth.bitbay.net/ref/jHlbB4mIkdS1)​ | bitbay | [bitbay](https://auth.bitbay.net/ref/jHlbB4mIkdS1) | \* | [API](https://bitbay.net/public-api) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;&#x5E01;](https://user-images.githubusercontent.com/1294454/27766244-e328a50c-5ed2-11e7-947b-041416579bb3.jpg)​](https://www.bitfinex.com/?refcode=P61eYxFL)​ | 比特币 | [Bitfinex](https://www.bitfinex.com/?refcode=P61eYxFL) | 1个 | [API](https://docs.bitfinex.com/v1/docs) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![bitfinex2](https://user-images.githubusercontent.com/1294454/27766244-e328a50c-5ed2-11e7-947b-041416579bb3.jpg)​](https://www.bitfinex.com/?refcode=P61eYxFL)​ | bitfinex2 | [Bitfinex](https://www.bitfinex.com/?refcode=P61eYxFL) | 2 | [API](https://docs.bitfinex.com/v2/docs/) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;&#x98DE;](https://user-images.githubusercontent.com/1294454/28051642-56154182-660e-11e7-9b0d-6042d1e6edd8.jpg)​](https://bitflyer.jp/)​ | 比特飞 | [bitFlyer](https://bitflyer.jp/) | 1个 | [API](https://lightning.bitflyer.com/docs?lang=en) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;&#x5916;&#x6C47;](https://user-images.githubusercontent.com/1294454/44310033-69e9e600-a3d8-11e8-873d-54d74d1bc4e4.jpg)​](https://www.bitforex.com/en/invitationRegister?inviterId=1867438)​ | 比特外汇 | [Bitforex](https://www.bitforex.com/en/invitationRegister?inviterId=1867438) | 1个 | [API](https://github.com/githubdev2020/API_Doc_en/wiki) | ​ | ​ |
| ​[​![bithumb](https://user-images.githubusercontent.com/1294454/30597177-ea800172-9d5e-11e7-804c-b9d4fa9b56b0.jpg)​](https://www.bithumb.com/)​ | bithumb | [Bithumb](https://www.bithumb.com/) | \* | [API](https://apidocs.bithumb.com/) | ​ | ​ |
| ​[​![bitkk](https://user-images.githubusercontent.com/1294454/32859187-cd5214f0-ca5e-11e7-967d-96568e2e2bd1.jpg)​](https://www.bitkk.com/)​ | bitkk | [bitkk](https://www.bitkk.com/) | 1个 | [API](https://www.bitkk.com/i/developer) | ​ | ​ |
| ​[​![bitlish](https://user-images.githubusercontent.com/1294454/27766275-dcfc6c30-5ed3-11e7-839d-00a846385d0b.jpg)​](https://bitlish.com/)​ | bitlish | [Bitlish](https://bitlish.com/) | 1个 | [API](https://bitlish.com/api) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;&#x739B;](https://user-images.githubusercontent.com/1294454/61835713-a2662f80-ae85-11e9-9d00-6442919701fd.jpg)​](http://www.bitmart.com/?r=rQCFLh)​ | 比特玛 | [BitMart](http://www.bitmart.com/?r=rQCFLh) | 2 | [API](https://github.com/bitmartexchange/bitmart-official-api-docs) | ​ | ​ |
| ​[​![&#x6700;&#x5927;&#x4F4D;](https://user-images.githubusercontent.com/1294454/66820319-19710880-ef49-11e9-8fbe-16be62a11992.jpg)​](https://bitmax.io/#/register?inviteCode=EL6BXBQM)​ | 最大位 | [BitMax](https://bitmax.io/#/register?inviteCode=EL6BXBQM) | 1个 | [API](https://github.com/bitmax-exchange/api-doc/blob/master/bitmax-api-doc-v1.2.md) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;&#x5E01;](https://user-images.githubusercontent.com/1294454/27766319-f653c6e6-5ed4-11e7-933d-f0bc3699ae8f.jpg)​](https://www.bitmex.com/register/upZpOX)​ | 比特币 | [BitMEX](https://www.bitmex.com/register/upZpOX) | 1个 | [API](https://www.bitmex.com/app/apiOverview) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x540D;](https://user-images.githubusercontent.com/1294454/27766335-715ce7aa-5ed5-11e7-88a8-173a27bb30fe.jpg)​](https://bitso.com/?ref=itej)​ | 名 | [Bitso](https://bitso.com/?ref=itej) | 3 | [API](https://bitso.com/api_info) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;&#x6233;](https://user-images.githubusercontent.com/1294454/27786377-8c8ab57e-5fe9-11e7-8ea4-2b05b6bcceec.jpg)​](https://www.bitstamp.net/)​ | 比特戳 | [Bitstamp](https://www.bitstamp.net/) | 2 | [API](https://www.bitstamp.net/api) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6BD4;&#x7279;&#x6233;1](https://user-images.githubusercontent.com/1294454/27786377-8c8ab57e-5fe9-11e7-8ea4-2b05b6bcceec.jpg)​](https://www.bitstamp.net/)​ | 比特戳1 | [Bitstamp](https://www.bitstamp.net/) | 1个 | [API](https://www.bitstamp.net/api) | ​ | ​ |
| ​[​![Bittrex](https://user-images.githubusercontent.com/1294454/27766352-cf0b3c26-5ed5-11e7-82b7-f3826b7a97d8.jpg)​](https://bittrex.com/Account/Register?referralCode=1ZE-G0G-M3B)​ | Bittrex | [Bittrex](https://bittrex.com/Account/Register?referralCode=1ZE-G0G-M3B) | 1.1 | [API](https://bittrex.github.io/api/) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6BD4;&#x5179;](https://user-images.githubusercontent.com/1294454/35862606-4f554f14-0b5d-11e8-957d-35058c504b6f.jpg)​](https://u.bitz.com/register?invite_code=1429193)​ | 比兹 | [位-Z](https://u.bitz.com/register?invite_code=1429193) | 2 | [API](https://apidoc.bitz.com/en/) | ​ | ​ |
| ​[​![BL3P](https://user-images.githubusercontent.com/1294454/28501752-60c21b82-6feb-11e7-818b-055ee6d0e754.jpg)​](https://bl3p.eu/)​ | BL3P | [BL3P](https://bl3p.eu/) | 1个 | [API](https://github.com/BitonicNL/bl3p-api/tree/master/docs) | ​ | ​ |
| ​[​![Bleutrade](https://user-images.githubusercontent.com/1294454/30303000-b602dbe6-976d-11e7-956d-36c5049c01e7.jpg)​](https://bleutrade.com/)​ | Bleutrade | [Bleutrade](https://bleutrade.com/) | \* | [API](https://app.swaggerhub.com/apis-docs/bleu/white-label/3.0.0) | ​ | ​ |
| ​[​![&#x5DF4;&#x897F;&#x7684;](https://user-images.githubusercontent.com/1294454/34703593-c4498674-f504-11e7-8d14-ff8e44fb78c1.jpg)​](https://braziliex.com/?ref=5FE61AB6F6D67DA885BC98BA27223465)​ | 巴西的 | [Braziliex](https://braziliex.com/?ref=5FE61AB6F6D67DA885BC98BA27223465) | \* | [API](https://braziliex.com/exchange/api.php) | ​ | ​ |
| ​[​![btcalpha](https://user-images.githubusercontent.com/1294454/42625213-dabaa5da-85cf-11e8-8f99-aa8f8f7699f0.jpg)​](https://btc-alpha.com/?r=123788)​ | btcalpha | [BTC-阿尔法](https://btc-alpha.com/?r=123788) | 1个 | [API](https://btc-alpha.github.io/api-docs) | ​ | ​ |
| ​[​![btcbox](https://user-images.githubusercontent.com/1294454/31275803-4df755a8-aaa1-11e7-9abb-11ec2fad9f2d.jpg)​](https://www.btcbox.co.jp/)​ | btcbox | [BtcBox](https://www.btcbox.co.jp/) | 1个 | [API](https://www.btcbox.co.jp/help/asm) | ​ | ​ |
| ​[​![btcmarkets](https://user-images.githubusercontent.com/1294454/29142911-0e1acfc2-7d5c-11e7-98c4-07d9532b29d7.jpg)​](https://btcmarkets.net/)​ | btcmarkets | [BTC市场](https://btcmarkets.net/) | \* | [API](https://github.com/BTCMarkets/API) | ​ | ​ |
| ​[​![btctradeim](https://user-images.githubusercontent.com/1294454/36770531-c2142444-1c5b-11e8-91e2-a4d90dc85fe8.jpg)​](https://m.baobi.com/invite?inv=1765b2)​ | btctradeim | [BtcTrade.im](https://m.baobi.com/invite?inv=1765b2) | \* | [API](https://www.btctrade.im/help.api.html) | ​ | ​ |
| ​[​![btctradeua](https://user-images.githubusercontent.com/1294454/27941483-79fc7350-62d9-11e7-9f61-ac47f28fcd96.jpg)​](https://btc-trade.com.ua/registration/22689)​ | btctradeua | [BTC贸易](https://btc-trade.com.ua/registration/22689) | \* | [API](https://docs.google.com/document/d/1ocYA0yMy_RXd561sfG3qEPZ80kyll36HUxvCRe5GbhE/edit) | ​ | ​ |
| ​[​![btcturk](https://user-images.githubusercontent.com/1294454/27992709-18e15646-64a3-11e7-9fa2-b0950ec7712f.jpg)​](https://www.btcturk.com/)​ | btcturk | [BTCTurk](https://www.btcturk.com/) | \* | [API](https://github.com/BTCTrader/broker-api-docs) | ​ | ​ |
| ​[​![buda](https://user-images.githubusercontent.com/1294454/47380619-8a029200-d706-11e8-91e0-8a391fe48de3.jpg)​](https://www.buda.com/)​ | buda | ​[Buda](https://www.buda.com/)​ | 2 | [API](https://api.buda.com/) | ​ | ​ |
| ​[​![&#x4F53;&#x91CD;](https://user-images.githubusercontent.com/1294454/69436317-31128c80-0d52-11ea-91d1-eb7bb5818812.jpg)​](https://www.bw.com/)​ | 体重 | [BW](https://www.bw.com/) | 1个 | [API](https://github.com/bw-exchange/api_docs_en/wiki) | ​ | ​ |
| ​[​![&#x7ED5;&#x884C;](https://user-images.githubusercontent.com/51840849/76547799-daff5b80-649e-11ea-87fb-3be9bac08954.jpg)​](https://www.bybit.com/app/register?ref=X7Prm)​ | 绕行 | [Bybit](https://www.bybit.com/app/register?ref=X7Prm) | 2 | [API](https://bybit-exchange.github.io/docs/inverse/) | ​ | ​ |
| ​[​![&#x5B57;&#x8282;&#x919A;&#x5316;](https://user-images.githubusercontent.com/1294454/67288762-2f04a600-f4e6-11e9-9fd6-c60641919491.jpg)​](https://www.bytetrade.com/)​ | 字节醚化 | [掉期交易](https://www.bytetrade.com/) | \* | [API](https://github.com/Bytetrade/bytetrade-official-api-docs/wiki) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​ |
| ​[​![&#x585E;&#x514B;&#x65AF;](https://user-images.githubusercontent.com/1294454/27766442-8ddc33b0-5ed8-11e7-8b98-f786aef0f3c9.jpg)​](https://cex.io/r/0/up105393824/0/)​ | 塞克斯 | [CEX.IO](https://cex.io/r/0/up105393824/0/) | \* | [API](https://cex.io/cex-api) | ​ | ​ |
| ​[​![&#x8FA3;&#x6912;](https://user-images.githubusercontent.com/1294454/27991414-1298f0d8-647f-11e7-9c40-d56409266336.jpg)​](https://chilebit.net/)​ | 辣椒 | [ChileBit](https://chilebit.net/) | 1个 | [API](https://blinktrade.com/docs) | ​ | ​ |
| ​[​![&#x8054;&#x5408;](https://user-images.githubusercontent.com/1294454/35755576-dee02e5c-0878-11e8-989f-1595d80ba47f.jpg)​](https://cobinhood.com/?referrerId=a9d57842-99bb-4d7c-b668-0479a15a458b)​ | 联合 | [COBINHOOD](https://cobinhood.com/?referrerId=a9d57842-99bb-4d7c-b668-0479a15a458b) | 1个 | [API](https://cobinhood.github.io/api-public) | ​ | ​ |
| ​[​![&#x5E01;&#x5E93;](https://user-images.githubusercontent.com/1294454/40811661-b6eceae2-653a-11e8-829e-10bfadb078cf.jpg)​](https://www.coinbase.com/join/58cbe25a355148797479dbd2)​ | 币库 | [Coinbase](https://www.coinbase.com/join/58cbe25a355148797479dbd2) | 2 | [API](https://developers.coinbase.com/api/v2) | ​ | ​ |
| ​[​![&#x539F;&#x59CB;&#x8D27;&#x5E01;](https://user-images.githubusercontent.com/1294454/44539184-29f26e00-a70c-11e8-868f-e907fc236a7c.jpg)​](https://prime.coinbase.com/)​ | 原始货币 | [总理Coinbase](https://prime.coinbase.com/) | \* | [API](https://docs.prime.coinbase.com/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![coinbasepro](https://user-images.githubusercontent.com/1294454/41764625-63b7ffde-760a-11e8-996d-a6328fa9347a.jpg)​](https://pro.coinbase.com/)​ | coinbasepro | [Coinbase临](https://pro.coinbase.com/) | \* | [API](https://docs.pro.coinbase.com/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6295;&#x5E01;&#x652F;&#x7968;](https://user-images.githubusercontent.com/1294454/27766464-3b5c3c74-5ed9-11e7-840e-31b32968e1da.jpg)​](https://coincheck.com/)​ | 投币支票 | [coincheck](https://coincheck.com/) | \* | [API](https://coincheck.com/documents/exchange/api) | ​ | ​ |
| ​[​![&#x79D1;&#x6D85;&#x683C;](https://user-images.githubusercontent.com/1294454/36770310-adfa764e-1c5a-11e8-8e09-449daac3d2fb.jpg)​](https://www.coinegg.com/user/register?invite=523218)​ | 科涅格 | [CoinEgg](https://www.coinegg.com/user/register?invite=523218) | \* | [API](https://www.coinegg.com/explain.api.html) | ​ | ​ |
| ​[​![Coinex](https://user-images.githubusercontent.com/1294454/38046312-0b450aac-32c8-11e8-99ab-bc6b136b6cc7.jpg)​](https://www.coinex.com/register?refer_code=yw5fz)​ | Coinex | [CoinEx](https://www.coinex.com/register?refer_code=yw5fz) | 1个 | [API](https://github.com/coinexcom/coinex_exchange_api/wiki) | ​ | ​ |
| ​[​![&#x730E;&#x9E70;](https://user-images.githubusercontent.com/1294454/41822275-ed982188-77f5-11e8-92bb-496bcd14ca52.jpg)​](https://coinfalcon.com/?ref=CFJSVGTUPASB)​ | 猎鹰 | [CoinFalcon](https://coinfalcon.com/?ref=CFJSVGTUPASB) | 1个 | [API](https://docs.coinfalcon.com/) | ​ | ​ |
| ​[​![&#x5730;&#x677F;](https://user-images.githubusercontent.com/1294454/28246081-623fc164-6a1c-11e7-913f-bac0d5576c90.jpg)​](https://www.coinfloor.co.uk/)​ | 地板 | [coinfloor](https://www.coinfloor.co.uk/) | \* | [API](https://github.com/coinfloor/api) | ​ | ​ |
| ​[​![COING](https://user-images.githubusercontent.com/1294454/28619707-5c9232a8-7212-11e7-86d6-98fe5d15cc6e.jpg)​](https://www.coingi.com/?r=XTPPMC)​ | COING | [COING](https://www.coingi.com/?r=XTPPMC) | \* | [API](https://coingi.docs.apiary.io/) | ​ | ​ |
| ​[​![&#x6295;&#x5E01;&#x5E02;&#x573A;](https://user-images.githubusercontent.com/1294454/28244244-9be6312a-69ed-11e7-99c1-7c1797275265.jpg)​](https://coinmarketcap.com/)​ | 投币市场 | [CoinMarketCap](https://coinmarketcap.com/) | 1个 | [API](https://coinmarketcap.com/api) | ​ | ​ |
| ​[​![&#x5171;&#x540C;&#x7684;](https://user-images.githubusercontent.com/1294454/27811229-c1efb510-606c-11e7-9a36-84ba2ce412d8.jpg)​](https://coinmate.io/?referral=YTFkM1RsOWFObVpmY1ZjMGREQmpTRnBsWjJJNVp3PT0)​ | 共同的 | [CoinMate](https://coinmate.io/?referral=YTFkM1RsOWFObVpmY1ZjMGREQmpTRnBsWjJJNVp3PT0) | \* | [API](https://coinmate.docs.apiary.io/) | ​ | ​ |
| ​[​![&#x53EF;&#x53EF;&#x916E;](https://user-images.githubusercontent.com/1294454/38003300-adc12fba-323f-11e8-8525-725f53c4a659.jpg)​](https://coinone.co.kr/)​ | 可可酮 | [CoinOne](https://coinone.co.kr/) | 2 | [API](https://doc.coinone.co.kr/) | ​ | ​ |
| ​[​![&#x786C;&#x5E01;&#x7F50;](https://user-images.githubusercontent.com/1294454/28208429-3cacdf9a-6896-11e7-854e-4c79a772a30f.jpg)​](https://www.coinspot.com.au/register?code=PJURCU)​ | 硬币罐 | [CoinSpot](https://www.coinspot.com.au/register?code=PJURCU) | \* | [API](https://www.coinspot.com.au/api) | ​ | ​ |
| ​[​![&#x9177;&#x5E01;](https://user-images.githubusercontent.com/1294454/36770529-be7b1a04-1c5b-11e8-9600-d11f1996b539.jpg)​](https://www.coolcoin.com/user/register?invite_code=bhaega)​ | 酷币 | [CoolCoin](https://www.coolcoin.com/user/register?invite_code=bhaega) | \* | [API](https://www.coolcoin.com/help.api.html) | ​ | ​ |
| ​[​![coss](https://user-images.githubusercontent.com/1294454/50328158-22e53c00-0503-11e9-825c-c5cfd79bfa74.jpg)​](https://www.coss.io/c/reg?r=OWCMHQVW2Q)​ | coss | [COSS](https://www.coss.io/c/reg?r=OWCMHQVW2Q) | 1个 | [API](https://api.coss.io/v1/spec) | ​ | ​ |
| ​[​![crex24](https://user-images.githubusercontent.com/1294454/47813922-6f12cc00-dd5d-11e8-97c6-70f957712d47.jpg)​](https://crex24.com/?refid=slxsjsjtil8xexl9hksr)​ | crex24 | [CREX24](https://crex24.com/?refid=slxsjsjtil8xexl9hksr) | 2 | [API](https://docs.crex24.com/trade-api/v2) | ​ | ​ |
| ​[​![&#x5FB7;&#x91CC;&#x5E03;](https://user-images.githubusercontent.com/1294454/41933112-9e2dd65a-798b-11e8-8440-5bab2959fcb8.jpg)​](https://www.deribit.com/reg-1189.4038)​ | 德里布 | [德里布](https://www.deribit.com/reg-1189.4038) | 2 | [API](https://docs.deribit.com/v2) | ​ | ​ |
| ​[​![digifinex](https://user-images.githubusercontent.com/1294454/62184319-304e8880-b366-11e9-99fe-8011d6929195.jpg)​](https://www.digifinex.vip/en-ww/from/DhOzBg/3798****5114)​ | digifinex | [DigiFinex](https://www.digifinex.vip/en-ww/from/DhOzBg/3798****5114) | 3 | [API](https://docs.digifinex.vip/) | ​ | ​ |
| ​[​![dsx](https://user-images.githubusercontent.com/51840849/76909626-cb2bb100-68bc-11ea-99e0-28ba54f04792.jpg)​](https://dsx.uk/)​ | dsx | [DSX](https://dsx.uk/) | 3 | [API](https://dsx.uk/developers/publicApi) | ​ | ​ |
| ​[​![&#x5BA3;&#x4F20;&#x7247;](https://user-images.githubusercontent.com/1294454/27766491-1b0ea956-5eda-11e7-9225-40d67b481b8d.jpg)​](https://exmo.me/?ref=131685)​ | 宣传片 | [议员](https://exmo.me/?ref=131685) | 1个 | [API](https://exmo.me/en/api_doc?ref=131685) | ​ | ​ |
| ​[​![exx](https://user-images.githubusercontent.com/1294454/37770292-fbf613d0-2de4-11e8-9f79-f2dc451b8ccb.jpg)​](https://www.exx.com/r/fde4260159e53ab8a58cc9186d35501f?recommQd=1)​ | exx | [EXX](https://www.exx.com/r/fde4260159e53ab8a58cc9186d35501f?recommQd=1) | \* | [API](https://www.exx.com/help/restApi) | ​ | ​ |
| ​[​![fcoin](https://user-images.githubusercontent.com/1294454/42244210-c8c42e1e-7f1c-11e8-8710-a5fb63b165c4.jpg)​](https://www.fcoin.com/i/Z5P7V)​ | fcoin | [签约](https://www.fcoin.com/i/Z5P7V) | 2 | [API](https://developer.fcoin.com/) | ​ | ​ |
| ​[​![fcoinjp](https://user-images.githubusercontent.com/1294454/54219174-08b66b00-4500-11e9-862d-f522d0fe08c6.jpg)​](https://www.fcoinjp.com/)​ | fcoinjp | [FCoinJP](https://www.fcoinjp.com/) | 2 | [API](https://developer.fcoin.com/) | ​ | ​ |
| ​[​![&#x6D41;&#x52A8;&#x6027;](https://user-images.githubusercontent.com/1294454/28162465-cd815d4c-67cf-11e7-8e57-438bea0523a2.jpg)​](https://www.flowbtc.com.br/)​ | 流动性 | [flowBTC](https://www.flowbtc.com.br/) | 1个 | [API](https://www.flowbtc.com.br/api.html) | ​ | ​ |
| ​[​![&#x72D0;&#x72F8;](https://user-images.githubusercontent.com/1294454/27991413-11b40d42-647f-11e7-91ee-78ced874dd09.jpg)​](https://foxbit.com.br/exchange)​ | 狐狸 | [FoxBit](https://foxbit.com.br/exchange) | 1个 | [API](https://foxbit.com.br/api/) | ​ | ​ |
| ​[​![FTX](https://user-images.githubusercontent.com/1294454/67149189-df896480-f2b0-11e9-8816-41593e17f9ec.jpg)​](https://ftx.com/#a=1623029)​ | FTX | [FTX](https://ftx.com/#a=1623029) | \* | [API](https://github.com/ftexchange/ftx) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​ |
| ​[​![fybse](https://user-images.githubusercontent.com/1294454/27766512-31019772-5edb-11e7-8241-2e675e6797f1.jpg)​](https://www.fybse.se/)​ | fybse | [FYB-SE](https://www.fybse.se/) | \* | [API](https://fyb.docs.apiary.io/) | ​ | ​ |
| ​[​![Gateio](https://user-images.githubusercontent.com/1294454/31784029-0313c702-b509-11e7-9ccc-bc0da6a0e435.jpg)​](https://www.gate.io/signup/2436035)​ | Gateio | [Gate.io](https://www.gate.io/signup/2436035) | 2 | [API](https://gate.io/api2) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x53CC;&#x5B50;&#x5EA7;](https://user-images.githubusercontent.com/1294454/27816857-ce7be644-6096-11e7-82d6-3c257263229c.jpg)​](https://gemini.com/)​ | 双子座 | [双子座](https://gemini.com/) | 1个 | [API](https://docs.gemini.com/rest-api) | ​ | ​ |
| ​[​![Hitbtc](https://user-images.githubusercontent.com/1294454/27766555-8eaec20e-5edc-11e7-9c5b-6dc69fc42f5e.jpg)​](https://hitbtc.com/?ref_id=5a5d39a65d466)​ | Hitbtc | [HitBTC](https://hitbtc.com/?ref_id=5a5d39a65d466) | 1个 | [API](https://github.com/hitbtc-com/hitbtc-api/blob/master/APIv1.md) | ​ | ​ |
| ​[​![hitbtc2](https://user-images.githubusercontent.com/1294454/27766555-8eaec20e-5edc-11e7-9c5b-6dc69fc42f5e.jpg)​](https://hitbtc.com/?ref_id=5a5d39a65d466)​ | hitbtc2 | [HitBTC](https://hitbtc.com/?ref_id=5a5d39a65d466) | 2 | [API](https://api.hitbtc.com/) | ​ | ​ |
| ​[​![&#x970D;&#x83B1;&#x514B;&#x65AF;](https://user-images.githubusercontent.com/1294454/75841031-ca375180-5ddd-11ea-8417-b975674c23cb.jpg)​](https://pro.hollaex.com/signup?affiliation_code=QSWA6G)​ | 霍莱克斯 | [HollaEx](https://pro.hollaex.com/signup?affiliation_code=QSWA6G) | 1个 | [API](https://apidocs.hollaex.com/) | ​ | ​ |
| ​[​![huobipro](https://user-images.githubusercontent.com/1294454/76137448-22748a80-604e-11ea-8069-6e389271911d.jpg)​](https://www.huobi.co/en-us/topic/invited/?invite_code=rwrd3)​ | huobipro | ​[Huobi Pro](https://www.huobi.co/en-us/topic/invited/?invite_code=rwrd3)​ | 1个 | [API](https://huobiapi.github.io/docs/spot/v1/cn/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![huobiru](https://user-images.githubusercontent.com/1294454/52978816-e8552e00-33e3-11e9-98ed-845acfece834.jpg)​](https://www.huobi.com.ru/invite?invite_code=esc74)​ | huobiru | ​[Huobi Russia](https://www.huobi.com.ru/invite?invite_code=esc74)​ | 1个 | [API](https://github.com/cloudapidoc/API_Docs_en) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![ice3x](https://user-images.githubusercontent.com/1294454/38012176-11616c32-3269-11e8-9f05-e65cf885bb15.jpg)​](https://ice3x.com/?ref=14341802)​ | ice3x | [ICE3X](https://ice3x.com/?ref=14341802) | 1个 | [API](https://ice3x.co.za/ice-cubed-bitcoin-exchange-api-documentation-1-june-2017) | ​ | ​ |
| ​[​![&#x89C2;&#x5FF5;](https://user-images.githubusercontent.com/1294454/63693236-3415e380-c81c-11e9-8600-ba1634f1407d.jpg)​](https://idex.market/)​ | 观念 | [IDEX](https://idex.market/) | \* | [API](https://docs.idex.market/) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​ |
| ​[​![&#x72EC;&#x7ACB;&#x50A8;&#x5907;](https://user-images.githubusercontent.com/1294454/30521662-cf3f477c-9bcb-11e7-89bc-d1ac85012eda.jpg)​](https://www.independentreserve.com/)​ | 独立储备 | [独立储量](https://www.independentreserve.com/) | \* | [API](https://www.independentreserve.com/API) | ​ | ​ |
| ​[​![x](https://user-images.githubusercontent.com/1294454/37443283-2fddd0e4-281c-11e8-9741-b4f1419001b5.jpg)​](https://indodax.com/ref/testbitcoincoid/1)​ | x | [INDODAX](https://indodax.com/ref/testbitcoincoid/1) | 1.8 | [API](https://indodax.com/downloads/BITCOINCOID-API-DOCUMENTATION.pdf) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;](https://user-images.githubusercontent.com/1294454/27822159-66153620-60ad-11e7-89e7-005f6d7f3de0.jpg)​](https://www.itbit.com/)​ | 比特 | [itBit](https://www.itbit.com/) | 1个 | [API](https://api.itbit.com/docs) | ​ | ​ |
| ​[​![ex](https://user-images.githubusercontent.com/1294454/47401462-2e59f800-d74a-11e8-814f-e4ae17b4968a.jpg)​](https://kkex.com/)​ | ex | [KKEX](https://kkex.com/) | 2 | [API](https://kkex.com/api_wiki/cn/) | ​ | ​ |
| ​[​![&#x6D77;&#x5996;](https://user-images.githubusercontent.com/51840849/76173629-fc67fb00-61b1-11ea-84fe-f2de582f58a3.jpg)​](https://www.kraken.com/)​ | 海妖 | [鲲](https://www.kraken.com/) | 0 | [API](https://www.kraken.com/features/api) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x9177;&#x5E01;](https://user-images.githubusercontent.com/1294454/57369448-3cc3aa80-7196-11e9-883e-5ebeb35e4f57.jpg)​](https://www.kucoin.com/?rcode=E5wkqe)​ | 酷币 | [KuCoin](https://www.kucoin.com/?rcode=E5wkqe) | 2 | [API](https://docs.kucoin.com/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x4ECE;](https://user-images.githubusercontent.com/1294454/31697638-912824fa-b3c1-11e7-8c36-cf9606eb94ac.jpg)​](https://kuna.io/?r=kunaid-gvfihe8az7o4)​ | 从 | [因为](https://kuna.io/?r=kunaid-gvfihe8az7o4) | 2 | [API](https://kuna.io/documents/api) | ​ | ​ |
| ​[​![Lakebtc](https://user-images.githubusercontent.com/1294454/28074120-72b7c38a-6660-11e7-92d9-d9027502281d.jpg)​](https://www.lakebtc.com/)​ | Lakebtc | [LakeBTC](https://www.lakebtc.com/) | 2 | [API](https://www.lakebtc.com/s/api_v2) | ​ | ​ |
| ​[​![&#x62C9;&#x6258;&#x80AF;](https://user-images.githubusercontent.com/1294454/61511972-24c39f00-aa01-11e9-9f7c-471f1d6e5214.jpg)​](https://latoken.com/)​ | 拉托肯 | [Latoken](https://latoken.com/) | 1个 | [API](https://api.latoken.com/) | ​ | ​ |
| ​[​![lbank](https://user-images.githubusercontent.com/1294454/38063602-9605e28a-3302-11e8-81be-64b1e53c4cfb.jpg)​](https://www.lbex.io/invite?icode=7QCY)​ | lbank | [LBank](https://www.lbex.io/invite?icode=7QCY) | 1个 | [API](https://github.com/LBank-exchange/lbank-official-api-docs) | ​ | ​ |
| ​[​![&#x6DB2;&#x4F53;](https://user-images.githubusercontent.com/1294454/45798859-1a872600-bcb4-11e8-8746-69291ce87b04.jpg)​](https://www.liquid.com/?affiliate=SbzC62lt30976)​ | 液体 | [液体](https://www.liquid.com/?affiliate=SbzC62lt30976) | 2 | [API](https://developers.liquid.com/) | ​ | ​ |
| ​[​![&#x6D3B;&#x5E01;](https://user-images.githubusercontent.com/1294454/27980768-f22fc424-638a-11e7-89c9-6010a54ff9be.jpg)​](https://livecoin.net/?from=Livecoin-CQ1hfx44)​ | 活币 | [LiveCoin](https://livecoin.net/?from=Livecoin-CQ1hfx44) | \* | [API](https://www.livecoin.net/api?lang=en) | ​ | ​ |
| ​[​![&#x6708;&#x4EAE;](https://user-images.githubusercontent.com/1294454/27766607-8c1a69d8-5ede-11e7-930c-540b5eb9be24.jpg)​](https://www.luno.com/invite/44893A)​ | 月亮 | [月亮](https://www.luno.com/invite/44893A) | 1个 | [API](https://www.luno.com/en/api) | ​ | ​ |
| ​[​![&#x5E78;&#x798F;](https://user-images.githubusercontent.com/1294454/34487620-3139a7b0-efe6-11e7-90f5-e520cef74451.jpg)​](https://www.lykke.com/)​ | 幸福 | [幸福](https://www.lykke.com/) | 1个 | [API](https://hft-api.lykke.com/swagger/ui/) | ​ | ​ |
| ​[​![&#x5E02;&#x573A;](https://user-images.githubusercontent.com/1294454/27837060-e7c58714-60ea-11e7-9192-f05e86adb83f.jpg)​](https://www.mercadobitcoin.com.br/)​ | 市场 | [比特币市场](https://www.mercadobitcoin.com.br/) | 3 | [API](https://www.mercadobitcoin.com.br/api-doc) | ​ | ​ |
| ​[​![&#x6DF7;&#x5408;&#x5E01;](https://user-images.githubusercontent.com/1294454/30237212-ed29303c-9535-11e7-8af8-fcd381cfa20c.jpg)​](https://mixcoins.com/)​ | 混合币 | [MixCoins](https://mixcoins.com/) | 1个 | [API](https://mixcoins.com/help/api/) | ​ | ​ |
| ​[​![Oceanex](https://user-images.githubusercontent.com/1294454/58385970-794e2d80-8001-11e9-889c-0567cd79b78e.jpg)​](https://oceanex.pro/signup?referral=VE24QX)​ | Oceanex | [OceanEx](https://oceanex.pro/signup?referral=VE24QX) | 1个 | [API](https://api.oceanex.pro/doc/v1) | ​ | ​ |
| ​[​![okcoin](https://user-images.githubusercontent.com/1294454/27766791-89ffb502-5ee5-11e7-8a5b-c5950b68ac65.jpg)​](https://www.okcoin.com/account/register?flag=activity&channelId=600001513)​ | okcoin | [OKCoin](https://www.okcoin.com/account/register?flag=activity&channelId=600001513) | 3 | [API](https://www.okcoin.com/docs/en/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x5965;&#x514B;&#x65AF;](https://user-images.githubusercontent.com/1294454/32552768-0d6dd3c6-c4a6-11e7-90f8-c043b64756a7.jpg)​](https://www.okex.com/join/1888677)​ | 奥克斯 | [OKEX](https://www.okex.com/join/1888677) | 3 | [API](https://www.okex.com/docs/en/) | ​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![m](https://user-images.githubusercontent.com/1294454/27790564-a945a9d4-5ff9-11e7-9d2d-b635763f2f24.jpg)​](https://www.paymium.com/)​ | m | [Paymium](https://www.paymium.com/) | 1个 | [API](https://github.com/Paymium/api-documentation) | ​ | ​ |
| ​[​![poloniex](https://user-images.githubusercontent.com/1294454/27766817-e9456312-5ee6-11e7-9b3c-b628ca5626a5.jpg)​](https://www.poloniex.com/?utm_source=ccxt&utm_medium=web)​ | poloniex | [Poloniex](https://www.poloniex.com/?utm_source=ccxt&utm_medium=web) | \* | [API](https://docs.poloniex.com/) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x6743;&#x5229;](https://user-images.githubusercontent.com/1294454/42633917-7d20757e-85ea-11e8-9f53-fffe9fbb7695.jpg)​](https://www.rightbtc.com/)​ | 权利 | [RightBTC](https://www.rightbtc.com/) | \* | [API](https://docs.rightbtc.com/api/) | ​ | ​ |
| ​[​![&#x5357;&#x6C47;](https://user-images.githubusercontent.com/1294454/27838912-4f94ec8a-60f6-11e7-9e5d-bbf9bd50a559.jpg)​](https://www.southxchange.com/)​ | 南汇 | [SouthXchange](https://www.southxchange.com/) | \* | [API](https://www.southxchange.com/Home/Api) | ​ | ​ |
| ​[​![&#x7279;&#x514B;&#x65AF;](https://user-images.githubusercontent.com/1294454/69680782-03fd0b80-10bd-11ea-909e-7f603500e9cc.jpg)​](https://app.stex.com/?ref=36416021)​ | 特克斯 | [STEX](https://app.stex.com/?ref=36416021) | 3 | [API](https://help.stex.com/en/collections/1593608-api-v3-documentation) | ​ | ​ |
| ​[​![&#x636E;&#x70B9;](https://user-images.githubusercontent.com/1294454/52160042-98c1f300-26be-11e9-90dd-da8473944c83.jpg)​](https://stronghold.co/)​ | 据点 | [据点](https://stronghold.co/) | 1个 | [API](https://docs.stronghold.co/) | ​ | ​ |
| ​[​![&#x6BD4;&#x7279;&#x5E01;](https://user-images.githubusercontent.com/1294454/27991511-f0a50194-6481-11e7-99b5-8f02932424cc.jpg)​](https://surbitcoin.com/)​ | 比特币 | [SurBitcoin](https://surbitcoin.com/) | 1个 | [API](https://blinktrade.com/docs) | ​ | ​ |
| ​[​![&#x6D77;&#x6D0B;](https://user-images.githubusercontent.com/1294454/43103756-d56613ce-8ed7-11e8-924e-68f9d4bcacab.jpg)​](https://theocean.trade/)​ | 海洋 | [海洋](https://theocean.trade/) | 1个 | [API](https://docs.theocean.trade/) | ​ | ​ |
| ​[​![&#x6447;&#x6EDA;](https://user-images.githubusercontent.com/1294454/27766869-75057fa2-5ee9-11e7-9a6f-13e641fa4707.jpg)​](https://therocktrading.com/)​ | 摇滚 | [TheRockTrading](https://therocktrading.com/) | 1个 | [API](https://api.therocktrading.com/doc/v1/index.html) | ​ | ​ |
| ​[​![&#x6F6E;&#x6C50;&#x4F4D;](https://user-images.githubusercontent.com/1294454/39034921-e3acf016-4480-11e8-9945-a6086a1082fe.jpg)​](http://bit.ly/2IX0LrM)​ | 潮汐位 | [TideBit](http://bit.ly/2IX0LrM) | 2 | [API](https://www.tidebit.com/documents/api/guide) | ​ | ​ |
| ​[​![&#x6CF0;&#x8FEA;&#x514B;&#x65AF;](https://user-images.githubusercontent.com/1294454/30781780-03149dc4-a12e-11e7-82bb-313b269d24d4.jpg)​](https://tidex.com/exchange/?ref=57f5638d9cd7)​ | 泰迪克斯 | [Tidex](https://tidex.com/exchange/?ref=57f5638d9cd7) | 3 | [API](https://tidex.com/exchange/public-api) | ​ | ​ |
| ​[​![&#x5929;&#x7F8E;&#x65F6;](https://user-images.githubusercontent.com/1294454/70423869-6839ab00-1a7f-11ea-8f94-13ae72c31115.jpg)​](https://timex.io/)​ | 天美时 | [TIMEX](https://timex.io/) | 1个 | [API](https://docs.timex.io/) | ​ | ​ |
| ​[​![Topq](https://user-images.githubusercontent.com/1294454/74596147-50247000-505c-11ea-9224-4fd347cfbb49.jpg)​](https://www.topliq.com/)​ | Topq | [TOP.Q](https://www.topliq.com/) | 1个 | [API](https://github.com/topq-exchange/api_docs_en/wiki/REST_api_reference) | ​ | ​ |
| ​[​![&#x4E0A;&#x884C;](https://user-images.githubusercontent.com/1294454/49245610-eeaabe00-f423-11e8-9cba-4b0aed794799.jpg)​](https://upbit.com/)​ | 上行 | [Upbit](https://upbit.com/) | 1个 | [API](https://docs.upbit.com/docs/%EC%9A%94%EC%B2%AD-%EC%88%98-%EC%A0%9C%ED%95%9C) | ​[​![CCXT&#x8BA4;&#x8BC1;](https://img.shields.io/badge/CCXT-Certified-green.svg)​](https://github.com/ccxt/ccxt/wiki/Certification)​ | ​[​![CCXT&#x4E13;&#x4E1A;&#x7248;](https://img.shields.io/badge/CCXT-Pro-black)​](https://ccxt.pro/)​ |
| ​[​![&#x8DF3;&#x9A6C;](https://user-images.githubusercontent.com/1294454/27766880-f205e870-5ee9-11e7-8fe2-0d5b15880752.jpg)​](https://www.vaultoro.com/)​ | 跳马 | [Vaultoro](https://www.vaultoro.com/) | 1个 | [API](https://api.vaultoro.com/) | ​ | ​ |
| ​[​![vbtc](https://user-images.githubusercontent.com/1294454/27991481-1f53d1d8-6481-11e7-884e-21d17e7939db.jpg)​](https://vbtc.exchange/)​ | vbtc | [VBTC](https://vbtc.exchange/) | 1个 | [API](https://blinktrade.com/docs) | ​ | ​ |
| ​[​![&#x767D;&#x6BD4;&#x7279;](https://user-images.githubusercontent.com/1294454/66732963-8eb7dd00-ee66-11e9-849b-10d9282bb9e0.jpg)​](https://whitebit.com/referral/d9bdf40e-28f2-4b52-b2f9-cd1415d82963)​ | 白比特 | [WhiteBit](https://whitebit.com/referral/d9bdf40e-28f2-4b52-b2f9-cd1415d82963) | 2 | [API](https://documenter.getpostman.com/view/7473075/SVSPomwS?version=latest#intro) | ​ | ​ |
| ​[​![bt](https://user-images.githubusercontent.com/1294454/28059414-e235970c-662c-11e7-8c3a-08e31f78684b.jpg)​](https://xbtce.com/?agent=XX97BTCXXXG687021000B)​ | bt | [xBTCe](https://xbtce.com/?agent=XX97BTCXXXG687021000B) | 1个 | [API](https://www.xbtce.com/tradeapi) | ​ | ​ |
| ​[​![&#x7EA6;&#x6BD4;](https://user-images.githubusercontent.com/1294454/27766910-cdcbfdae-5eea-11e7-9859-03fea873272d.jpg)​](https://www.yobit.net/)​ | 约比 | [YoBit](https://www.yobit.net/) | 3 | [API](https://www.yobit.net/en/api/) | ​ | ​ |
| ​[​![&#x5F31;](https://user-images.githubusercontent.com/1294454/27766927-39ca2ada-5eeb-11e7-972f-1b4199518ca6.jpg)​](https://zaif.jp/)​ | 弱 | [弱势](https://zaif.jp/) | 1个 | [API](https://techbureau-api-document.readthedocs.io/ja/latest/index.html) | ​ | ​ |
| ​[​![&#x4F8B;&#x5982;](https://user-images.githubusercontent.com/1294454/32859187-cd5214f0-ca5e-11e7-967d-96568e2e2bd1.jpg)​](https://www.zb.com/)​ | 例如 | [例如，](https://www.zb.com/) | 1个 | [API](https://www.zb.com/i/developer) | ​ | ​ |

除了建立基本的市场和限价订单外，一些交易所还提供保证金交易（杠杆），各种衍生产品（例如期货合约和期权），并且还具有[暗池](https://en.wikipedia.org/wiki/Dark_pool)，[场外交易](https://en.wikipedia.org/wiki/Over-the-counter_%28finance)（场外交易），商人API等。

​

### 实例化 <a id="instantiation"></a>

要连接到交易所并开始交易，您需要从ccxt库实例化交易所类。

要以编程方式获取受支持交易所的ID的完整列表，请执行以下操作：

```text
// JavaScriptconst ccxt = require（'ccxt'）console.log（ccxt.exchanges）
```

```text
＃Python导入ccxt打印（ccxt.exchanges）
```

```text
// PHP包括'ccxt.php';var_dump（\ ccxt \ Exchange :: $ exchanges）;
```

可以像下面的示例中所示实例化交换：

```text
// JavaScriptconst ccxt = require（'ccxt'）let exchange = new ccxt.kraken（）//默认ID让kraken1 = new ccxt.kraken（{id：'kraken1'}）让kraken2 = new ccxt.kraken（{id：'kraken2'}）让id ='coinbasepro'让coinbasepro = new ccxt [id]（）;​//来自变量IDconst exchangeId ='binance'    ，exchangeClass = ccxt [exchangeId]    ，exchange = new exchangeClass（{        'apiKey'：'YOUR_API_KEY'，        '秘密'：'YOUR_SECRET'，        “超时”：30000，        'enableRateLimit'：是的，    }）
```

```text
＃Python导入ccxtexchange = ccxt.okcoinusd（）＃默认IDokcoin1 = ccxt.okcoinusd（{'id'：'okcoin1'}）okcoin2 = ccxt.okcoinusd（{'id'：'okcoin2'}）id ='btcchina'btcchina =评估（'ccxt。％s（）'％id）coinbasepro = getattr（ccxt，'coinbasepro'）（）​＃来自变量IDexchange_id ='binary'exchange_class = getattr（ccxt，exchange_id）exchange = exchange_class（{    'apiKey'：'YOUR_API_KEY'，    '秘密'：'YOUR_SECRET'，    “超时”：30000，    'enableRateLimit'：是的，}）
```

PHP中的ccxt库使用内置的UTC / GMT时间函数，因此，在使用库的PHP版本之前，您需要在php.ini中设置date.timezone或调用[date\_default\_timezone\_set（）](http://php.net/manual/en/function.date-default-timezone-set.php)函数。建议的时区设置为。`"UTC"`

```text
// PHPdate_default_timezone_set（'UTC'）;包括'ccxt.php';$ bitfinex =新的\ ccxt \ bitfinex（）; //默认ID$ bitfinex1 =新\ ccxt \ bitfinex（array（'id'=>'bitfinex1'））;$ bitfinex2 =新的\ ccxt \ bitfinex（array（'id'=>'bitfinex2'））;$ id ='海妖';$ exchange ='\\ ccxt \\'。$ id$ kraken =新的$ exchange（）;​//来自变量ID$ exchange_id ='二进制';$ exchange_class =“ \\ ccxt \\ $ exchange_id”;$ exchange =新的$ exchange_class（array（    'apiKey'=>'YOUR_API_KEY'，    '秘密'=>'YOUR_SECRET'，    '超时'=> 30000，    'enableRateLimit'=>是，））；
```

#### 实例化时覆盖Exchange属性 <a id="overriding-exchange-properties-upon-instantiation"></a>

在交换类实例化之后或之后，可以覆盖大多数交换属性以及特定选项，如下所示：

```text
// JavaScriptconst exchange = new ccxt.binance（{    'rateLimit'：10000，//统一交换属性    “标题”：{        'YOUR_CUSTOM_HTTP_HEADER'：'YOUR_CUSTOM_VALUE'，    }，    '选项'：{        'adjustForTimeDifference'：true，//特定于交易所的选项    }}）exchange.options ['adjustForTimeDifference'] =否
```

```text
＃Pythonexchange = ccxt.binance（{    'rateLimit'：10000，＃统一交换属性    “标题”：{        'YOUR_CUSTOM_HTTP_HEADER'：'YOUR_CUSTOM_VALUE'，    }，    '选项'：{        'adjustForTimeDifference'：正确，＃特定于交易所的选项    }}）exchange.options ['adjustForTimeDifference'] = False
```

```text
// PHP$ exchange_id ='二进制';$ exchange_class =“ \\ ccxt \\ $ exchange_id”;$ exchange =新的$ exchange_class（array（    'rateLimit'=> 10000，//统一交换属性    'headers'=>数组（        'YOUR_CUSTOM_HTTP_HEADER'=>'YOUR_CUSTOM_VALUE'，    ），    '选项'=>数组（        'adjustForTimeDifference'=> true，//特定于交易所的选项    ），））；$ exchange-> options ['adjustForTimeDifference'] = false;
```

### 交易结构 <a id="exchange-structure"></a>

每个交换都有一组属性和方法，您可以通过将一组关联的参数传递给交换构造函数来覆盖其中的大多数属性和方法。您还可以创建一个子类并覆盖所有内容。

这是基本交换属性的概述，其中添加了值：

```text
{    'id'：'exchange'//小写字符串交换ID    'name'：'Exchange'//可读字符串    'countries'：['US'，'CN'，'EU']，// ISO国家/地区代码数组    '网址'：{        'api'：'https://api.example.com/data'，//基本API URL的字符串或字典        'www'：'https://www.example.com'//字符串网站URL        'doc'：'https://docs.example.com/api'，//字符串URL或URL数组    }，    'version'：'v1'，//以数字结尾的字符串    'api'：{...}，// api端点字典    '有'：{//交换功能        “课程”：错误，        'publicAPI'：是的，        'privateAPI'：是的，        'cancelOrder'：是的，        'createDepositAddress'：否，        'createOrder'：true，        'deposit'：假，        'fetchBalance'：是的，        'fetchClosedOrders'：否，        'fetchCurrencies'：否，        'fetchDepositAddress'：否，        'fetchMarkets'：正确，        'fetchMyTrades'：否，        'fetchOHLCV'：否，        'fetchOpenOrders'：否，        'fetchOrder'：否，        'fetchOrderBook'：是的，        'fetchOrders'：否，        'fetchStatus'：'模拟的'，        'fetchTicker'：是的，        'fetchTickers'：否，        'fetchBidsAsks'：否，        'fetchTrades'：是的，        '提现'：假，    }，    'timeframes'：{//如果exchange.has ['fetchOHLCV']为空，== true        '1m'：'1minute'，        '1h'：'1hour'，        '1d'：'1day'，        '1M'：'1month'，        '1y'：'1year'，    }，    'timeout'：10000，//毫秒数    'rateLimit'：2000，//以毫秒为单位的数字    'userAgent'：'ccxt / 1.1.1 ...'//字符串，HTTP User-Agent标头    'verbose'：false，//布尔值，输出错误详细信息    'markets'：{...} //通过符号的市场/货币对字典    'symbols'：[...] //字符串符号（交易对）的排序列表    'currencies'：{...} //通过货币代码的货币词典    'markets_by_id'：{...}，//通过ID的字典（市场）字典    'proxy'：'https://crossorigin.me/'，//字符串网址    'apiKey'：'92560ffae9b8a0421 ...'，//字符串公共apiKey（ASCII，十六进制，Base64等）    'secret'：'9aHjPmW + EtRRKN / Oi ...'//字符串私有密钥    'password'：'6kszf4aci8r'，//字符串密码    'uid'：'123456'，//字符串用户ID}
```

#### 交换属性 <a id="exchange-properties"></a>

下面是每个基本交换属性的详细说明：

* `id`：每个交易所都有一个默认ID。id不会用于任何用途，它是用于用户土地交换实例标识目的的字符串文字。您可以具有指向同一交易所的多个链接，并通过ID区分它们。默认ID均为小写，并且与交换名称相对应。
* `name`：这是一个字符串文字，包含人类可读的交换名称。
* `countries`：由2个符号的ISO国家/地区代码组成的字符串文字的数组，在此位置进行交换。
* `urls['api']`：用于API调用的单字符串文字基础URL，或者用于私有和公共API的独立URL的关联数组。
* `urls['www']`：主要的HTTP网站网址。
* `urls['doc']`：指向原始文档的单个字符串URL链接，用于其网站上的Exchange API或指向文档的一系列链接。
* `version`：一个字符串文字，其中包含当前交换API的版本标识符。每次请求时，ccxt库都会将此版本字符串附加到API Base URL。除非您要实现新的交换API，否则不必修改它。在某些情况下，版本标识符是通常以字母'v'开头的数字字符串，例如v1.1。除非您要实现自己的新加密货币交换类，否则不要覆盖它。
* `api`：一个关联数组，其中包含由密码交换公开的所有API端点的定义。ccxt使用API​​定义为每个可用端点自动构造可调用的实例方法。
* `has`：这是交换能力（例如关联数组，或）。`fetchTickersfetchOHLCVCORS`
* `timeframes`：时间范围的关联数组，受交易所的fetchOHLCV方法支持。仅在property为true 时填充。`has['fetchOHLCV']`
* `timeout`：请求-响应往返的超时时间（以毫秒为单位）（默认超时为10000 ms = 10秒）。您应该始终将其设置为一个合理的值，当然，永久挂起且没有超时不是您的选择。
* `rateLimit`：请求速率限制（以毫秒为单位）。指定到同一交换机的两个后续HTTP请求之间所需的最小延迟。内置的速率限制器默认情况下是禁用的，并且通过将属性设置为true 可以打开。`enableRateLimit`
* `enableRateLimit`：一个布尔值（true / false），它启用内置的速率限制器并限制连续的请求。默认情况下，此设置为false（禁用）。**要求用户实施自己的**[**速率限制**](https://github.com/ccxt/ccxt/wiki/Manual#rate-limit)**或启用内置的速率限制器，以免被禁止进行交换**。
* `userAgent`：将HTTP User-Agent标头设置为的对象。ccxt库将默认设置其User-Agent。一些交易所可能不喜欢它。如果您很难从交易所获得答复，并且想要关闭User-Agent或使用默认代理，请将此值设置为false，undefined或空字符串。的值可能会被下面的HTTP 属性覆盖。`userAgentheaders`
* `headers`：HTTP标头及其值的关联数组。默认值为空。所有标题都将放在所有请求之前。如果标头设置在中，它将覆盖上面属性中设置的任何值。`{}User-AgentheadersuserAgent`
* `verbose`：布尔值标志，指示是否将HTTP请求记录到stdout（默认标志为false）。Python人员可以使用标准的pythonic记录器来进行DEBUG记录的另一种方式，方法是在代码的开头添加以下两行：

  ```text
  导入日志logging.basicConfig（level = logging.DEBUG）
  ```

* `markets`：由常见交易对或交易品种索引的市场关联数组。在访问此属性之前，应先加载市场。在调用交换实例上的方法之前，市场不可用。`loadMarkets() / load_markets()`
* `symbols`：交换可用的非关联符号数组（列表），按字母顺序排序。这些是属性的键。从市场上加载和重新加载符号。此属性是所有市场密钥的便捷快捷方式。`markets`
* `currencies`：交易所提供的按代码（通常为3或4个字母）组成的货币关联数组（字典）。从市场上加载和重新加载货币。
* `markets_by_id`：由特定于交易所的ID索引的市场的关联数组。在访问此属性之前，应先加载市场。
* `proxy`：默认情况下，包含http（s）代理的基本URL的字符串文字。与Web浏览器一起使用，并在受阻止的位置使用。代理字符串的示例是。在发送HTTP请求之前，将绝对交换端点URL附加到此字符串。`'''http://crossorigin.me/'`
* `apiKey`：这是您的公共API密钥字符串文字。大多数交换要求[设置API密钥](https://github.com/ccxt/ccxt/wiki/Manual#api-keys-setup)。
* `secret`：您的私有秘密API密钥字符串文字。大多数交易所也需要使用apiKey。
* `password`：带有您的密码/短语的字符串文字。一些交易所要求使用此参数进行交易，但大多数交易所不需要。
* `uid`：您帐户的唯一ID。这可以是字符串文字或数字。一些交易所也要求使用此功能，但大多数交易所不需要。
* `requiredCredentials`：一个统一的关联字典，显示将上面的API凭证中的哪些凭证用于将私有API调用发送到基础交易所（交易所可能需要一组特定的密钥）。
* `options`：特定于交易所的关联字典，其中包含基础交易所接受并在CCXT中支持的特殊键和选项。
* `precisionMode`：交换小数精度计数模式，详细了解精度和极限

有关[覆盖交换属性的信息，](https://github.com/ccxt/ccxt/wiki/Manual#overriding-exchange-properties-upon-instantiation)请参见本节。

**交换元数据**

* `has`：一个assoc数组，其中包含用于交换功能的标志，包括：

  ```text
  '已'： {​      'CORS'：false，//是否启用跨域资源共享（通过浏览器工作）​      'publicAPI'：true，//具有可用的公共API并已实现，true / false      'privateAPI'：true，//具有可用的和已实现的私有API，true / false​      //统一方法的可用性标志（可以为true，false或“模拟”）：​      'cancelOrder'：是的，      'createDepositAddress'：否，      'createOrder'：true，      'deposit'：假，      'fetchBalance'：是的，      'fetchClosedOrders'：否，      'fetchCurrencies'：否，      'fetchDepositAddress'：否，      'fetchMarkets'：正确，      'fetchMyTrades'：否，      'fetchOHLCV'：否，      'fetchOpenOrders'：否，      'fetchOrder'：否，      'fetchOrderBook'：是的，      'fetchOrders'：否，      'fetchStatus'：'模拟的'，      'fetchTicker'：是的，      'fetchTickers'：否，      'fetchBidsAsks'：否，      'fetchTrades'：是的，      '提现'：假，      ...  }
  ```

  显示此方法或该方法的可用性的每个标志的含义是：

  * 布尔值表示该方法可从Exchange API本地获得，并在ccxt库中统一`true`
  * 布尔值表示该方法不是可从Exchange API本地获得的，或者尚未在ccxt库中统一`false`
  * 一个字符串表示的端点不是本身可从交流API，但重建从可用真方法ccxt库`'emulated'`

### 速率限制 <a id="rate-limit"></a>

交易所通常实行所谓的_限价_。交易所将记住并跟踪您的用户凭据和IP地址，并且不允许您过于频繁地查询API。他们平衡负载并控制流量拥塞，以保护API服务器免受（D）DoS和滥用的影响。

**警告：请遵守速率限制以避免被禁止！**

大多数交换**每秒**最多允许**1或2个请求**。如果您对请求过于激进，交易所可能会暂时限制您对其API的访问，或者在一段时间内禁止您访问。

**该属性设置为次优的安全默认值。一些交易所对于不同的端点可能具有不同的速率限制。用户可以根据应用程序的特定目的进行调整。`exchange.rateLimitrateLimit`**

CCXT库具有内置的实验速率限制器，它将对用户透明地在后台进行必要的限制。**警告：用户至少要负责某种速率限制：通过实现自定义算法或使用内置的速率限制器来执行。**。

用属性打开内置的速率限制器，如下所示：`.enableRateLimit`

```text
// JavaScript​//在交换实例化时启用内置速率限制const exchange = new ccxt.bitfinex（{    'enableRateLimit'：是的，}）​//或在实例化之后稍后打开或关闭内置速率限制器exchange.enableRateLimit = true //启用exchange.enableRateLimit = false //禁用
```

```text
＃Python​＃在交换实例化时启用内置速率限制交换= ccxt.bitfinex（{    'enableRateLimit'：是的，}）​＃或在实例化之后稍后打开或关闭内置速率限制器exchange.enableRateLimit =真＃使能exchange.enableRateLimit = False＃禁用
```

```text
// PHP​//在交换实例化时启用内置速率限制$ exchange =新的\ ccxt \ bitfinex（数组（    'enableRateLimit'=>是，））；​//或在实例化之后稍后打开或关闭内置速率限制器$ exchange-> enableRateLimit = true; //启用$ exchange-> enableRateLimit = false; //禁用
```

如果您的呼叫达到了速率限制或出现随机数错误，则ccxt库将引发异常，或在某些情况下为以下类型之一：`InvalidNonce`

* `DDoSProtectionError`
* `ExchangeNotAvailable`
* `ExchangeError`
* `InvalidNonce`

稍后重试通常足以解决该问题。这里的更多信息：

* [认证](https://github.com/ccxt/ccxt/wiki/Manual#authentication)
* [疑难解答](https://github.com/ccxt/ccxt/wiki/Manual#troubleshooting)
* [重写杜撰](https://github.com/ccxt/ccxt/wiki/Manual#overriding-the-nonce)

#### Cloudflare /封装的DDoS保护 <a id="ddos-protection-by-cloudflare-incapsula"></a>

某些交易所受[Cloudflare](https://www.cloudflare.com/)或[Incapsula](https://www.incapsula.com/)保护的[DDoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)。在高负载期间，您的IP可能会暂时被阻止。有时，它们甚至限制了整个国家和地区。在这种情况下，他们的服务器通常会返回一个页面，该页面指出HTTP 40x错误或对您的浏览器/验证码测试进行AJAX测试，并将页面的重新加载延迟几秒钟。然后，您的浏览器/指纹将被临时授予访问权限，并被添加到白名单或接收HTTP cookie以供进一步使用。

DDoS保护问题，速率限制问题或基于位置的过滤问题的最常见症状：

* 使用所有类型的交换方法获取异常`RequestTimeout`
* 捕获或带有HTTP错误代码400、403、404、429、500、501、503等。`ExchangeErrorExchangeNotAvailable`
* 存在DNS解决问题，SSL证书问题和低级连接问题
* 从交易所获取模板HTML页面而不是JSON

如果遇到DDoS保护错误，并且无法进行特定的交换，则：

* 尝试使用cloudscraper：
  * [https://github.com/ccxt/ccxt/blob/master/examples/js/bypass-cloudflare.js](https://github.com/ccxt/ccxt/blob/master/examples/js/bypass-cloudflare.js)
  * [https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare.py](https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare.py)
  * [https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare-with-cookies.py](https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare-with-cookies.py)
* 使用代理（尽管响应速度较慢）
* 要求交流支持将您添加到白名单
* 在交易所附近（同一国家，同一城市，同一数据中心，同一服务器机架，同一服务器）运行您的软件
* 在其他地理区域内尝试其他IP
* 在服务器的分布式网络中运行软件
* …

## 市场 <a id="markets"></a>

每个交易所都是交易某些贵重物品的地方。有时，它们用各种不同的术语来称呼，例如工具，符号，交易对，货币，代币，股票，商品，合约等，但它们的含义都是相同的-交易对，符号或金融工具。

就ccxt库而言，每个交易所都在其内部提供多个市场。市场的设置因交易所的不同而不同，可以进行交叉交易和跨市场套利。市场通常是一对交易的加密/法定货币。

### 市场结构 <a id="market-structure"></a>

```text
{    'id'：'btcusd'，//用于在交换中引用的字符串文字    'symbol'：'BTC / USD'，//一对货币的大写字符串文字    'base'：'BTC'，//大写字符串，统一的基本货币代码，3个或更多字母    'quote'：'USD'，//大写字符串，统一报价货币代码，3个或更多字母    'baseId'：'btc'，//任何字符串，特定于交易所的基础货币ID    'quoteId'：'usd'，//任何字符串，特定于交易所的报价货币ID    'active'：true，//布尔值，市场状态    'precision'：{//“点后”的小数位数        'price'：8，// TICK_SIZE roundingMode的整数或浮点数，如果交易所未提供，则可能会丢失        'amount'：8，//整数，如果交易所未提供，则可能会丢失        'cost'：8，//整数，实际上很少有交易所    }，    'limits'：{//在此市场下单时的价值限制        '金额'：{            'min'：0.01，//订单金额应> min            'max'：1000，//订单金额应<max        }，        'price'：{...}，//订单价格的最小/最大限制相同        'cost'：{...}，//订单费用的相同限制=价格*金额    }，    'info'：{...}，//交易所未解析的原始市场信息}
```

每个市场都是具有以下键的关联数组（也称为字典）：

* `id`。交易所内市场或交易工具的字符串或数字ID。市场ID在内部在交易所内部使用，以在请求/响应过程中识别交易对。
* `symbol`。特定交易对或工具的大写字符串代码表示。通常在，或等中用斜杠编写。符号用于引用ccxt库中的市场（如下所述）。`BaseCurrency/QuoteCurrencyBTC/USDLTC/CNYETH/EUR`
* `base`。基本法定货币或加密货币的统一大写字符串代码。这是标准化的货币代码，用于在整个CCXT和整个Unified CCXT API中引用该货币或令牌，这是CCXT理解的语言。
* `quote`。法定货币或加密货币的统一大写字符串代码。
* `baseId`。此市场的基础货币的交易所特定的ID，不统一。从字面上看，可以是任何字符串。使用交易所理解的语言将此信息传达给交易所。
* `quoteId`。报价货币的交易所特定的ID，不统一。
* `active`。指示当前是否可以交易该市场的布尔值。通常，当市场处于非活动状态时，所有相应的报价单，订单簿和其他相关端点将返回该市场的空响应，全零，无数据或过时的数据。用户应检查市场是否活跃，并定期重新加载市场缓存，如下所述。
* `info`。非常见市场属性的关联数组，包括费用，费率，限额和其他一般市场信息。内部信息数组因每个特定市场而异，其内容取决于交易所。
* `precision`。通过在下单时交换价格，金额和成本来接受订单价值中的精度。该市场属性内的价值取决于。`exchange.precisionMode`
  * 如果为，则指定点后的小数位数。`exchange.precisionModeDECIMAL_DIGITSmarket['precision']`
  * 如果为，则指定点后的非零位数。`exchange.precisionModeSIGNIFICANT_DIGITSmarket['precision']`
  * 当是那么指定的最小可能浮馏分。`exchange.precisionModeTICK_SIZEmarket['precision']`
* `limits`。价格，数量（量）和成本（其中成本=价格\*数量）的最小和最大。

### 货币结构 <a id="currency-structure"></a>

```text
{    'id'：'btc'，//用于在交换中引用的字符串文字    'code'：'BTC'，//大写统一字符串文字代码货币    'name'：'Bitcoin'，//字符串，人类可读的名称（如果指定）    'active'：true，//布尔值，货币状态（可交易和可提取）    ``费用''：0.123    'precision'：8，//点后的小数位数（取决于exchange.precisionMode）    'limits'：{//在此市场下单时的价值限制        '金额'：{            'min'：0.01，//订单金额应> min            'max'：1000，//订单金额应<max        }，        'price'：{...}，//订单价格的最小/最大限制相同        'cost'：{...}，//订单费用的相同限制=价格*金额        'withdraw'：{...}，//提款限额    }，    'info'：{...}，//交易所未解析的原始货币信息}
```

每种货币都是具有以下键的关联数组（也称为字典）：

* `id`。交易所内货币的字符串或数字ID。在请求/响应过程中，内部使用货币ID进行内部交易所识别硬币。
* `code`。特定货币的大写字符串代码表示形式。货币代码用于引用ccxt库中的货币（如下所述）。
* `name`。自我解释。
* `active`。一个布尔值，指示当前是否可以进行此货币的交易和融资（存款和取款）。通常，当一种货币处于非活动状态时，所有相应的代码，订单簿和其他相关端点将返回该货币的空响应，全零，无数据或过时的数据。用户应检查货币是否有效，并定期重新加载市场，如下所述。
* `info`。非常见市场属性的关联数组，包括费用，费率，限额和其他一般市场信息。内部信息数组因每个特定市场而异，其内容取决于交易所。
* `precision`。在参考该货币时通过汇率接受的精度值。此属性内的值取决于。`exchange.precisionMode`
  * 如果为，则指定点后的小数位数。`exchange.precisionModeDECIMAL_DIGITScurrency['precision']`
  * 如果为，则指定点后的非零位数。`exchange.precisionModeSIGNIFICANT_DIGITScurrency['precision']`
  * 当是那么指定的最小可能浮馏分。`exchange.precisionModeTICK_SIZEcurrency['precision']`
* `limits`。价格，金额（数量），成本（其中成本=价格\*金额）和取款的最小值和最大值。

#### 精度和极限 <a id="precision-and-limits"></a>

**不要混淆与！**精度与最小限制无关。8位数字的精度不一定意味着最低限制为0.00000001。反之亦然：0.0001的最小限制不一定表示精度为4。**`limitsprecision`**

例子：

1. `(market['limits']['amount']['min'] == 0.05) && (market['precision']['amount'] == 4)`

   在第一个示例中，投放市场的任何订单的**数量必须满足以下两个条件**：

   * 的_量值_应该是&gt; = 0.05：

     ```text
     +好：0.05、0.051、0.0501、0.0502，...，0.0599、0.06、0.0601，...-差：0.04、0.049、0.0499
     ```

   * _金额的精度_应最多为4个十进制数字：

     ```text
     +好：0.05、0.051、0.052，...，0.0531，...，0.06，... 0.0719，...-差：0.05001、0.05000、0.06001
     ```

2. `(market['limits']['price']['min'] == 0.0019) && (market['precision']['price'] == 5)`

   在第二个示例中，在市场**上下**的任何订单的**价格必须满足以下两个条件**：

   * 所述_价格值_应&gt; = 0.019：

     ```text
     +良好：0.019，... 0.0191，... 0.01911，0.01912，...-差：0.016，...，0.01699
     ```

   * _价格精度_应为5个小数位数或更少：

     ```text
     +好：0.02、0.021、0.0212、0.02123、0.02124、0.02125，...-不好：0.017000、0.017001 ...
     ```

3. `(market['limits']['amount']['min'] == 50) && (market['precision']['amount'] == -1)`
   * 的_量的值_应大于或等于50：

     ```text
     +好：50，60，70，80，90，100，... 2000，...-不好：1、2、3，...，9
     ```

   * 负数_精度_表示该数量应为10的整数倍（达到指定的绝对功效）：

     ```text
     +好：50，...，110，... 1230，...，1000000，...，1234560，...-不好：9.5，...，10.1，...，11，... 200.71，...
     ```

_在和PARAMS目前处于开发状态，有些字段可能在这里失踪，直到有统一的过程就完成了。这不会影响大多数订单，但是在非常大或非常小的订单的极端情况下可能会很重要。并非所有市场都支持和/或实施该标志。`precisionlimitsactive`_

**关于精度和极限的注意事项**

要求用户保持所有限制和精度！订单的值应满足以下条件：

* 订单&gt; =`amountlimits['min']['amount']`
* 订单&lt;=`amountlimits['max']['amount']`
* 订单&gt; =`pricelimits['min']['price']`
* 订单&lt;=`pricelimits['max']['price']`
* 顺序（）&gt; =`costamount * pricelimits['min']['cost']`
* 顺序（）&lt;=`costamount * pricelimits['max']['cost']`
* 的精度必须&lt;=`amountprecision['amount']`
* 的精度必须&lt;=`priceprecision['price']`

在某些未从其API提供有关限制的信息或尚未实现这些信息的交易所中，上述值可能会丢失。

**格式化小数的方法**

每个交换都有自己的舍入，计数和填充模式。

支持的舍入模式为：

* `ROUND` –将最后的十进制数字舍入到精度
* `TRUNCATE`–达到一定精度后将切断数字

该属性中提供了十进制精度计数模式。`exchange.precisionMode`

支持的精度模式为：

* `DECIMAL_PLACES`–计算所有数字，99％的交换使用此计数模式。在这种精度模式下，中的数字表示点后的小数位数，以便进一步舍入或截断。`market['precision']`
* `SIGNIFICANT_DIGITS`–仅计算非零数字，某些交易所（可能还有其他一些交易所）采用这种计数小数的模式。在这种精度模式下，数字表示点后最后一个有效（非零）十进制数字的第N位。`bitfinexmarket['precision']`
* `TICK_SIZE`–某些交易所仅允许使用特定值的倍数（例如，使用此模式）。在此模式下，数字指定用于舍入或截断的最小精度分数（浮点数）。`bitmexftxmarket['precision']`

支持的填充模式为：

* `NO_PADDING` –大多数情况下默认
* `PAD_WITH_ZERO` –最多附加零个字符

交换基类包含的方法可帮助将值格式化为所需的十进制精度，并支持不同的舍入，计数和填充模式。`decimalToPrecision`

```text
// JavaScript函数decimalToPrecision（x，roundingMode，numPrecisionDigits，countingMode = DECIMAL_PLACES，paddingMode = NO_PADDING）
```

```text
＃Python＃ 警告！`decimal_to_precision`方法容易受到getcontext（）。prec的影响！def decimal_to_precision（n，rounding_mode = ROUND，precision = None，counting_mode = DECIMAL_PLACES，padding_mode = NO_PADDING）：
```

```text
// PHP函数decimalToPrecision（$ x，$ roundingMode = ROUND，$ numPrecisionDigits = null，$ countingMode = DECIMAL_PLACES，$ paddingMode = NO_PADDING）
```

有关如何使用来格式化字符串和浮点格式的示例，请参见以下文件：`decimalToPrecision`

* JavaScript的：[https://github.com/ccxt/ccxt/blob/master/js/test/base/functions/test.number.js](https://github.com/ccxt/ccxt/blob/master/js/test/base/functions/test.number.js)
* 的Python：[https://github.com/ccxt/ccxt/blob/master/python/test/test\_decimal\_to\_precision.py](https://github.com/ccxt/ccxt/blob/master/python/test/test_decimal_to_precision.py)
* PHP：[https://github.com/ccxt/ccxt/blob/master/php/test/decimal\_to\_precision.php](https://github.com/ccxt/ccxt/blob/master/php/test/decimal_to_precision.php)

**Python警告！该方法易受getcontext（）。prec！`decimal_to_precision`**

### 加载市场 <a id="loading-markets"></a>

在大多数情况下，您需要先访问特定交易所的市场和交易代码列表，然后才能访问其他API方法。如果您忘记加载市场，ccxt库将在您首次调用统一API时自动执行。它将依次发送两个HTTP请求，第一个针对市场，然后第二个针对其他数据。

为了手动加载市场，请事先在交易所实例上调用/ 方法。它返回由交易代码索引的市场相关数组。如果您想更好地控制逻辑的执行，建议手动预装市场。`loadMarkets ()load_markets ()`

```text
// JavaScript（异步（）=> {    让kraken = new ccxt.kraken（）    让市场=等待kraken.load_markets（）    console.log（kraken.id，市场）}）（）
```

```text
＃Pythonokcoin = ccxt.okcoinusd（）市场= okcoin.load_markets（）打印（okcoin.id，市场）
```

```text
// PHP$ id ='huobipro';$ exchange ='\\ ccxt \\'。$ id;$ huobipro =新的$ exchange（）;$ markets = $ huobipro-> load_markets（）;var_dump（$ huobipro-> id，$ markets）;
```

除市场信息外，该呼叫还将从交易所加载货币，并将信息分别缓存在和属性中。`loadMarkets().markets.currencies`

用户还可以绕过直接取出由交换端点信息，高速缓存和呼叫统一的方法和，虽然使用这些方法，不建议最终用户。建议的预加载市场的方法是调用统一方法。但是，如果基础交换具有相应的API端点，则需要新的交换集成来实现这些方法。`fetchMarkets()fetchCurrencies()loadMarkets()`

### 符号和市场编号 <a id="symbols-and-market-ids"></a>

在REST请求-响应过程中使用市场ID来引用交易所内的交易对。市场ID的集合在每个交易所都是唯一的，不能在各个交易所之间使用。例如，BTC /美元/市场可能对各种流行的交流，不同的ID等，，，，（数字ID）， ， ，， 。 您无需记住或使用市场ID，它们在交易所实现中用于内部HTTP请求-响应目的。`btcusdBTCUSDXBTUSDbtc/usd42BTC/USDBtc/UsdtBTCUSDXXBTZUSD`

ccxt库将不常见的市场ID提取为符号，并标准化为通用格式。符号与市场编号不同。每个市场都有相应的符号引用。符号在交易所之间是通用的，这使得它们适用于套利和许多其他事情。

符号通常是一对交易货币的大写字符串文字名称，中间使用斜杠。一种货币的三个或四个大写字母，一个类似的代码，，，，，，，，，，，，等一些交易所有更长的名字异国情调的货币。斜线前的第一个货币通常称为_基础货币_，斜线后的第一个_货币_称为_报价货币_。一个符号的实例为：，，，，，，。`BTCETHUSDGBPCNYLTCJPYDOGERUBZECXRPXMRBTC/USDDOGE/LTCETH/EURDASH/XRPBTC/CNYZEC/XMRETH/JPY`

有时，用户可能会注意到类似或或其他_“稀有/稀有符号”的符号_。该符号**不需要**带有斜线或成对的货币。符号中的字符串实际上取决于市场类型（无论是现货市场还是期货市场，暗池市场或过期市场等）。不鼓励尝试解析符号字符串，不应依赖符号格式，建议改用市场属性。`'XBTM18''.XRPUSDM20180101'`

市场结构由符号和id索引。基本交易所类还具有用于通过符号访问市场的内置方法。大多数API方法都要求在第一个参数中传递符号。查询当前价格，下订单等时，通常需要指定符号。

大多数时候，用户将使用市场符号。如果您访问这些命令中不存在的键，则将获得标准的Userland例外。

#### 市场和货币的方法 <a id="methods-for-markets-and-currencies"></a>

```text
// JavaScript​（异步（）=> {​    console.log（等待exchange.loadMarkets（））​    let btcusd1 = exchange.markets ['BTC / USD'] //通过符号获取市场结构    let btcusd2 = exchange.market（'BTC / USD'）//相同结果略有不同​    let btcusdId = exchange.marketId（'BTC / USD'）//通过符号获取市场编号​    let symbol = exchange.symbols //获取一个符号数组    let symbol2 = Object.keys（exchange.markets）//与上一行相同​    console.log（exchange.id，symbol）//打印所有符号​    let currency = exchange.currencies //货币词典​    让bitfinex =新的ccxt.bitfinex（）    等待bitfinex.loadMarkets（）​    bitfinex.markets ['BTC / USD'] //符号→市场（通过符号获取市场）    bitfinex.markets_by_id ['XRPBTC'] // ID→市场（按ID获取市场）​    bitfinex.markets ['BTC / USD'] ['id'] //符号→ID（通过符号获取ID）    bitfinex.markets_by_id ['XRPBTC'] ['symbol'] // ID→符号（按ID获取符号）​}）
```

```text
＃Python​打印（exchange.load_markets（））​etheur1 = exchange.markets ['ETH / EUR']＃通过符号获取市场结构etheur2 = exchange.market（'ETH / EUR'）＃相同的结果略有不同​etheurId = exchange.market_id（'BTC / USD'）＃通过符号获取市场编号​symbol = exchange.symbols＃获取符号列表symbol2 =列表（exchange.markets.keys（））＃与上一行相同​打印（exchange.id，符号）＃打印所有符号​货币= exchange.currencies＃货币词典​裂纹= ccxt.kraken（）kraken.load_markets（）​kraken.markets ['BTC / USD']＃符号→市场（通过符号获取市场）kraken.markets_by_id ['XXRPZUSD']＃ID→市场（按ID获取市场）​kraken.markets ['BTC / USD'] ['id']＃符号→ID（按符号获取ID）kraken.markets_by_id ['XXRPZUSD'] ['symbol']＃id→符号（通过id获取符号）
```

```text
// PHP​$ var_dump（$ exchange-> load_markets（））;​$ dashcny1 = $ exchange-> markets ['DASH / CNY']; //通过符号获取市场结构$ dashcny2 = $ exchange-> market（'DASH / CNY'）; //相同的结果稍有不同​$ dashcnyId = $ exchange-> market_id（'DASH / CNY'）; //通过符号获取市场编号​$ symbols = $ exchange-> symbols; //获取符号数组$ symbols2 = array_keys（$ exchange-> markets）; //与上一行相同​var_dump（$ exchange-> id，$ symbols）; //打印所有符号​$ currencies = $ exchange-> currencies; //货币的关联数组​$ okcoinusd ='\\ ccxt \\ okcoinusd';$ okcoinusd =新的$ okcoinusd（）;​$ okcoinusd-> load_markets（）;​$ okcoinusd-> markets ['BTC / USD']; //符号→市场（通过符号获取市场）$ okcoinusd-> markets_by_id ['btc_usd']; // ID→市场（按ID获取市场）​$ okcoinusd-> markets ['BTC / USD'] ['id']; //符号→ID（按符号获取ID）$ okcoinusd-> markets_by_id ['btc_usd'] ['symbol']; // ID→符号（通过ID获取符号）
```

#### 命名一致性 <a id="naming-consistency"></a>

各个交易所的术语含糊不清，可能会引起新来交易者的困惑。一些交易所将市场称为_对_，而另一些交易所将符号称为_产品_。就ccxt库而言，每个交易所都包含一个或多个交易市场。每个市场都有一个ID和一个符号。大多数符号是基础货币和报价货币对。

`Exchanges → Markets → Symbols → Currencies`

历史上，各种符号名称已用于指定相同的交易对。一些加密货币（例如Dash）甚至在其整个生命周期中多次更改了名称。为了使交易所之间保持一致，ccxt库将执行以下已知的符号和货币替换：

* `XBT → BTC`：较新，但在交易所中更为常见，听起来更像是比特币（`XBTBTC`[了解更多](https://www.google.ru/search?q=xbt+vs+btc)）。
* `BCC → BCH`：经常使用两种不同的符号名称来调用Bitcoin Cash fork：和。对于比特币现金，这个名字是模棱两可的，它与BitConnect混淆了。该ccxt库将转换到它是合适的（一些交流和集成混淆）。`BCCBCHBCCBCCBCH`
* `DRK → DASH`：是Darkcoin，然后成为Dash（`DASH`[阅读更多内容](https://minergate.com/blog/dashcoin-and-dash/)）。
* `BCHABC → BCH`：在2018年11月15日，比特币现金第二次分叉，所以现在有（对于BCH ABC）和（对于BCH SV）。`BCHBSV`
* `BCHSV → BSV`：这是比特币Cash SV分支的常见替代映射（一些交易所称为，其他交易所称为，我们使用前者）。`BSVBCHSV`
* `DSH → DASH`：不要混淆符号和货币。的（Dashcoin）是不一样的（短划线）。一些交易所将不一致地标记为，ccxt库也对此进行了更正（），但是仅在某些特定的交易所将这两种货币混淆了，而大多数交易所却都将它们都正确了。请记住，这与。`DSHDASHDASHDSHDSH → DASHDASH/BTCDSH/BTC`
* `XRB`→ ：是较新的代码RaiBlocks，因此，CCXT统一的API使用将取代旧的用在需要的地方。`NANONANOXRBNANO`[https://hackernoon.com/nano-rebrand-announcement-9101528a7b76](https://hackernoon.com/nano-rebrand-announcement-9101528a7b76)
* `USD`→ ：一些交易所（例如Bitfinex，HitBTC和其他一些交易所）在其列表中使用货币作为名称，但是这些市场实际上正在交易。混淆可能来自符号名称的3个字母的限制，也可能是由于其他原因。在实际交易的货币不是交易货币的情况下，CCXT库将执行→ 转换。但是请注意，某些交易所同时具有和符号，例如，Kraken有交易对。`USDTUSDUSDTUSDTUSDUSDUSDTUSDUSDTUSDT/USD`

**命名一致性注意事项**

每个交易所在属性中都有一个替换数组，用于替换加密货币符号代码。有时，用户可能会在代码中注意到带有混合大小写单词和空格的奇异符号名称。当一种或多种货币具有相同的符号代码且具有不同的兑换时，解决这些命名和货币编码冲突的规则解释了拥有这些名称的逻辑：`exchange.commonCurrencies`

* 首先，我们从交易所本身收集所有有关货币代码的信息。他们通常会在其API或文档，知识库或网站其他位置中对硬币清单进行描述。
* 当我们识别货币代码背后的每种特定加密货币时，我们会在[CoinMarketCap](https://coinmarketcap.com/)上进行[查询](https://coinmarketcap.com/)。
* 市值最大的货币将赢得并保留其货币代码。例如，HOT通常代表或。在这种情况下，将保留代码，并将其名称作为其代码，字面意思是。因此，可能存在带有（for ）和– 等符号的交易对，它们是两个不同的市场。`HoloHydro ProtocolHoloHOTHydro ProtocolHydro ProtocolHOT/USDHoloHydro Protocol/USD`
* 如果特定硬币的市值未知或不足以确定获胜者，我们还将考虑交易量和其他因素。
* 确定获胜者后，所有其他竞争货币都会通过重新正确映射其代号并在冲突的交易所内替换。`.commonCurrencies`
* 不幸的是，这是一个正在进行的工作，因为每天都会列出新货币并不时添加新交易所，因此，通常，在快速变化的环境中，实际上，这是一个永无止境的自我校正过程，实际上是_“实时”模式”_。对于您发现的所有冲突和不匹配现象，我们深表感谢。

**命名一致性问题**

_**符号是否有可能改变？**_

简而言之，是的，有时但很少。如果绝对必要且无法避免，则可以更改符号映射。但是，以前所有的符号更改都与解决冲突或分叉有关。到目前为止，在CCXT中还没有先例的市值能超过一个具有相同符号代码的代币。

_**我们可以依靠总是列出具有相同符号的相同加密货币吗？**_

或多或少）首先，该库正在开发中，它正在尝试适应不断变化的现实，因此将来可能会通过更改某些映射来解决冲突。最终，许可证说“不做任何担保，使用后果自负”。但是，我们不会在整个地方随机更改符号映射，因为我们了解后果，并且我们也希望依赖于库，并且根本不希望破坏向后兼容性。

如果发生这种情况，即主要令牌的符号被分叉或必须更改，则控件仍在用户手中。与其他任何交换属性一样，可以在初始化时或以后覆盖该属性。如果涉及到重要的标记，我们通常会通过在构造函数参数中添加几行来发布有关如何保留旧行为的说明。`exchange.commonCurrencies`

**基础货币和报价货币的一致性**

这要看你交换使用，但其中一些有一个反转（不一致）配对和。实际上，它们的基数和引号放错了位置（切换/反面）。在这种情况下，您会看到市场子结构中已解析和货币值与未解析值的差异。`basequotebasequoteinfo`

对于这些交易所，ccxt将在解析交易所答复时对基础货币和报价货币进行更正，切换和标准化。这种逻辑在财务和术语上都是正确的。如果要减少混乱，请记住以下规则：**在任何符号和任何市场中，base总是在斜杠之前，报价总是在斜杠之后**。

```text
基础货币↓             BTC / USDT             ETH / BTC            DASH / ETH                    ↑报价货币
```

### 市场缓存力重新加载 <a id="market-cache-force-reload"></a>

这也是一种肮脏的方法，具有在交换实例上保存市场阵列的副作用。每次交换只需要调用一次。随后对同一方法的所有调用将返回本地保存（缓存）的市场数组。`loadMarkets () / load_markets ()`

加载交易所市场后，您可以随时通过该属性访问市场信息。该属性包含一个由符号索引的市场关联数组。如果已经加载市场后需要强制重新加载市场列表，则将reload = true标志再次传递给相同的方法。`markets`

```text
// JavaScript（异步（）=> {    let kraken = new ccxt.kraken（{verbose：true}）//记录HTTP请求    await kraken.load_markets（）//请求市场    console.log（kraken.id，kraken.markets）//输出所有已加载市场的完整列表    console.log（Object.keys（kraken.markets））//输出简短的市场符号列表    console.log（kraken.markets ['BTC / USD']）//输出单个市场详细信息    await kraken.load_markets（）//返回本地缓存的版本，不重新加载    let reloadedMarkets =等待kraken.load_markets（true）//强制HTTP reload = true    console.log（reloadedMarkets ['ETH / BTC']）}）（）
```

```text
＃Pythonpoloniex = ccxt.poloniex（{'verbose'：True}）＃记录HTTP请求poloniex.load_markets（）＃请求市场print（poloniex.id，poloniex.markets）＃输出所有已加载市场的完整列表print（list（poloniex.markets.keys（）））＃输出简短的市场符号列表print（poloniex.markets ['BTC / ETH']）＃输出单个市场详细信息poloniex.load_markets（）＃返回本地缓存的版本，不重新加载reloadedMarkets = poloniex.load_markets（True）＃强制HTTP重新加载= True打印（reloadedMarkets ['ETH / ZEC']）
```

```text
// PHP$ bitfinex =新的\ ccxt \ bitfinex（数组（'verbose'=> true））; //记录HTTP请求$ bitfinex.load_markets（）; //请求市场var_dump（$ bitfinex-> id，$ bitfinex-> markets）; //输出所有已加载市场的完整列表var_dump（array_keys（$ bitfinex-> markets））; //输出简短的市场符号列表var_dump（$ bitfinex-> markets ['XRP / USD']）; //输出单个市场详细信息$ bitfinex-> load_markets（）; //返回本地缓存的版本，不重新加载$ reloadedMarkets = $ bitfinex-> load_markets（true）; //强制HTTP重新加载= truevar_dump（$ bitfinex-> markets ['XRP / BTC']）;
```

## API方法/端点 <a id="api-methods-endpoints"></a>

每个交换提供一组API方法。API的每种方法都称为_终结点_。端点是用于查询各种类型信息的HTTP URL。所有端点均响应客户端请求返回JSON。

通常，有一个端点可以从交易所获取市场清单，一个端点可以检索特定市场的订单簿，一个端点可以检索交易历史记录，端点可以下订单和取消订单，可以存钱或取款，等等。基本上，您可以在特定交换中执行的每种操作都有API提供的单独的端点URL。

由于交换的方法集不同，因此ccxt库实现以下内容：

* 适用于所有可能的URL和方法的公共和私有API
* 支持通用方法子集的统一API

在每个交换的属性中预定义了端点URL 。除非您要实现新的Exchange API（至少您应该知道自己在做什么），否则不必覆盖它。`api`

### 隐式API方法 <a id="implicit-api-methods"></a>

大多数特定于交易所的API方法都是隐式的，这意味着它们没有在代码中的任何地方明确定义。该库实现了一种声明式方法，用于定义隐式（非统一）交换的API方法。

API的每种方法通常都有自己的端点。该库为属性中的每个特定交换定义了所有端点。在进行交换时，将在端点的列表中为每个端点在交换实例内部创建一个隐式_魔术_方法（aka _部分函数_或_闭包_）。普遍对所有交易所执行此操作。每个生成的方法都可以用和表示法访问。`.apidefineRestApi()/define_rest_api().apicamelCaseunder_score`

端点定义是交易所公开**的所有API URL**的**完整列表**。交换实例化后，此列表将转换为可调用方法。API端点列表中的每个URL都有一个对应的可调用方法。这对于所有交易所都是自动完成的，因此ccxt库支持加密交易所提供的**所有可能的URL**。

每个隐式方法都有一个根据定义构造的唯一名称。例如，私有HTTPS PUT 端点将具有名为/ 的相应交换方法。公共HTTPS GET 端点将产生名为/ 的相应方法，依此类推。`.apihttps://api.exchange.com/order/{id}/cancel.privatePutOrderIdCancel().private_put_order_id_cancel()https://api.exchange.com/market/ticker/{pair}.publicGetTickerPair().public_get_ticker_pair()`

隐式方法采用参数字典，将请求发送到交易所，并按**原样**从API返回交易所特定的JSON结果**（未解析）**。要传递参数，请将其显式添加到与参数名称相同的键下的字典中。对于上面的示例，这看起来像和。`.privatePutOrderIdCancel ({ id: '41987a2b-...' }).publicGetTickerPair ({ pair: 'BTC/USD' })`

建议使用交换的方法不是使用特定于交换的隐式方法，而是使用统一的ccxt方法。如果尚未使用相应的统一方法，则应使用特定于交易所的方法作为后备方法。

要获取一个交换实例的所有可用方法的列表，包括隐式方法和统一方法，您只需执行以下操作：

```text
console.log（new ccxt.kraken（））// JavaScript打印（dir（ccxt.hitbtc（）））＃pythonvar_dump（new \ ccxt \ okcoinusd（））; // PHP
```

### 公共/私人API <a id="public-private-api"></a>

API URL通常分为两组方法，分别称为用于市场数据的_公共API_和用于交易和帐户访问的_专用API_。这些API方法组通常以单词“ public”或“ private”开头。

公用API用于访问市场数据，并且不需要任何身份验证。大多数交易所都向所有人公开提供市场数据（在其汇率限制之下）。使用ccxt库，任何人都可以直接使用市场数据，而无需在交易所注册，也无需设置帐户密钥和密码。

公共API包括以下内容：

* 乐器/交易对
* 价格饲料（汇率）
* 订购书（L1，L2，L3…）
* 交易历史（平仓订单，交易，执行）
* 股票行情（现货/ 24小时价格）
* OHLCV系列图表
* 其他公共端点

要使用私有API进行交易，您需要从/获取交易所的API密钥。这通常意味着向交易所注册并使用您的帐户创建API密钥。大多数交易所要求提供个人信息或身份证明。也可能需要某种验证。

如果您要交易，则需要注册自己，该库不会为您创建帐户或API密钥。一些交易所API公开了用于从代码本身内部注册帐户的接口方法，但是大多数交易所没有。您必须注册并使用其网站创建API密钥。

专用API允许以下内容：

* 管理个人帐户信息
* 查询账户余额
* 通过订立市场和限价单进行交易
* 创建存款地址和资金账户
* 要求提取法定和加密货币资金
* 查询个人未结/未结订单
* 查询保证金/杠杆交易中的头寸
* 获取分类账历史
* 在账户之间转移资金
* 使用商家服务

一些交易所以不同的名称提供相同的逻辑。例如，公共API通常也被称为_市场数据_，_基本_，_市场_，_mapi_，_api_，_价格_等。所有这些都意味着一组访问公众可用数据的方法。私有API通常也称为_交易_，_交易_，_塔皮_，_交易所_，_账户_等。

一些交易所还公开了商家API，该API可让您创建发票并接受来自客户的加密和法定付款。这种API通常称为_商家_，_钱包_，_付款_，_ecapi_（用于电子商务）。

要获取交换实例的所有可用方法的列表，只需执行以下操作：

```text
console.log（new ccxt.kraken（））// JavaScript打印（dir（ccxt.hitbtc（）））＃pythonvar_dump（new \ ccxt \ okcoinusd（））; // PHP
```

### 同步与异步调用 <a id="synchronous-vs-asynchronous-calls"></a>

在CCXT的JavaScript版本中，所有方法都是异步的，并返回使用解码的JSON对象解析的[Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)。在CCXT中，我们使用现代的_async / await_语法来处理Promises。如果您不熟悉该语法，可以[在此处](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)阅读有关它的更多信息。

```text
// JavaScript​（异步（）=> {    让对=等待kraken.publicGetSymbolsDetails（）    让marketIds = Object.keys（pairs ['result']）    让marketId = marketIds [0]    让代码=等待kraken.publicGetTicker（{对：marketId}）    console.log（kraken.id，marketId，代码）}）（）
```

ccxt库在Python 3.5+中支持async / await语法的异步并发模式。异步Python版本将纯[asyncio](https://docs.python.org/3/library/asyncio.html)与[aiohttp](http://aiohttp.readthedocs.io/) [结合](https://docs.python.org/3/library/asyncio.html)使用。在异步模式下，您具有所有相同的属性和方法，但是大多数方法都使用async关键字修饰。如果要使用异步模式，则应链接到子包，如以下示例所示：`ccxt.async_support`

```text
＃Python​导入异步将ccxt.async_support导入为ccxt​异步def print_poloniex_ethbtc_ticker（）：    poloniex = ccxt.poloniex（）    打印（等待poloniex.fetch_ticker（'ETH / BTC'））​asyncio.get_event_loop（）。run_until_complete（print_poloniex_ethbtc_ticker（））
```

在PHP中，所有API方法都是同步的。

### 返回的JSON对象 <a id="returned-json-objects"></a>

所有公共和私有API方法都会原样返回未响应的原始解码JSON对象，以响应交换的响应。统一的API以通用格式返回经过JSON解码的对象，并且在所有交换中结构统一。

### 将参数传递给API方法 <a id="passing-parameters-to-api-methods"></a>

所有可能的API端点的集合因交换而异。大多数方法都接受键值参数的单个关联数组（或Python dict）。参数传递如下：

```text
bitso.publicGetTicker（{book：'eth_mxn'}）// JavaScriptccxt.zaif（）。public_get_ticker_pair（{'pair'：'btc_jpy'}）＃Python$ luno-> public_get_ticker（array（'pair'=>'XBTIDR'））; // PHP
```

有关每次交换可接受的方法参数的完整列表，请查阅API文档。

#### API方法命名约定 <a id="api-method-naming-conventions"></a>

交换方法名称是由类型（公共或私有），HTTP方法（GET，POST，PUT，DELETE）和端点URL路径组成的串联字符串，如以下示例所示：

| 方法名称 | 基本API网址 | 端点网址 |
| :--- | :--- | :--- |
| publicGetIdOrderbook | [https://bitbay.net/API/Public](https://bitbay.net/API/Public) | {id} /订单 |
| publicGetPairs | [https://bitlish.com/api](https://bitlish.com/api) | 对 |
| publicGetJsonMarketTicker | [https://www.bitmarket.net](https://www.bitmarket.net/) | json / {market} / ticker |
| privateGetUserMargin | [https://bitmex.com](https://bitmex.com/) | 用户/保证金 |
| privatePostTrade | [https://btc-x.is/api](https://btc-x.is/api) | 贸易 |
| tapiCancelOrder | [https://yobit.net](https://yobit.net/) | 但是/ CancelOrder |
| … | … | … |

ccxt库支持驼峰表示法（在JavaScript中为首选）和下划线表示法（在Python和PHP中为首选），因此所有方法都可以以任何语言的表示法或编码样式进行调用。这两种符号均可在JavaScript，Python和PHP中使用：

```text
exchange.methodName（）//驼峰式伪代码exchange.method_name（）//下划线伪代码
```

要获取交换实例的所有可用方法的列表，只需执行以下操作：

```text
console.log（new ccxt.kraken（））// JavaScript打印（dir（ccxt.hitbtc（）））＃pythonvar_dump（new \ ccxt \ okcoinusd（））; // PHP
```

### 统一API <a id="unified-api"></a>

统一的ccxt API是交换之间通用的方法的子集。它当前包含以下方法：

* `fetchMarkets ()`：获取从交易所所有可用的市场列表并返回市场（对象与诸如属性的阵列，，等等）。一些交易所没有通过其在线API获取市场列表的方法。对于那些，市场清单是硬编码的。`symbolbasequote`
* `fetchCurrencies ()`：获取所有可用的货币交换，并返回货币（对象与诸如属性的关联的字典，等）。一些交易所没有通过在线API获取货币的手段。对于这些货币，将从市场对中提取货币或对其进行硬编码。`codename`
* `loadMarkets ([reload])`：将市场列表作为由符号索引的对象返回，并将其与交换实例缓存在一起。如果已加载，则返回缓存的市场，除非强制设置标志。`reload = true`
* `fetchOrderBook (symbol[, limit = undefined[, params = {}]])`：获取特定市场交易代码的L2 / L3订单簿。
* `fetchStatus ([, params = {}])`：从交换实例或API（如果有）中硬编码的信息返回有关交换状态的信息。
* `fetchL2OrderBook (symbol[, limit = undefined[, params]])`：特定符号的2级（价格汇总）订单簿。
* `fetchTrades (symbol[, since[, [limit, [params]]]])`：获取特定交易代码的近期交易。
* `fetchTicker (symbol)`：通过交易代码获取最新的报价器数据。
* `fetchBalance ()`：获取余额。
* `createOrder (symbol, type, side, amount[, price[, params]])`
* `createLimitBuyOrder (symbol, amount, price[, params])`
* `createLimitSellOrder (symbol, amount, price[, params])`
* `createMarketBuyOrder (symbol, amount[, params])`
* `createMarketSellOrder (symbol, amount[, params])`
* `cancelOrder (id[, symbol[, params]])`
* `fetchOrder (id[, symbol[, params]])`
* `fetchOrders ([symbol[, since[, limit[, params]]]])`
* `fetchOpenOrders ([symbol[, since, limit, params]]]])`
* `fetchClosedOrders ([symbol[, since[, limit[, params]]]])`
* `fetchMyTrades ([symbol[, since[, limit[, params]]]])`
* …

#### 覆盖统一API参数 <a id="overriding-unified-api-params"></a>

请注意，统一API的大多数方法都接受可选参数。它是一个包含您要覆盖的参数的关联数组（字典，默认情况下为空）。的内容特定于交易所，请参阅交易所的API文档以获取受支持的字段和值。如果您需要将自定义设置或可选参数传递给统一查询，请使用词典。`paramsparamsparams`

```text
// JavaScript（异步（）=> {​    const params = {        'foo'：'bar'，//统一查询中特定于交换的覆盖        'Hello'：'World！'，//有关参数名称的更多详细信息，请参见其文档    }​    //替代项进入统一调用的最后一个参数↓HERE    const结果=等待exchange.fetchOrderBook（符号，长度，参数）}）（）
```

```text
＃Python参数= {    'foo'：'bar'，＃统一查询中特定于交易所的覆盖    'Hello'：'World！'，＃请参阅其文档以获取有关参数名称的更多详细信息}​＃覆盖进入统一调用的最后一个参数↓这里结果= exchange.fetch_order_book（符号，长度，参数）
```

```text
// PHP$ params =数组（    'foo'=>'bar'，//统一查询中特定于交易所的覆盖    'Hello'=>'World！'，//有关参数名称的更多详细信息，请参见其文档}​//覆盖进入统一调用的最后一个参数↓这里$ result = $ exchange-> fetch_order_book（$ symbol，$ length，$ params）;
```

#### 分页 <a id="pagination"></a>

大多数统一方法将返回单个对象或对象（交易，订单，交易等）的纯数组（列表）。但是，很少有交易所（如果有的话）一次返回所有订单，所有交易，所有ohlcv蜡烛或所有交易。大多数情况下，它们的API 输出到一定数量的最新对象。**从时间开始到现在的一刻之间，您无法得到所有对象**。实际上，很少有交易所会容忍或允许这样做。`limit`

为了获取历史订单或交易，用户将需要遍历对象的部分或“页面”中的数据。分页通常意味着_“_循环_获取数据的一部分”_。

在大多数情况下，**要求**用户**至少使用某种类型的分页**以便始终如一地获得预期结果。如果用户未应用任何分页，则大多数方法将返回交换的默认值，该默认值可以从历史记录的开头开始，也可以是最新对象的子集。默认行为（无分页）是特定于交换的！分页方法通常特别用于以下方法：

* `fetchTrades`
* `fetchOHLCV`
* `fetchOrders`
* `fetchOpenOrders`
* `fetchClosedOrders`
* `fetchMyTrades`
* `fetchTransactions`
* `fetchDeposits`
* `fetchWithdrawals`

使用返回对象列表的方法，交换可以提供一种或多种类型的分页。CCXT 默认情况下统一**基于日期的分页**，整个库中的时间戳**以毫秒为单位**。

**处理日期时间和时间戳**

使用UTC日期和时间戳并在它们之间进行转换的方法集：

```text
exchange.parse8601（'2018-01-01T00：00：00Z'）== 1514764800000 //整数，Z = UTCexchange.iso8601（1514764800000）=='2018-01-01T00：00：00Z'// iso8601字符串exchange.seconds（）//整数UTC时间戳，以秒为单位exchange.milliseconds（）//整数UTC时间戳（以毫秒为单位）
```

**基于日期的分页**

这是当前在整个CCXT Unified API中使用的分页类型。用户提供一个**以毫秒为单位**的时间戳（！）和一个数字作为结果。要逐页遍历感兴趣的对象，用户运行以下命令（以下为伪代码，根据所涉及的交换，它可能需要覆盖某些特定于交换的参数）：`sincelimit`

```text
// JavaScript如果（exchange.has ['fetchTrades']）{    let since = exchange.milliseconds（）-86400000 // -1天后    //或者，从某个开始日期时间获取    //让since = exchange.parse8601（'2018-01-01T00：00：00Z'）    让allTrades = []    while（因为<exchange.milliseconds（））{        const symbol = undefined //更改您的符号        const limit = 20 //更改您的限制        const trades =等待exchange.fetchTrades（符号，自此，限制）        如果（trades.length）{            由于= trades [trades.length-1] ['timestamp']            allTrades = allTrades.concat（交易）        }其他{            打破        }    }}
```

```text
＃Python如果exchange.has ['fetchOrders']：    since = exchange.milliseconds（）-86400000＃-1天从现在    ＃或者，从某个开始日期时间获取    ＃因为= exchange.parse8601（'2018-01-01T00：00：00Z'）    all_orders = []    而由于<exchange.milliseconds（）：        symbol = None＃更改您的符号        限制= 20＃更改您的限制        订单=等待exchange.fetch_orders（符号，自限制）        如果len（orders）：            因为= orders [len（orders）-1] ['timestamp']            all_orders + =订单        其他：            打破
```

```text
// PHP如果（$ exchange-> has ['fetchMyTrades']）{    $ since = exchange->毫秒（）-86400000; //从现在开始-1天    //或者，从某个开始日期时间获取    // $ since = $ exchange-> parse8601（'2018-01-01T00：00：00Z'）;    $ all_trades =数组（）;    同时（由于<exchange->毫秒（））{        $ symbol = null; //更改您的符号        $ limit = 20; //更改您的限额        $ trades = $ exchange-> fetchMyTrades（$ symbol，$ since，$ limit）;        如果（count（$ trades））{            $ since = $ trades [count（$ trades）-1] ['timestamp'];            $ all_trades = array_merge（$ all_trades，$ trades）;        }其他{            打破;        }    }}
```

**基于id的分页**

用户提供对象的，查询应从该对象继续返回结果，并提供一个结果编号。这是某些交易所的默认设置，但是此类型尚未统一。要基于对象的ID对对象进行分页，用户将运行以下命令：`from_idlimit`

```text
// JavaScript如果（exchange.has ['fetchTrades']）{    let from_id ='abc123'//所有ID为字符串    让allTrades = []    而（true）{        const symbol = undefined //更改您的符号        const因为=未定义        const limit = 20 //更改您的限制        const params = {            'from_id'：from_id，//特定于交易所的非统一参数名称        }        const trades =等待exchange.fetchTrades（符号，自定义，限制，参数）        如果（trades.length）{            from_id = trades [trades.length-1] ['id']            allTrades.push（交易）        }其他{            打破        }    }}
```

```text
＃Python如果exchange.has ['fetchOrders']：    from_id ='abc123'＃所有ID为字符串    all_orders = []    而True：        symbol = None＃更改您的符号        由于=无        限制= 20＃更改您的限制        参数= {            'from_id'：from_id，＃特定于交易所的非统一参数名称        }        订单=等待exchange.fetch_orders（符号，因为，限制，参数）        如果len（orders）：            from_id = orders [len（orders）-1] ['id']            all_orders + =订单        其他：            打破
```

```text
// PHP如果（$ exchange-> has ['fetchMyTrades']）{    $ from_id ='abc123'//所有ID为字符串    $ all_trades =数组（）;    而（true）{        $ symbol = null; //更改您的符号        $ since = null;        $ limit = 20; //更改您的限额        $ params =数组（            'from_id'=> $ from_id，//特定于交易所的非统一参数名称        ）;        $ trades = $ exchange-> fetchMyTrades（$ symbol，$ since，$ limit，$ params）;        如果（count（$ trades））{            $ from_id = $ trades [count（$ trades）-1] ['id'];            $ all_trades = array_merge（$ all_trades，$ trades）;        }其他{            打破;        }    }}
```

**基于页码的（游标）分页**

用户提供页码或_初始“光标”_值。交换返回结果页面和_下一个“游标”_值以继续。大多数实现这种分页的交换都将在响应本身内返回下一个游标，或者将在HTTP响应头中返回下一个游标值。

在这里看到的范例：[https://github.com/ccxt/ccxt/blob/master/examples/py/gdax-fetch-my-trades-pagination.py](https://github.com/ccxt/ccxt/blob/master/examples/py/gdax-fetch-my-trades-pagination.py)

在循环的每次迭代中，用户都必须使用下一个光标并将其放入重写的参数中，以进行下一个查询（在下一个迭代中）：

```text
// JavaScript如果（exchange.has ['fetchTrades']）{    let page = 0 //交换特定的类型和值    让allTrades = []    而（true）{        const symbol = undefined //更改您的符号        const因为=未定义        const limit = 20 //更改您的限制        const params = {            'page'：page，//特定于交易所的非统一参数名称        }        const trades =等待exchange.fetchTrades（符号，自定义，限制，参数）        如果（trades.length）{            //不是线程Safu和特定于交换的！            页面= exchange.last_json_response ['光标']            allTrades.push（交易）        }其他{            打破        }    }}
```

```text
＃Python如果exchange.has ['fetchOrders']：    cursor = 0＃特定于交易所的类型和值    all_orders = []    而True：        symbol = None＃更改您的符号        由于=无        限制= 20＃更改您的限制        参数= {            'cursor'：光标，＃特定于交易所的非统一参数名称        }        订单=等待exchange.fetch_orders（符号，因为，限制，参数）        如果len（orders）：            ＃不是线程safu和特定于交换的！            游标= exchange.last_response_headers ['CB-AFTER']            all_orders + =订单        其他：            打破
```

```text
// PHP如果（$ exchange-> has ['fetchMyTrades']）{    $ start ='0'//特定于交易所的类型和值    $ all_trades =数组（）;    而（true）{        $ symbol = null; //更改您的符号        $ since = null;        $ limit = 20; //更改您的限额        $ params =数组（            'start'=> $ start，//特定于交易所的非统一参数名称        ）;        $ trades = $ exchange-> fetchMyTrades（$ symbol，$ since，$ limit，$ params）;        如果（count（$ trades））{            //不是线程Safu和特定于交换的！            $ start = $ exchange-> last_json_response ['next'];            $ all_trades = array_merge（$ all_trades，$ trades）;        }其他{            打破;        }    }}
```

## 市场数据 <a id="market-data"></a>

* [订单/市场深度](https://github.com/ccxt/ccxt/wiki/Manual#order-book--market-depth)
  * [市场价格](https://github.com/ccxt/ccxt/wiki/Manual#market-price)
* [价格行情](https://github.com/ccxt/ccxt/wiki/Manual#price-tickers)
  * [分别由符号](https://github.com/ccxt/ccxt/wiki/Manual#individually-by-symbol)
  * [一下子](https://github.com/ccxt/ccxt/wiki/Manual#all-at-once)
* [OHLCV烛台图表](https://github.com/ccxt/ccxt/wiki/Manual#ohlcv-candlestick-charts)
* [公开交易](https://github.com/ccxt/ccxt/wiki/Manual#public-trades)

### 订购书 <a id="order-book"></a>

交易所通过开价（买入）和开价（卖出）价格，交易量和其他数据公开未结订单的信息。通常，有一个单独的端点，用于查询特定市场的_订单簿的_当前状态（堆栈框架）。订单通常也称为_市场深度_。订单簿信息用于交易决策过程中。

用于获取特定交易品种的订单的方法称为或。它接受符号和带有附加参数的可选词典（如果特定交换所支持）。提取订单的方法如下所示：`fetchOrderBookfetch_order_book`

```text
// JavaScript延迟= 2000 //毫秒=秒* 1000（异步（）=> {    对于（exchange.markets中的符号）{        console.log（等待exchange.fetchOrderBook（符号））        等待新的Promise（resolve => setTimeout（resolve，delay））//速率限制    }}）（）
```

```text
＃Python导入时间延迟= 2＃秒用于exchange.markets中的符号：    打印（exchange.fetch_order_book（符号））    time.sleep（delay）＃速率限制
```

```text
// PHP$ delay = 2000000; //微秒=秒* 1000000foreach（$ exchange-> markets as $ symbol => $ market）{    var_dump（$ exchange-> fetch_order_book（$ symbol））;    usleep（$ delay）; //速率限制}
```

#### 订单簿结构 <a id="order-book-structure"></a>

退回的订单簿的结构如下：

```text
{    “出价”：[        [价格，金额]，// [浮动，浮动]        [价格，金额]，        ...    ]，    “问”：[        [价格，金额]，        [价格，金额]，        ...    ]，    'timestamp'：1499280391811，// Unix时间戳，以毫秒为单位（秒* 1000）    'datetime'：'2017-07-05T18：47：14.692Z'，// ISO8601日期时间字符串（以毫秒为单位）    'nonce'：1499280391811，//订单簿快照的唯一标识符不断增加}
```

**如果所讨论的交换未在API响应中提供相应的值，则时间戳和日期时间可能会丢失（）。`undefined/None/null`**

价格和金额都是浮动的。bids数组按价格降序排列。最佳（最高）出价是第一要素，而最低（最低）出价是最后要素。asks数组按价格升序排序。最佳（最低）要价是第一要素，最差（最高）要价是最后要素。如果交易所的订单簿中没有相应的订单，则出价/要价数组可以为空。

交易所可以返回各种详细程度的订单堆栈以进行分析。它要么包含每个订单的详细信息，要么聚合在一起，而价格和数量对订单进行分组和合并的细节则略少一些。拥有更多细节需要更多流量和带宽，并且通常较慢，但具有更高精度的好处。较少的细节通常会更快，但是在某些非常特殊的情况下可能不够。

#### 订单簿结构注意事项 <a id="notes-on-order-book-structure"></a>

* 这是交易所生成此订单簿响应的时间（在将其回复给您之前）。如手册中所述，可能会缺少（），并非所有交易所都在此处提供时间戳。如果已定义，则它是自1970年1月1日00:00:00以来的UTC时间戳（**以毫秒为单位）**。`orderbook['timestamp']undefined/None/null`
* 某些交易所可能会按订单ID为订单簿中的订单编制索引，在这种情况下，订单ID可能会作为出价的第三要素返回并询问：。没有聚合的L3订单通常是这种情况。订单（如果显示在订单簿中）是指订单簿，不一定与所有者或其他人所看到的来自交易所数据库的实际订单ID相符。订单ID是订单簿中该行的ID ，但不一定是该订单的True （不过，它们也可能相等，这取决于所涉及的交易所）。`[ price, amount, id ]ididid`
* 在某些情况下，交易所可以为L2聚合订单簿提供每个聚合级别的订单计数，在这种情况下，订单计数可能作为投标的第三要素返回并询问：。该告诉多少订单竞标每个价格水平汇总，并要求。`[ price, amount, count ]count`

#### 市场深度 <a id="market-depth"></a>

一些交易所接受该函数额外参数的字典。**所有额外的都是特定于交易所的（非统一的）**。如果要覆盖特定参数（例如订单簿的深度），则需要咨询交易所文档。您可以通过指定一个限制参数和特定于交易所的额外信息来获得有限数量的退货订单或所需的汇总水平（又称_市场深度_），如下所示：`fetchOrderBook () / fetch_order_book ()`**`params`**`params`

```text
// JavaScript​（异步功能测试（）{    const ccxt = require（'ccxt'）    const exchange =新的ccxt.bitfinex（）    常量限制= 5    常量订单=等待exchange.fetchOrderBook（'BTC / USD'，限制，{        //此参数是特定于交换的，每次交换时所有额外的参数都有唯一的名称        'group'：1，// // 1 =订单按价格分组，0 =订单分开    }）}）（）
```

```text
＃Python​导入ccxt＃在订单簿的每一侧最多返回十个投标限制= 10ccxt.cex（）。fetch_order_book（'BTC / USD'，限制）
```

```text
// PHP​//通过id实例化交换$ exchange ='\\ ccxt \\ kraken';$ exchange =新的$ exchange（）;//例如，每边最多十个订单$ limit = 20;var_dump（$ exchange-> fetch_order_book（'BTC / USD'，$ limit））;
```

细节级别或订单簿聚合级别通常用数字标记，例如L1，L2，L3…

* **L1**：较少的详细信息，用于快速获取非常基本的信息，即仅是市场价格。它看起来像是订单簿中的一个订单。
* **L2**：最常见的聚合级别，其中按价格对订单量进行分组。如果两个订单的价格相同，则它们显示为一个订单，其数量等于其总金额。这很可能是您实现大多数目的所需的聚合级别。
* **L3**：最详细的级别，没有聚合，其中每个订单与其他订单分开。此LOD自然在输出中包含重复项。因此，如果两个订单的价格相等，则它们**不会**合并在一起，并且取决于交易所的匹配引擎来决定其在堆叠中的优先级。您真的不需要L3详细信息即可成功交易。实际上，您很可能根本不需要它。因此，某些交易所不支持它，并且总是返回汇总的订单簿。

如果要获取L2订单簿，无论交换是否返回，都可以使用或统一方法。`fetchL2OrderBook(symbol, limit, params)fetch_l2_order_book(symbol, limit, params)`

该参数不能保证出价或要价的数量始终等于。它指定上限或最大值，因此有时可能会少于出价或要价，但决不会超过出价或要价。当交易所在订单簿上没有足够的订单时，就是这种情况。`limitlimitlimitlimit`

#### 市场价 <a id="market-price"></a>

为了获得当前的最佳价格（查询市场价格）并计算买卖价差，请从买价和卖价中选择第一个元素，如下所示：

```text
// JavaScript让订单簿= exchange.fetchOrderBook（exchange.symbols [0]）让出价= orderbook.bids.length？orderbook.bids [0] [0]：未定义让我们问= orderbook.asks.length？orderbook.asks [0] [0]：未定义让传播=（出价&&询问）？询问-出价：未定义console.log（exchange.id，“市场价格”，{出价，要价，价差}）
```

```text
＃Python订单簿= exchange.fetch_order_book（exchange.symbols [0]）如果len（orderbook ['bids']）> 0，则bid = orderbook ['bids'] [0] [0]否则无ask = orderbook ['asks'] [0] [0]如果len（orderbook ['asks']）> 0否则无点差=（询问-出价）是否（出价并询问）否则无打印（exchange.id，“市场价格”，{“出价”：出价，“询问”：询问，“价差”：价差}）
```

```text
// PHP$ orderbook = $ exchange-> fetch_order_book（$ exchange-> symbols [0]）;$ bid = count（$ orderbook ['bids']）吗？$ orderbook ['bids'] [0] [0]：空；$ ask =计数（$ orderbook ['asks']）？$ orderbook ['asks'] [0] [0]：空；$ spread =（$ bid && $ ask）？$ ask-$ bid：null;$ result =数组（'bid'=> $ bid，'ask'=> $ ask，'spread'=> $ spread）;var_dump（$ exchange-> id，'market price'，$ result）;
```

### 价格行情 <a id="price-tickers"></a>

价格行情包含最近一段时间内（通常持续24小时）特定市场/符号的统计信息。提取行情的方法是：

```text
fetchTicker（symbol，params = {}）//用于一个股票fetchTickers（symbol，params = {}）//一次用于所有股票
```

检查交换实例的和属性，以确定所讨论的交换是否确实支持这些方法。`exchange.has['fetchTicker']exchange.has['fetchTickers']`

#### 股票代号结构 <a id="ticker-structure"></a>

股票代码的结构如下：

```text
{    '符号'：市场的字符串符号（'BTC / USD'，'ETH / BTC'，...）    'info'：{来自Exchange API的原始未修改的未分析回复}，    'timestamp'：int（自1970年1月1日以来的64位Unix时间戳，以毫秒为单位）    'datetime'：ISO8601日期时间字符串（以毫秒为单位）    'high'：浮动，//最高价    'low'：浮动，//最低价格    'bid'：浮动，//当前的最佳买入价    'bidVolume'：float，//当前的最佳出价（购买）金额（可能缺失或未定义）    '问'：浮动，//当前的最佳卖价    'askVolume'：float，//当前的最佳卖出（卖出）金额（可能缺失或不确定）    'vwap'：浮动，//成交量加权平均价格    'open'：浮动，//开盘价    'close'：float，//最后一笔交易的价格（当前期间的收盘价）    'last'：float，//与`close`相同，为方便起见重复    'previousClose'：float，//上一时期的收盘价    'change'：float，//绝对变化，`last-open`    '百分比'：浮点数，//相对变化量，（（change / open）* 100`    'average'：float，//平均价格，（（last + open）/ 2`    'baseVolume'：float，//最近24小时交易的基础货币量    'quoteVolume'：float，//最近24小时交易的报价货币量}
```

#### 股票代号结构注意事项 <a id="notes-on-ticker-structure"></a>

* 这是订单中当前最佳出价的数量（金额）。`bidVolume`
* 这是订单中当前最佳卖出量（数量）。`askVolume`
* 的是基本货币交易的在过去的24小时的量（买或卖）。`baseVolume`
* 该是报价货币交易（买入或卖出）在过去24小时的量。`quoteVolume`

**股票报价结构中的所有价格均为报价货币。返回的代码结构中的某些字段可能未定义/无/为空。**

```text
基础货币↓             BTC / USDT             ETH / BTC            DASH / ETH                    ↑报价货币
```

时间戳和日期时间都是以毫秒为单位的世界标准时间（UTC）。

* `ticker['timestamp']`是交易所生成此响应的时间（在将其回复给您之前）。如手册中所述，它可能会丢失（），并非所有交易所都在此处提供时间戳。如果已定义，则它是自1970年1月1日00:00:00以来的UTC时间戳（**以毫秒为单位）**。`undefined/None/null`
* `exchange.last_response_headers['Date']`是最后一次收到的HTTP响应（来自HTTP标头）的日期时间字符串。“日期”解析器应遵守此处指定的时区。日期时间的精度为1秒1000毫秒。消息起源于以下标准时，由交换服务器设置该日期：
  * [https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html\#sec14.18](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.18)
  * [https://tools.ietf.org/html/rfc1123\#section-5.2.14](https://tools.ietf.org/html/rfc1123#section-5.2.14)
  * [https://tools.ietf.org/html/rfc822\#section-5](https://tools.ietf.org/html/rfc822#section-5)

尽管有些交易所确实将订单簿的最高买/卖价格混入了其股票行情中（有些交易所甚至提供了最高买/卖量），但您不应将股票作为替代股票。股票报价的主要目的是提供统计数据，因此将其视为“实时24小时OHLCV”。众所周知，交易所通过对这些查询施加更严格的速率限制来阻止频繁的请求。如果您需要统一的方式来获取出价，并要求您改为使用家庭。`fetchOrderBookfetchTickerfetchL[123]OrderBook`

要获取历史价格和数量，请在可用的地方使用统一的方法。[`fetchOHLCV`](https://github.com/ccxt/ccxt/wiki/Manual#ohlcv-candlestick-charts)

提取行情的方法：

* `fetchTicker (symbol[, params = {}])`，符号是必需的，参数是可选的
* `fetchTickers ([symbols = undefined[, params = {}]])`，两个参数都是可选的

#### 单独通过符号 <a id="individually-by-symbol"></a>

要从交易所获取特定交易对或特定交易品种的个人报价数据，请调用：`fetchTicker (symbol)`

```text
// JavaScript如果（exchange.has ['fetchTicker']）{    console.log（await（exchange.fetchTicker（'BTC / USD'）））// BTC / USD的代码    让符号= Object.keys（exchange.markets）    让random = Math.floor（Math.random（）*（symbols.length-1））    console.log（exchange.fetchTicker（symbols [random]））//随机符号的代码}
```

```text
＃Python随机导入如果（exchange.has ['fetchTicker']）：    print（exchange.fetch_ticker（'LTC / ZEC'））＃LTC / ZEC的代码    符号=列表（exchange.markets.keys（））    print（exchange.fetch_ticker（random.choice（symbols）））＃代码随机符号
```

```text
// PHP（不要忘记正确设置时区！）如果（$ exchange-> has ['fetchTicker']）{    var_dump（$ exchange-> fetch_ticker（'ETH / CNY'））; // ETH / CNY的代码    $ symbols = array_keys（$ exchange-> markets）;    $ random = rand（）％计数（$符号）；    var_dump（$ exchange-> fetch_ticker（$ symbols [$ random]））; //随机符号的代码}
```

#### 一次全部 <a id="all-at-once"></a>

一些交易所（并非全部）还支持一次提取所有股票。有关详细信息，请参见[他们的文档](https://github.com/ccxt/ccxt/wiki/Manual#exchanges)。您可以通过一次调用来获取所有报价，如下所示：

```text
// JavaScript如果（exchange.has ['fetchTickers']）{    console.log（await（exchange.fetchTickers（）））//通过其符号索引的所有股票}
```

```text
＃Python如果（exchange.has ['fetchTickers']）：    print（exchange.fetch_tickers（））＃所有代号均由其符号索引
```

```text
// PHP如果（$ exchange-> has ['fetchTickers']）{    var_dump（$ exchange-> fetch_tickers（））; //所有代码均由其符号索引}
```

提取所有股票比提取单个股票需要更多的流量。另外，请注意，某些交易所对所有代码的后续提取都设置了更高的速率限制（有关详细信息，请参见相应端点上的文档）。**就限速而言，通话费用通常高于平均水平**。如果您只需要一个股票，则通过特定符号进行提取也将更快。您可能只希望在确实需要所有报价器的情况下才提取所有报价器，并且很可能不希望在一分钟左右的时间内频繁提取fetchTickers。**`fetchTickers()`**

此外，某些交易所可能会对呼叫施加其他要求，有时由于所讨论的交易所交易平台的API限制，您无法获取所有交易品种的代码。但是，某些交易所接受HTTP URL查询参数中的符号列表，因为URL长度有限，在极端情况下，交易所可以拥有成千上万的市场-所有符号列表根本不适合URL，因此必须是其符号的有限子集。有时，还有其他一些原因要求提供符号列表，并且您一次可以获取的符号数量可能会受到限制，但是无论有何限制，都应归咎于交换。要将感兴趣的符号传递给交易所，您可以提供字符串列表作为fetchTickers的第一个参数：`fetchTickers()`

```text
// JavaScript如果（exchange.has ['fetchTickers']）{    console.log（await（exchange.fetchTickers（['ETH / BTC'，'LTC / BTC']）））//列出的代码按其符号索引}
```

```text
＃Python如果（exchange.has ['fetchTickers']）：    print（exchange.fetch_tickers（['ETH / BTC'，'LTC / BTC']））＃列出的代码按其符号索引
```

```text
// PHP如果（$ exchange-> has ['fetchTickers']）{    var_dump（$ exchange-> fetch_tickers（array（'ETH / BTC'，'LTC / BTC'））））; //列出的代码按其符号索引}
```

请注意，在大多数情况下，不需要符号列表，但是如果要处理交易所可能施加的所有可能的限制，则必须添加其他逻辑。

像Unified CCXT API的大多数方法一样，fetchTickers的最后一个参数是用于覆盖向交换发送的请求参数的参数。`params`

返回值的结构如下：

```text
{    'info'：{...}，//来自交换的原始JSON响应    'BTC / USD'：{...}，// BTC / USD的单个代码    'ETH / BTC'：{...}，// ETH / BTC的代码    ...}
```

目前正在寻求一种从所有交易所（甚至没有相应API端点的交易所）获取所有报价的通用解决方案，该部分将很快更新。

```text
🚧正在施工🚧
```

**异步模式/并发**

```text
🚧正在施工🚧
```

### OHLCV烛台图 <a id="ohlcv-candlestick-charts"></a>

```text
-目前正在大力发展，感谢捐助
```

大多数交易所都有用于获取OHLCV数据的端点，但是其中一些没有。名为的交换布尔值（true / false）属性指示交换是否支持烛台数据系列。`has['fetchOHLCV']`

该方法以以下方式声明：`fetchOHLCV`

```text
fetchOHLCV（符号，时间段=“ 1m”，因为=未定义，限制=未定义，参数= {}）
```

您可以调用Unified / 方法来获取特定符号的OHLCV蜡烛列表，如下所示：`fetchOHLCVfetch_ohlcv`

```text
// JavaScriptlet sleep =（ms）=>新的Promise（resolve => setTimeout（resolve，ms））;如果（exchange.has.fetchOHLCV）{    对于（exchange.markets中的符号）{        等待睡眠（exchange.rateLimit）//毫秒        console.log（等待exchange.fetchOHLCV（符号，'1m'））//一分钟    }}
```

```text
＃Python导入时间如果exchange.has ['fetchOHLCV']：    用于exchange.markets中的符号：        time.sleep（exchange.rateLimit / 1000）＃time.sleep要秒        打印（符号，exchange.fetch_ohlcv（符号，'1d'））＃一天
```

```text
// PHP如果（$ exchange-> has ['fetchOHLCV']）{    foreach（$ exchange-> markets as $ symbol => $ market）{        usleep（$ exchange-> rateLimit * 1000）; // usleep想要微秒        var_dump（$ exchange-> fetch_ohlcv（$ symbol，'1M'））; // 一个月    }}
```

要获取可用于交换的时间表列表，请参阅属性。注意，只有在为true 时才填充它。`timeframeshas['fetchOHLCV']`

**您的请求可以返回多长时间有一个限制。**大多数交易所不允许查询过去的详细烛台历史记录（例如1分钟和5分钟时间范围的烛台历史​​记录）。他们通常会保留一定数量的最新蜡烛，例如在任何时间范围内都可以容纳1000支最后一支蜡烛，足以满足大多数需求。您可以通过连续获取（也称为_REST轮询_）最新的OHLCV并将其存储在CSV文件或数据库中来解决该限制。

**请注意，直到关闭蜡烛为止（直到下一个蜡烛开始），来自上一个（当前）蜡烛的信息可能是不完整的。**

与大多数其他统一和隐式方法一样，该方法接受extra的关联数组（字典）作为其最后一个参数，该数组用于`fetchOHLCVparams`[覆盖](https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-api-params)在请求中发送给交易所的[默认值](https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-api-params)。的内容特定于交易所，请参阅交易所的API文档以获取受支持的字段和值。`params`

该参数是一个**以毫秒为单位**的整数UTC时间戳（整个库中所有使用统一方法的地方）。`since`

如果未指定，则该方法将返回时间范围，这是交易所本身的默认时间范围。这不是错误。一些交易所从开始就返回蜡烛，另一些交易所仅返回最近的蜡烛，这是交易所的默认行为。因此，在不指定返回蜡烛范围的情况下，将特定于交易所。人们应该通过辩论，以确保准确获得所需的历史范围。`sincefetchOHLCVsincesince`

#### OHLCV结构 <a id="ohlcv-structure"></a>

上面显示的fetchOHLCV方法返回由以下结构表示的OHLCV蜡烛的列表（平面数组）：

```text
[    [        1504541580000，//以毫秒为单位的UTC时间戳，整数        4235.4，//（O）笔价格，浮动        4240.6，//（最高）浮动价格        4230.0，//（L）最高价浮动        4230.7，//（C）亏损价格，浮动        37.72941911 //（V）olume（以基础货币计），浮点数    ]，    ...]
```

返回的蜡烛列表按升序（历史/时间顺序）排序，最早的蜡烛排在前，最近的蜡烛排在后。

#### OHLCV仿真 <a id="ohlcv-emulation"></a>

某些交易所不提供任何OHLCV方法，对于这些交易所，ccxt库将模拟[Public Trades的](https://github.com/ccxt/ccxt/wiki/Manual#trades-executions-transactions) OHLCV蜡烛。在这种情况下，您将看到。但是，由于交易历史通常非常有限，因此模拟的fetchOHLCV方法仅涵盖最新信息，并且在没有其他选择可用时，只能用作备用。`exchange.has['fetchOHLCV'] = 'emulated'`

**警告：fetchOHLCV仿真是实验性的！**

### 交易，执行，交易 <a id="trades-executions-transactions"></a>

```text
-目前正在大力发展，感谢捐助
```

您可以调用Unified / 方法来获取特定交易品种的最新交易清单。该方法以以下方式声明：`fetchTradesfetch_tradesfetchTrades`

```text
异步fetchTrades（符号，因为=未定义，限制=未定义，参数= {}）
```

例如，如果您要依次打印所有交易品种的近期交易（请注意rateLimit！），您可以这样做：

```text
// JavaScript如果（exchange.has ['fetchTrades']）{    let sleep =（ms）=>新的Promise（resolve => setTimeout（resolve，ms））;    对于（exchange.markets中的符号）{        等待睡眠（exchange.rateLimit）//毫秒        console.log（等待exchange.fetchTrades（符号））    }}
```

```text
＃Python导入时间如果exchange.has ['fetchTrades']：    for exchange.markets中的符号：＃确保已调用loadMarkets（）或load_markets（）方法。        time.sleep（exchange.rateLimit / 1000）＃time.sleep要秒        打印（符号，exchange.fetch_trades（符号））
```

```text
// PHP如果（$ exchange-> has ['fetchTrades']）{    foreach（$ exchange-> markets as $ symbol => $ market）{        usleep（$ exchange-> rateLimit * 1000）; // usleep想要微秒        var_dump（$ exchange-> fetch_trades（$ symbol））;    }}
```

上面显示的fetchTrades方法返回交易的有序列表（一个平面数组，按时间戳从小到大排序，最早的交易在先，最新的交易在后）。交易清单由以下结构表示：

```text
[    {        'info'：{...}，//原始解码的JSON原样        'id'：'12345-67890：09876/54321'，//字符串交易ID        'timestamp'：1502962946216，// Unix时间戳以毫秒为单位        'datetime'：'2017-08-17 12：42：48.000'，// ISO8601日期时间（以毫秒为单位）        'symbol'：'ETH / BTC'，//符号        'order'：'12345-67890：09876/54321'，//字符串顺序ID或未定义/无/空        'type'：'limit'，//订单类型，'market'，'limit'或未定义/无/空        'side'：'buy'，//交易方向，'buy'或'sell'        'price'：0.06917684，//报价货币的浮动价格        'amount'：1.5，//基础货币数量    }，    ...]
```

尽管有些交易所不返回交易的类型，边，交易ID或订单ID，但大多数交易所会为每笔交易返回上述大多数字段。在大多数情况下，可以保证每笔交易都有时间戳，日期时间，符号，价格和金额。

第二个可选参数按时间戳减少数组，第三个参数按返回项目的数量（计数）减少。`sincelimit`

如果用户未指定，则该方法将从交易所返回默认的公共交易范围。默认设置是特定于交易所的，一些交易所将从在交易所中列出一对交易对的日期开始返回交易，其他交易所将返回减少的交易集合（例如最近24小时，最近100次交易等）。如果用户希望精确控制时间范围，则用户负责指定自变量。`sincefetchTradessince`

大多数统一方法将返回单个对象或对象（交易）的纯数组（列表）。但是，很少有交易所（如果有的话）会一次返回所有交易。大多数情况下，它们的API 输出到一定数量的最新对象。**从时间开始到现在的一刻之间，您无法得到所有对象**。实际上，很少有交易所会容忍或允许这样做。`limit`

为了获取历史交易，用户将需要遍历对象的部分或“页面”中的数据。分页通常意味着_“_循环_获取数据的一部分”_。

在大多数情况下，**要求**用户**至少使用某种类型的分页**以便始终如一地获得预期结果。

另一方面，**某些交易所根本不支持对公共交易的分页**。通常，交易所仅提供最新的交易。

的/ 方法还接受可选的（缔合键阵列/字典，通过缺省为空）作为它的第四个参数。您可以使用它来将额外的参数传递给方法调用或覆盖特定的默认值（由交换所支持）。有关更多详细信息，请参见API文档以进行交换。`fetchTrades ()fetch_trades()params`

```text
🚧正在施工🚧
```

## 贸易 <a id="trading"></a>

为了能够访问您的用户帐户，通过下达市场和限价单，查询余额，存入和提取资金等进行算法交易，您需要从要与之交易的每个交易所获取API密钥以进行身份​​验证。他们通常在用户帐户设置的单独选项卡或页面上提供该功能。API密钥是特定于交换的，在任何情况下都不能交换。

### 认证方式 <a id="authentication"></a>

如果提供了正确的API密钥，则会自动处理所有交换的身份验证。身份验证过程通常遵循以下模式：

1. 生成新的随机数。随机数是一个整数，通常是Unix时间戳，以秒或毫秒为单位（自1970年1月1日开始）。随机数对于特定请求应该是唯一的，并且会不断增加，这样就不会有两个请求共享相同的随机数。每个下一个请求应具有比上一个请求更大的随机数。**默认的随机数是32位Unix时间戳，以秒为单位。**
2. 将public apiKey和nonce附加到其他端点参数（如果有），然后序列化整个对象以进行签名。
3. 使用HMAC-SHA256 / 384/512或MD5与您的密钥签署序列化的参数。
4. 将Hex或Base64中的签名附加到HTTP标头或正文中，并将现时值附加到HTTP标头或正文中。

这个过程可能因交换而异。一些交易所可能希望签名使用不同的编码，其中一些交易所的标头和主体参数名称和格式有所不同，但是所有的通用模式都相同。

**您不应在同时运行，在单独的脚本中或在多个线程中同时运行的多个交换实例之间共享同一API密钥对。同时使用来自不同实例的相同密钥对可能会导致各种意外行为。**

**请勿在其他软件中重复使用API​​密钥！其他软件会使您的随机数过高。如果收到InvalidNonce错误，请确保首先生成一个新的新密钥对。**

身份验证已经为您完成，因此除非您要实现新的交换类，否则无需手动执行任何步骤。您唯一需要进行交易的就是实际的API密钥对。

### API密钥设置 <a id="api-keys-setup"></a>

API凭证通常包括以下内容：

* `apiKey`。这是您的公共API密钥和/或令牌。这部分_是非秘密的_，包含在您的请求标头或正文中，并通过HTTPS以开放文本的形式发送，以标识您的请求。它通常是十六进制或Base64编码的字符串或UUID标识符。
* `secret`。这是您的私钥。保密，不要告诉任何人。它用于在将请求发送到交易所之前在本地对您的请求进行签名。私钥不会在请求-响应过程中通过Internet发送，因此不应发布或通过电子邮件发送。它与随机数一起使用以生成加密强度高的签名。该签名与您的公共密钥一起发送以验证您的身份。每个请求都具有唯一的随机数，因此也具有唯一的加密签名。
* `uid`。某些交换（并非全部）也生成用户ID或_uid_的简称。它可以是字符串或数字文字。如果交换明确要求，则应进行设置。有关详细信息，请参见[他们的文档](https://github.com/ccxt/ccxt/wiki/Manual#exchanges)。
* `password`。一些交易所（并非全部）也需要您的密码/短语进行交易。如果交换明确要求，则应设置此字符串。有关详细信息，请参见[他们的文档](https://github.com/ccxt/ccxt/wiki/Manual#exchanges)。

为了创建API密钥，请在交易所网站上的用户设置中找到API选项卡或按钮。然后创建您的密钥并将其复制粘贴到您的配置文件中。您的配置文件权限应进行适当设置，除所有者外，其他任何人都无法读取。

**切记要确保您的apiKey和密钥安全，防止未经授权的使用，请勿将其发送或告知任何人。密钥泄漏或安全漏洞会给您造成资金损失。**

要设置交易交易所，只需将API凭据分配给现有的交易所实例，或在实例化时将它们传递给交易所构造函数，如下所示：

```text
// JavaScript​const ccxt = require（'ccxt'）​// 任何时候让kraken = new ccxt.kraken（）kraken.apiKey ='YOUR_KRAKEN_API_KEY'kraken.secret ='YOUR_KRAKEN_SECRET_KEY'​//实例化时let okcoinusd = new ccxt.okcoinusd（{    apiKey：“ YOUR_OKCOIN_API_KEY”，    机密：“ YOUR_OKCOIN_SECRET_KEY”，}）​//来自变量IDconst exchangeId ='binance'    ，exchangeClass = ccxt [exchangeId]    ，exchange = new exchangeClass（{        'apiKey'：'YOUR_API_KEY'，        '秘密'：'YOUR_SECRET'，        “超时”：30000，        'enableRateLimit'：是的，    }）
```

```text
＃Python​导入ccxt​＃ 任何时候bitfinex = ccxt.bitfinex（）bitfinex.apiKey ='YOUR_BFX_API_KEY'bitfinex.secret ='YOUR_BFX_SECRET'​＃实例化时hitbtc = ccxt.hitbtc（{    'apiKey'：'YOUR_HITBTC_API_KEY'，    '秘密'：'YOUR_HITBTC_SECRET_KEY'，}）​＃来自变量IDexchange_id ='binary'exchange_class = getattr（ccxt，exchange_id）exchange = exchange_class（{    'apiKey'：'YOUR_API_KEY'，    '秘密'：'YOUR_SECRET'，    “超时”：30000，    'enableRateLimit'：是的，}）
```

```text
// PHP​包括“ ccxt.php”​// 任何时候$ quoinex =新的\ ccxt \ quoinex（）;$ quoinex-> apiKey ='YOUR_QUOINE_API_KEY';$ quoinex-> secret ='YOUR_QUOINE_SECRET_KEY';​//实例化时$弱=新\ ccxt \弱（数组（    'apiKey'=>'YOUR_ZAIF_API_KEY'，    '秘密'=>'YOUR_ZAIF_SECRET_KEY'））；​//来自变量ID$ exchange_id ='二进制';$ exchange_class =“ \\ ccxt \\ $ exchange_id”;$ exchange =新的$ exchange_class（数组（    'apiKey'=>'YOUR_API_KEY'，    '秘密'=>'YOUR_SECRET'，    '超时'=> 30000，    'enableRateLimit'=>是，））；
```

请注意，如果您在开始交易之前未设置API凭据，则您的私人请求将会失败，并出现异常或错误。为避免字符转义，请**始终用单引号**而不是双引号（，）**书写凭据**。`'VERY_GOOD'"VERY_BAD"`

### 查询账户余额 <a id="querying-account-balance"></a>

要查询余额并获取可用于交易的资金或锁定在订单中的资金，请使用以下方法：`fetchBalance`

```text
fetchBalance（参数= {}）
```

#### 平衡结构 <a id="balance-structure"></a>

返回的余额结构如下：

```text
{    'info'：{...}，//原始的未解析的未解析的回复，包含详细信息​    // ------------------------------------------------ -------------------------    //首先按资金可用情况编制索引，然后再按货币编制索引​    'free'：{//可用货币交易的货币        'BTC'：321.00，//浮动...        '美元'：123.00，        ...    }，​    'used'：{...}，//货币持有，锁定，冻结或未决的货币​    'total'：{...}，//总计（免费+使用），按货币​    // ------------------------------------------------ -------------------------    //首先按货币索引，然后按资金可用性索引​    'BTC'：{//字符串，三字母的货币代码，大写        'free'：321.00 //浮动，可用于交易的资金        'used'：234.00，//浮动资金，暂停付款，锁定，冻结或待处理        'total'：555.00，//浮动，总余额（免费+已用）    }，​    '美元'： { // ...        '免费'：123.00 // ...        '二手'：456.00，        '总计'：579.00，    }，​    ...}
```

某些交易所可能不会返回全部余额信息。许多交易所不退还您的空帐户或未使用帐户的余额。在这种情况下，返回的余额结构中可能会缺少某些货币。

```text
// JavaScript（异步（）=> {    console.log（等待exchange.fetchBalance（））}）（）
```

```text
＃Python打印（exchange.fetch_balance（））
```

```text
// PHPvar_dump（$ exchange-> fetch_balance（））;
```

#### 平衡推断 <a id="balance-inference"></a>

一些交易所不从其API返回完整的余额信息集。那些将仅返回或仅返还资金，即未知订单上的资金。在这种情况下，ccxt会尝试从.orders缓存中获取丢失的数据，并从确定的已知信息中猜测完整的余额信息。但是，在极少数情况下，可用信息可能不足以推断出缺失的部分，因此，**用户应注意可能无法从不太复杂的交易所获得完整的余额信息**。`freetotalused`

### 订单 <a id="orders"></a>

```text
-统一API的这一部分目前正在进行中-到处可能存在一些问题和缺少的实现-贡献，拉取请求和反馈表示赞赏
```

#### 查询订单 <a id="querying-orders"></a>

大多数时候，您可以按ID或符号查询订单，尽管并非所有交易所都提供完整而灵活的端点集合来查询订单。某些交易所可能没有获取最近关闭的订单的方法，其他交易所可能缺少通过id获取订单的方法，依此类推。ccxt库将通过在可能的情况下进行变通来解决这些情况。

查询订单的方法列表包括以下内容：

* `fetchOrder (id, symbol = undefined, params = {})`
* `fetchOrders (symbol = undefined, since = undefined, limit = undefined, params = {})`
* `fetchOpenOrders (symbol = undefined, since = undefined, limit = undefined, params = {})`
* `fetchClosedOrders (symbol = undefined, since = undefined, limit = undefined, params = {})`

请注意，这些方法的名称指示该方法返回的是单个订单还是多个订单（订单的数组/列表）。该方法需要强制性的订单ID参数（字符串）。某些交易所还需要一个符号来按ID提取订单，其中订单ID可以与各种交易对相交。另外，请注意，上述所有其他方法都返回订单数组（列表）。它们中的大多数也将需要一个符号参数，但是，某些交换允许使用未指定的符号（即_所有符号_）进行查询。`fetchOrder()`

如果用户调用了交易所不可用或未在ccxt中实现的方法，则库将引发NotSupported异常。

要检查以上任何方法是否可用，请查看交换的属性：`.has`

```text
// JavaScript“使用严格”；​const ccxt = require（'ccxt'）const id ='poloniex'交换=新的ccxt [id]（）console.log（exchange.has）
```

```text
＃Python导入ccxtid ='binance'交换= getattr（ccxt，id）（）打印（exchange.has）
```

```text
// PHP$ exchange =新的\ ccxt \ liqui（）;print_r（$ exchange->有）; //或var_dump
```

该属性的典型结构通常包含与用于查询订单的订单API方法相对应的以下标志：`.has`

```text
exchange.has = {​    // ...其他标志...​    'fetchOrder'：true，//可直接从交易所获得并在ccxt中实现    'fetchOrders'：false，//无法从交易所获得或未在ccxt中实现    'fetchOpenOrders'：是，    'fetchClosedOrders'：'模拟'，//无法从交易所获得，但在ccxt中模拟​    // ...其他标志...​}
```

布尔和的含义很明显。字符串值意味着交换API中缺少特定方法，并且ccxt将在可能的情况下通过添加缓存层（缓存）来解决此问题。下一节描述了缓存的内部工作原理，必须了解它才能有效地使用ccxt进行订单管理。`truefalseemulated.orders.orders`

**查询多个订单和交易**

所有返回交易清单和订单清单的方法都接受第二个参数和第三个参数：`sincelimit`

* `fetchTrades` （上市）
* `fetchMyTrades` （私人的）
* `fetchOrders`
* `fetchOpenOrders`
* `fetchClosedOrders`

第二个参数按时间戳减少数组，第三个参数按返回项目的数量（计数）减少。`sincelimit`

如果用户未指定，则该方法将从交易所返回默认设置。默认设置是特定于交易所的，某些交易所将从在交易所中列出一对交易之日起就退回交易或最近的订单，其他交易所将退回减少的交易或订单集（例如过去24小时，过去100笔交易，前100个订单，依此类推）。如果用户希望精确控制时间范围，则用户负责指定自变量。`sincefetchTrades/fetchOrderssince`

**注意：并非所有交易所都提供了按开始时间过滤交易和订单清单的方法，因此，对and** **的支持是特定于交易所的。但是，大多数交易所确实为“分页”和“滚动”至少提供了一些替代方法，这些替代方法可以用额外的参数来覆盖。`sincelimitparams`**

**.orders快取**

某些交易所没有获取已关闭订单或所有订单的方法。它们仅提供端点，有时它们也很慷慨地提供端点。这意味着他们没有任何获取订单历史记录的方法。ccxt库将通过保留包含在特定交换类实例内发布的所有订单的缓存属性来尝试模拟用户的订单历史记录。`fetchOpenOrdersfetchOrder.orders`

每当用户创建新订单或取消现有的未结订单或执行其他可能更改订单状态的操作时，ccxt库都会在其缓存中记住整个订单信息。在一个模拟的后续调用，或方法，交流实例将发送一个请求，目前会比较牵强的未完成订单与存储在缓存以前的订单。ccxt库将检查每个缓存的订单，并尝试将其与相应的获取的未清订单匹配。当从交易所获取的未平仓订单中不再存在缓存的订单时，库会将缓存的订单标记为（已填写）。一个呼叫，，然后将从返回更新的订单缓存给用户。`fetchOrderfetchOrdersfetchClosedOrders`**`fetchOpenOrders`**`closedfetchOrderfetchOrdersfetchClosedOrders.orders`

可以在短时间内提出相同的逻辑：_如果在获取的未平仓订单中未找到缓存的订单，则该订单不再打开，因此已关闭_。这使得库能够跟踪订单状态和订单历史记录，即使在API本身没有该功能的交易所中也是如此。对于以任何方式查询订单或操纵（下达，取消或编辑）订单的所有方法，都是如此。

在大多数情况下，缓存将对用户透明地工作。大多数情况下，交易所本身具有足够的方法集。但是，由于某些交易所没有完整的API，因此缓存具有以下已知限制：`.orders.orders`

* 如果用户没有在程序运行之间保存高速缓存，并且在启动新的运行时也没有还原高速缓存，则由于明显的原因，高速缓存将丢失。因此，稍后在另一次运行中调用fetchClosedOrders时，交换实例将返回空的订单列表。如果没有正确还原缓存，则新的交换实例将无法了解有关已关闭和取消的订单的任何信息（无订单历史记录）。`.orders.orders`
* 如果API密钥对在多个交换实例之间共享（例如，当用户在多线程环境中或在同时启动的单独脚本中访问同一交换帐户时）。每个特定实例将不了解有关其他实例创建或取消的订单的任何信息。这意味着不共享订单缓存，并且通常，不应在访问私有API的多个实例之间共享同一API密钥对。否则，将导致副作用，即随机数和缓存的数据不同步。
* 如果订单是从ccxt外部（在交易所的网站上或通过其他方式）下达或取消的，则新的订单状态将不会到达缓存，并且ccxt稍后将无法正确退回该订单。
* 如果订单的取消请求绕过了ccxt，则库将无法在从后续调用中返回的未结订单列表中找到该订单。因此，库将使用状态标记缓存的订单。`fetchOpenOrders()'closed'`
* 当被仿真时，如果先前未缓存该库，或者绕过ccxt完成了订单状态的更改，则该库将无法返回特定的订单。在这种情况下，库将引发异常。`fetchOrder(id)OrderNotFound`
* 如果未处理的错误导致应用程序崩溃，并且在重新启动时未保存和还原缓存，则缓存将丢失。正确处理异常是用户的责任。在实施适当的错误处理时，必须**格外小心**，否则缓存可能会不同步。`.orders.orders`

_注意：定单缓存功能将尽快重新进行，以从私人交易历史中获得定单状态（如果有）。这是一项正在进行的工作，旨在为订单费用，成本和其他信息添加功能全面的支持。有关更多信息，请访问：_[_https_](https://github.com/ccxt/ccxt/issues/569) _:_ [_//github.com/ccxt/ccxt/issues/569_](https://github.com/ccxt/ccxt/issues/569)。

**清除缓存的订单**

对于一些长时间运行的实例，当不再需要使用的资源时，释放它们可能至关重要。因为在活跃交易中缓存会变得非常大，所以ccxt库提供了一种方法，用于从缓存中清除旧的未平仓订单，并释放用于其他目的的已用内存。清除方法接受一个名为：`.orderspurgeCachedOrders/purge_cached_orders(order['timestamp'] < before) && (order['status'] != 'open')before`

```text
// JavaScript​//将最近24小时的历史记录保留在缓存中之前= exchange.milliseconds（）-24 * 60 * 60 * 1000​//清除所有“较旧”或“之前”之前已关闭和取消的订单exchange.purgeCachedOrders（之前）
```

```text
＃Python​＃将历史的最后一小时保存在缓存中之前= exchange.milliseconds（）-1 * 60 * 60 * 1000​＃清除所有“较旧”或在“之前”之前发出的已关闭和取消的订单exchange.purge_cached_orders（之前）
```

```text
// PHP​//将最近24小时的历史记录保留在缓存中$ before = $ exchange->毫秒（）-24 * 60 * 60 * 1000;​//清除所有“较旧”或“之前”之前已关闭和取消的订单$ exchange-> purge_cached_orders（$之前）;
```

**按订单ID**

要通过其ID获取特定订单的详细信息，请使用fetchOrder / fetch\_order方法。某些交易所甚至在通过id获取特定订单时也需要符号。

fetchOrder / fetch\_order方法的签名如下：

```text
如果（exchange.has ['fetchOrder']）{    //您可以使用params参数进行自定义覆盖    让订单=等待exchange.fetchOrder（ID，符号=未定义，参数= {}）}
```

**某些交易所没有通过ID提取订单的端点，ccxt会在可能的情况下模拟该端点。**目前，它可能仍然不存在，因为这是一项正在进行的工作。

您可以在其他params参数中传递自定义的覆盖键值，以提供特定的订单类型，或根据需要提供其他设置。

以下是使用fetchOrder方法从经过身份验证的交换实例获取订单信息的示例：

```text
// JavaScript（异步函数（）{    const order =等待exchange.fetchOrder（id）    console.log（顺序）}）（）
```

```text
＃Python 2/3（同步）如果exchange.has ['fetchOrder']：    订单= exchange.fetch_order（id）    打印（顺序）​＃Python 3.5+异步（异步）导入异步将ccxt.async_support导入为ccxt如果exchange.has ['fetchOrder']：    order = asyncio.get_event_loop（）。run_until_complete（exchange.fetch_order（id））    打印（顺序）
```

```text
// PHP如果（$ exchange-> has ['fetchOrder']）{    $ order = $ exchange-> fetch_order（$ id）;    var_dump（$ order）;}
```

**所有订单**

```text
如果（exchange.has ['fetchOrders']）    exchange.fetchOrders（符号=未定义，因为=未定义，限制=未定义，参数= {}）
```

**某些交易所没有获取所有订单的端点，ccxt会在可能的情况下模拟它。**目前，它可能仍然不存在，因为这是一项正在进行的工作。

**未结订单**

```text
如果（exchange.has ['fetchOpenOrders']）    exchange.fetchOpenOrders（符号=未定义，因为=未定义，限制=未定义，参数= {}）
```

**未结订单**

不要将_已关闭的订单_与_交易_（也称为_补单）_混淆！一个订单可以关闭（执行）多个相反的交易！因此，_关闭的订单_与_交易不同_。在一般情况下，为了不具有所有，但每个特定用户交易确实有，和其他属性。但是，许多交易所也将这些属性传播到订单。`feefeecost`

**某些交易所没有端点来获取已关闭的订单，ccxt会在可能的情况下模拟它。**目前，它可能仍然不存在，因为这是一项正在进行的工作。

```text
如果（exchange.has ['fetchClosedOrders']）    exchange.fetchClosedOrders（符号=未定义，因为=未定义，限制=未定义，参数= {}）
```

#### 订单结构 <a id="order-structure"></a>

在ccxt统一API中返回订单的大多数方法通常会产生如下所示的订单结构：

```text
{    'id'：'12345-67890：09876/54321'，//字符串    'datetime'：'2017-08-17 12：42：48.000'，// ISO8601'时间戳'的日期时间，以毫秒为单位    'timestamp'：1502962946216，//以毫秒为单位下订单/打开Unix时间戳    'lastTradeTimestamp'：1502962956216，//此订单上最近交易的Unix时间戳    '状态'：'打开'，//'打开'，'关闭'，'取消'    'symbol'：'ETH / BTC'，//符号    'type'：'limit'，//'市场'，'limit'    'side'：'buy'，//'buy'，'sell'    'price'：0.06917684，//报价货币的浮动价格    'amount'：1.5，//基本货币的订购量    '填充'：1.1，//基础货币的填充量    'remaining'：0.4，//剩余金额    'cost'：0.076094524，//'已填充'*'价格'（在可用时使用填充价格）    'trades'：[...]，//订单交易/执行列表    'fee'：{//费用信息（如果有）        'currency'：'BTC'，//费用是哪种货币（通常是报价）        'cost'：0.0009，//以该货币表示的费用金额        'rate'：0.002，//费用费率（如果有）    }，    'info'：{...}，//原始的未解析订单结构}
```

* 有关信息的工作仍在进行中，取决于交换功能，费用信息可能会部分或全部丢失。`'fee'`
* 的货币可以从两个交易货币不同（例如，一个ETH / BTC以便与在USD费）。`fee`
* 所述时间戳可以具有任何值，并且可以是其中不被交换或在一个开放的顺序（即还没有被填充，也还部分地填充的顺序）的情况下支持。`lastTradeTimestampundefined/None/null`
* 的，如果有的话，指定的最后交易的时间戳，如果顺序完全或部分填充，否则是。`lastTradeTimestamplastTradeTimestampundefined/None/null`
* 订单优先于或优先于。`statuslastTradeTimestamp`
* 该命令是：`cost{ filled * price }`
* 所述订单的装置，总_报价_的顺序的体积（而是_碱_体积）。的值应尽可能接近实际的最新已知订单成本。该字段本身主要是为了方便起见，并且可以从其他字段推论得出。`costamountcostcost`

#### 下订单 <a id="placing-orders"></a>

要下订单，您将需要以下信息：

* `symbol`，市场希望字符串文字符号贸易，如，，，等...确保在存在与目标交换问题和可供交易的象征。`BTC/USDZEC/ETHDOGE/DASH`
* `side`，用于指示订单方向的字符串文字，或。下订单时，您提供报价货币并获得基础货币。例如，购买意味着您将获得美元的比特币。当您出售产品时，结果恰恰相反，您将获得比特币美元。`buysellBTC/USDBTC/USD`
* `type`，一种字符串文字类型的订单，**ccxt当前仅统一和订购**，请参阅**`marketlimit`**[https://github.com/ccxt/ccxt/wiki/Manual\#custom-order-params](https://github.com/ccxt/ccxt/wiki/Manual#custom-order-params)和[https://github.com/ccxt/ccxt/维基/手动＃等阶类型](https://github.com/ccxt/ccxt/wiki/Manual#other-order-types)
* `amount`，您想交易多少货币。这通常是指交易对符号的基础货币，尽管某些交易所要求以报价货币表示的金额，而少数交易所根据订单的面要求基础或报价金额。有关详细信息，请参见其API文档。
* `price`，您愿意为一交易手基础货币支付多少报价货币（仅限价订单）

成功调用用于下达市场或限价单的统一方法将返回以下结构：

```text
{    'id'：'string'，//订单ID    'info'：{...}，//照原样解码来自交换的原始JSON响应}
```

* **一些交易所只允许使用限价单进行交易。**有关详细信息，请参见[他们的文档](https://github.com/ccxt/ccxt/wiki/Manual#exchanges)。

**市场订单**

市场价格定单也称为_现货价格定单_，_即时定单_或简称为_市场定单_。市场订单将立即执行。交易所的匹配引擎使用订单簿堆栈顶部的一个或多个交易来关闭订单（完成订单）。

交易所将以最优惠的价格关闭您的市场订单。但是，您不能保证将以您下订单前观察到的价格执行订单。在执行订单时，交易市场的价格可能会略有变化，也称为_价格滑点_。价格可能会由于网络往返延迟，交易所的高负载，价格波动和其他因素而下滑。下市价订单时，您无需指定订单价格。

```text
// camelCaseNotationexchange.createMarketSellOrder（符号，金额[，参数]）exchange.createMarketBuyOrder（符号，金额[，参数]）​// underscore_notationexchange.create_market_sell_order（符号，金额[，参数]）exchange.create_market_buy_order（符号，金额[，参数]）​//使用一般的createOrder，输入='market'，并且side ='buy'或'sell'exchange.createOrder（符号，“市场”，“出售”，金额等）exchange.create_order（符号，“市场”，“购买”，金额等）
```

**请注意，某些交易所不接受市场定单（它们只允许限价定单）。**为了以编程方式检测相关交易所是否支持市场订单，可以使用交易所属性：`.has['createMarketOrder']`

```text
// JavaScript如果（exchange.has ['createMarketOrder']）{    ...}
```

```text
＃Python如果exchange.has ['createMarketOrder']：    ...
```

```text
// PHP如果（$ exchange-> has ['createMarketOrder']）{    ...}
```

**市场购买**

通常，在下单或下单时，用户必须仅指定要购买或出售的基础货币数量。但是，对于某些交易所，市场买入订单采用了另一种方法来计算订单价值。`market buymarket sell`

假设您正在交易BTC / USD，当前BTC的市场价格超过9000美元。对于市场买入或市场卖出，您可以指定2个BTC，这将在您的帐户中产生_正负_ 18000美元（或多或少；）），具体取决于订单的一侧。`amount`

**随着市场购买，一些交易所要求以报价货币表示的订单总成本！**其背后的逻辑很简单，而不是用基础货币的数量来买卖某些交易所，而是使用_“您想在购买中总共花费多少报价货币”来操作_。

要向这些交易所下达市场买单，您不会指定2 BTC的金额，而是应以某种方式指定订单的总成本，在此示例中为18000 USD。以这种方式处理订单的交易所具有特定于交易所的选项，该选项允许以两种方式指定订单的总成本。`market buycreateMarketBuyOrderRequiresPricemarket buy`

第一个是默认值，如果您指定以及订单的总成本，则将使用简单的乘法（）从这两个值在lib内部计算订单总成本。结果将是将用在此特定市场买单上的美元报价货币金额。`priceamountcost = amount * pricecost`

```text
//此示例过于简化，并没有显示所有的代码//需要处理错误并正确交换元数据//它仅显示下达市场买单的概念​const exchange = new ccxt.cex（{    'apiKey'：YOUR_API_KEY，    '秘密'：'YOUR_SECRET'，    'enableRateLimit'：是的，    //'options'：{    //'createMarketBuyOrderRequiresPrice'：true，//默认    //}，}）​;（async（）=> {​    //当`createMarketBuyOrderRequiresPrice`为true时，我们可以传递价格    //，以便在库中计算订单的总费用    //将金额乘以价格（金额*价格）​    const symbol ='BTC / USD'    常量= 2 // BTC    const price = 9000 //美元    //费用=金额*价格= 2 * 9000 = 18000（美元）​    //请注意，此处我们不使用createMarketBuyOrder，而是使用createOrder    // createMarketBuyOrder将忽略价格，并且在以下情况下不起作用    // exchange.options ['createMarketBuyOrderRequiresPrice'] = true    const order =等待exchange.createOrder（符号，“市场”，“购买”，金额，价格）​    console.log（顺序）}）
```

在用户想要自己计算和指定订单的最终总成本的情况下，第二种选择很有用。可以通过设置选项将其关闭来完成：`createMarketBuyOrderRequiresPricefalse`

```text
const exchange = new ccxt.cex（{    'apiKey'：YOUR_API_KEY，    '秘密'：'YOUR_SECRET'，    'enableRateLimit'：是的，    '选项'：{        'createMarketBuyOrderRequiresPrice'：false，//关闭    }，}）​//或稍后将其关闭，在交换实例化之后，您可以exchange.options ['createMarketBuyOrderRequiresPrice'] = false​;（async（）=> {​    //当`createMarketBuyOrderRequiresPrice`为true时，我们可以传递价格    //，以便在库中计算订单的总费用    //将金额乘以价格（金额*价格）​    const symbol ='BTC / USD'    常量= 2 // BTC    const price = 9000 //美元    成本=金额*价格//←而不是金额成本↓    const order =等待exchange.createMarketBuyOrder（符号，成本）    console.log（顺序）}）
```

关于它的更多信息：

* [https://github.com/ccxt/ccxt/issues/564\#issuecomment-347458566](https://github.com/ccxt/ccxt/issues/564#issuecomment-347458566)
* [https://github.com/ccxt/ccxt/issues/4914\#issuecomment-478199357](https://github.com/ccxt/ccxt/issues/4914#issuecomment-478199357)
* [https://github.com/ccxt/ccxt/issues/4799\#issuecomment-470966769](https://github.com/ccxt/ccxt/issues/4799#issuecomment-470966769)
* [https://github.com/ccxt/ccxt/issues/5197\#issuecomment-496270785](https://github.com/ccxt/ccxt/issues/5197#issuecomment-496270785)

**用限价订单模拟市场订单**

也可以使用订单模拟订单。`marketlimit`

**警告由于高波动性，此方法可能会有风险，请您自担风险，仅在非常了解自己在做什么时才使用它！**

大多数情况下，可以用非常低的价格模拟a- 交易所会自动将其设为市场价格的接受者订单（当前价格与订单书中提供的价格最相符）。当交易所检测到您以非常低的价格出售时，它将自动为您提供可从订单簿获得的最佳买方价格。这实际上与下达市场卖单相同。因此，市场订单可以与限价订单（缺少订单）进行模拟。`market selllimit sell`

反之亦然– 可以用非常高的价格模拟a 。大多数交易所会再次以最优惠的价格（即市场价格）关闭您的订单。`market buylimit buy`

但是，您永远不应完全依赖它，请**始终先进行少量测试！**您可以先在其Web界面中尝试该操作以验证逻辑。您可以以指定的限制价格卖出最小金额（为了以防万一，可以承受的可亏损金额），然后在交易历史记录中查看实际的填充价格。

**限价单**

限价单也称为_限价单_。一些交易所只接受限价单。限价订单要求价格（每单位价格）与订单一起提交。当且仅当市场价格达到所需水平时，交易所才会关闭限价单。

```text
// camelCaseStyleexchange.createLimitBuyOrder（符号，金额，价格[，参数]）exchange.createLimitSellOrder（符号，金额，价格[，参数]）​// underscore_styleexchange.create_limit_buy_order（符号，金额，价格[，参数]）exchange.create_limit_sell_order（符号，金额，价格[，参数]）
```

**自定义订单参数**

一些交易所允许您为订单指定可选参数。您可以传递可选参数，并使用统一API调用的参数使用关联数组覆盖查询。当然，所有自定义参数都是特定于交换的，并且不能互换，不要期望一个交换的那些自定义参数可以与另一个交换一起工作。`params`

```text
// JavaScript//使用自定义订单类型bitfinex.createLimitSellOrder（'BTC / USD'，1，10，{'type'：'trailing-stop'}）
```

```text
＃Python＃添加自定义订单标志kraken.create_market_buy_order（'BTC / USD'，1，{'trading_agreement'：'agree'}）
```

```text
// PHP//将自定义用户ID添加到您的订单$ hitbtc-> create_order（'BTC / USD'，'limit'，'buy'，1，3000，array（'clientOrderId'=>'123'））;
```

**其他订单类型**

该可以是或者，如果你想要一个类型，使用PARAMS覆盖，如下所述：`typelimitmarketstopLimit`[https://github.com/ccxt/ccxt/wiki/Manual\#overriding-unified-api-params](https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-api-params)。

以下是覆盖订单类型的通用示例，但是，您必须阅读所涉及交易所的文档才能指定正确的参数和值。订单类型不是或当前未统一，因此对于其他订单类型，必须覆盖统一的参数，如下所示。`limitmarket`

```text
const symbol ='ETH / BTC'const type ='limit'//或'market'，其他类型尚未统一const side ='卖出'const amount = 123.45 //您的金额const price = 54.321 //您的价格//覆盖const params = {    'stopPrice'：123.45，//您的止损价    'type'：'stopLimit'，}const order =等待exchange.createOrder（符号，类型，边，金额，价格，参数）
```

```text
符号='ETH / BTC'type ='limit'＃或'market'，其他类型尚未统一侧='卖出'金额= 123.45＃您的金额价格= 54.321＃您的价格＃覆盖参数= {    'stopPrice'：123.45，＃您的止损价    'type'：'stopLimit'，}order = exchange.create_order（符号，类型，边，金额，价格，参数）
```

```text
$ symbol ='ETH / BTC';$ type ='限制'; //或“市场”，其他类型尚未统一$ side ='卖出';$ amount = 123.45; //您的金额$ price = 54.321; // 你的价格//覆盖$ params = {    'stopPrice'：123.45，//您的止损价    'type'：'stopLimit'，}$ order = $ exchange-> create_order（$ symbol，$ type，$ side，$ amount，$ price，$ params）；
```

#### 取消订单 <a id="canceling-orders"></a>

要取消现有订单，请将订单ID传递给方法。请注意，某些交易所甚至需要第二个符号参数才能通过ID取消已知订单。用法显示在以下示例中：`cancelOrder (id, symbol, params) / cancel_order (id, symbol, params)`

```text
// JavaScriptexchange.cancelOrder（'1234567890'）//在此处替换为您的订单ID（字符串）
```

```text
＃Pythonexchange.cancel_order（'1234567890'）＃在此处替换为您的订单ID（字符串）
```

```text
// PHP$ exchange-> cancel_order（'1234567890'）; //在此处替换为您的订单ID（字符串）
```

**取消订单的例外**

在通常用在只开放订单。但是，您的订单可能会在取消请求进入之前被执行（执行和关闭），因此取消请求可能会触及已经关闭的订单。`cancelOrder()`

取消请求也可能会显示一个指示，说明是否成功取消了订单以及是否需要重试。连续调用可能还会触发已取消的订单。`NetworkErrorcancelOrder()`

因此，在以下情况下可能会引发异常：`cancelOrder()OrderNotFound`

* 取消已经关闭的订单
* 取消已经取消的订单

### 个人交易 <a id="personal-trades"></a>

```text
-统一API的这一部分目前正在进行中-到处可能存在一些问题和缺少的实现-贡献，拉取请求和反馈表示赞赏
```

#### 订单与交易如何相关 <a id="how-orders-are-related-to-trades"></a>

通常也称为交易。每笔交易都是订单执行的结果。请注意，订单和交易具有一对多的关系：执行一个订单可能会导致几笔交易。但是，当一个订单与另一个相反的订单匹配时，两个匹配的订单对将产生一个交易。因此，当一个订单与多个相反的订单匹配时，这将产生多个交易，每对匹配的订单一对交易。`a fill`

简而言之，一个订单可以包含_一个或多个_交易。或者，换句话说，一个订单可以_填充_一个或多个交易。

例如，一个订单簿可以具有以下订单（无论是交易符号还是配对）：

```text
| 价格| 量---- | ----------------  一个| 1.200 | 200  s | 1.100 | 300  k | 0.900 | 100---- | ----------------  b | 0.800 | 100  我 0.700 | 200  d | 0.500 | 100
```

上面所有具体数字都不是真实的，这仅是为了说明订单和交易的总体关联方式。

卖方决定在卖价侧以0.700的价格和150的价格下达限价订单。

```text
| 价格| 量---- | ----------------↓  一个| 1.200 | 200↓  s | 1.100 | 300↓  k | 0.900 | 100↓---- | ----------------↓  b | 0.800 | 100↓以0.700的价格卖出150  我 0.700 | 200 --------------------  d | 0.500 | 100
```

由于收到的卖出（卖出）定单的价格和金额涵盖多个买入定单（orders 和），因此以下一系列事件通常在交换引擎中很快发生，但不是立即发生：`bi`

1. 订单与进货相匹配，因为它们的价格相交。他们的交易量_相互“歼灭”_，因此，投标人以0.800的价格获得100。卖方（质询者）将以0.800的价格将其卖出订单部分填充为100个投标量。请注意，对于订单的已履行部分，卖方获得的价格要比最初要求的要好。他要求至少为0.7，但得到的却是0.8，这对卖方来说甚至更好。大多数传统交易所都以最优惠的价格执行订单。`b`
2. 针对订单生成了与传入的销售订单的交易。该交易_“填充”_了整个订单和大部分卖出订单。每对匹配的订单都会产生一笔交易，无论金额是全部还是部分都被填补。在此示例中，卖方金额（100）完全填写订单（关闭订单），还部分填写销售订单（在订单簿中将其打开）。`bbbb`
3. 现在，订单的状态为，并且填充量为100。其中包含一笔针对卖单的交易。卖单的状态为，成交量为100。它包含一份针对订单的交易。因此，到目前为止，每个订单只有一个填充交易。`bclosedopenb`
4. 传入的卖单有一个已完成的数量100，尚未从其最初的总数量150填补剩余的50。

所述手持订单的中间状态现在是（顺序是和不处于手持订单了）：`bclosed`

```text
| 价格| 量---- | ----------------↓  一个| 1.200 | 200↓  s | 1.100 | 300↓  k | 0.900 | 100↓---- | ----------------↓将剩余的50卖给0.700  我 0.700 | 200 -----------------------------  d | 0.500 | 100
```

1. 订单与进货的剩余部分匹配，因为它们的价格相交。数量为200 的购买订单将完全消除剩余的50的卖出订单。该订单将部分填充50，但是剩余数量（即剩余的150）将保留在订单簿中。但是，第二次比赛完全完成了销售订单。`iii`
2. 针对订单生成了与传入的销售订单的交易。那笔交易部分地填补了订单。并完成卖单的填写。同样，这只是一对匹配订单的交易。`ii`
3. 现在，订单的状态为，填充量为50，剩余量为150。它包含一个针对销售订单的填充交易。卖单现在处于状态，并且已完全填满其初始总金额150。但是，它包含两项交易，第一项针对订单，第二项针对订单。因此，每个订单可以具有一个或多个填充交易，具体取决于交换引擎如何匹配其交易量。`iopenclosedbi`

完成上述顺序后，更新后的订单将如下所示。

```text
| 价格| 量---- | ----------------  一个| 1.200 | 200  s | 1.100 | 300  k | 0.900 | 100---- | ----------------  我 0.700 | 150  d | 0.500 | 100
```

请注意，订单已消失，销售订单也不存在。所有已关闭和已满的订单将从订单簿中消失。仍然部分地执行的订单仍然有剩余的数量和状态。`biopen`

#### 个人交易 <a id="personal-trades-1"></a>

大多数统一方法将返回单个对象或对象（交易）的纯数组（列表）。但是，很少有交易所（如果有的话）会一次返回所有交易。大多数情况下，它们的API 输出到一定数量的最新对象。**从时间开始到现在的一刻之间，您无法得到所有对象**。实际上，很少有交易所会容忍或允许这样做。`limit`

与用于获取历史数据的所有其他统一方法一样，该方法接受基于日期的分页的参数。就像整个CCXT库中的所有其他统一方法一样，for 的参数必须**是以毫秒为单位**的**整数时间戳**。`fetchMyTradessincesincefetchMyTrades`

为了获取历史交易，用户将需要遍历对象的部分或“页面”中的数据。分页通常意味着_“_循环_获取数据的一部分”_。

在大多数情况下，**要求**用户**至少使用某种类型的分页**以便始终如一地获得预期结果。

```text
// JavaScript// fetchMyTrades（符号=未定义，因为=未定义，限制=未定义，参数= {}）​如果（exchange.has ['fetchMyTrades']）{    const trades =等待exchange.fetchMyTrades（符号，因为，限制，参数）}
```

```text
＃Python＃fetch_my_trades（符号=无，因为=无，限制=无，参数= {}）​如果exchange.has ['fetchMyTrades']：    exchange.fetch_my_trades（符号=无，因为=无，限制=无，参数= {}）
```

```text
// PHP// fetch_my_trades（$ symbol = null，$ since = null，$ limit = null，$ params = array（））​如果（$ exchange-> has ['fetchMyTrades']）{    $ trades = $ exchange-> fetch_my_trades（$ symbol，$ since，$ limit，$ params）;}
```

返回交易的有序数组（最近交易）。`[]`

**贸易结构**

```text
{    'info'：{...}，//原始解码的JSON原样    'id'：'12345-67890：09876/54321'，//字符串交易ID    'timestamp'：1502962946216，// Unix时间戳以毫秒为单位    'datetime'：'2017-08-17 12：42：48.000'，// ISO8601日期时间（以毫秒为单位）    'symbol'：'ETH / BTC'，//符号    'order'：'12345-67890：09876/54321'，//字符串顺序ID或未定义/无/空    'type'：'limit'，//订单类型，'market'，'limit'或未定义/无/空    'side'：'buy'，//交易方向，'buy'或'sell'    'takerOrMaker'：'taker'，//字符串，'taker'或'maker'    'price'：0.06917684，//报价货币的浮动价格    'amount'：1.5，//基础货币数量    'cost'：0.10376526，//总费用（包括费用），`price * amount`    'fee'：{//由交易所提供或由ccxt计算        'cost'：0.0015，//浮动        'currency'：'ETH'，//通常是购买的基本货币，卖出的报价货币        'rate'：0.002，//费用费率（如果有）    }，}
```

* 有关信息的工作仍在进行中，取决于交换功能，费用信息可能会部分或全部丢失。`'fee'`
* 的货币可以从两个交易货币不同（例如，一个ETH / BTC以便与在USD费）。`fee`
* 该交易手段。它是总_报价_的贸易量（然而是_碱_体积）。成本字段本身主要是为了方便起见，可以从其他字段中推导出。`costamount * priceamount`

#### 订单编号交易 <a id="trades-by-order-id"></a>

`UNDER CONSTRUCTION`

### 为您的帐户注资 <a id="funding-your-account"></a>

```text
-统一API的这一部分目前正在进行中-到处可能存在一些问题和缺少的实现-贡献，拉取请求和反馈表示赞赏
```

#### 存款 <a id="deposit"></a>

为了将资金存入交易所，您必须从交易所获取要存入其中的货币的地址。大多数交易所都会为用户创建和管理这些地址。一些交易所还将允许用户创建新的存款地址。一些交易所要求为每个新存款创建一个新的存款地址。

存款地址可以是先前在交易所创建的已经存在的地址，也可以根据要求创建。为了查看支持两种方法中的哪一种，请检查和属性。两种方法都返回一个地址结构`exchange.has['fetchDepositAddress']exchange.has['createDepositAddress']`

```text
fetchDepositAddress（代码，参数= {}）createDepositAddress（代码，参数= {}）
```

* `code` 是统一货币代码（大写字符串）
* `params` 包含可选的额外替代

某些交易所还可能提供一种一次性获取多个或所有一次性存款地址的方法：

```text
fetchDepositAddresses（代码=未定义，参数= {}）
```

根据交易所的不同，第一个参数中可能需要也可能不需要统一货币列表。该方法返回一个地址结构数组。`codesfetchDepositAddresses`

**地址结构**

从返回的地址结构，而像这样：`fetchDepositAddressfetchDepositAddressescreateDepositAddress`

```text
{    'currency'：货币，//货币代码    'address'：地址，//地址，以要求的货币表示    'tag'：标签，//特定货币（XRP，XMR等）的标签/便笺/ paymentId    'info'：响应，//从交易所返回的未解析的原始数据}
```

对于某些货币，例如AEON，BTS，GXS，NXT，SBD，STEEM，STR，XEM，XLM，XMR，XRP，交易所通常需要附加参数。其他货币将设置为。标签是附加在提款交易中的备忘录，消息或付款ID。对于这些货币，该标记是必需的，并且它标识收件人用户帐户。`tagtagundefined / None / null`

指定和时要小心。的是**不是一个武断的用户定义的字符串**的选择！您无法在中发送用户消息和评论。该字段的目的是正确处理您的钱包，因此必须正确。您只应使用与之打交道的交易所收到的款项，否则您的交易可能永远不会到达目的地。`tagaddresstagtagtagtag`

#### 退出 <a id="withdraw"></a>

```text
// JavaScriptexchange.withdraw（代码，金额，地址，标签=未定义，参数= {}）
```

```text
＃Pythonexchange.withdraw（代码，金额，地址，标签=无，参数= {}）
```

```text
// PHP$ exchange-> withdraw（$ code，$ amount，$ address，$ tag = null，$ params = array（））
```

该是货币代码（通常是三个或更多的大写字母，但可以在不同的情况）。`code`

withdraw方法返回一个包含提款id的字典，通常是链上交易本身的txid，或者是在交易所中注册的内部_提款请求id_。返回的值如下所示：

```text
{    'info'{...}，//交易所未解析的回复，原样    'id'：'12345567890'，//字符串提取ID（如果有）}
```

某些交易所要求通过2FA（两要素验证）手动批准每次提款。为了批准您的提款，您通常必须在电子邮件收件箱中单击其秘密链接，或者在其网站上输入Google Authenticator代码或Authy代码，以验证是否有意提出提款交易。

在某些情况下，您还可以使用提款ID稍后检查提款状态（是否成功）并提交2FA确认码（交易所支持）。有关详细信息，请参见[他们的文档](https://github.com/ccxt/ccxt/wiki/Manual#exchanges)。

#### 交易次数 <a id="transactions"></a>

**交易结构**

```text
{    'info'：{...}，//交换的JSON响应原样    'id'：'123456'，//交易专用交易ID，字符串    'txid'：'0x68bfb29821c50ca35ef3762f887fd3211e4405aba1a94e448a4f218b850358f0'，    '时间戳'：1534081184515，//时间戳以毫秒为单位    'datetime'：'2018-08-12T13：39：44.515Z'，//时间戳的ISO8601字符串    'addressFrom'：'0x38b1F8644ED1Dbd5DcAedb3610301Bf5fa640D6f'，//发送者    '地址'：'0x02b0a9b7b4cDe774af0f8e47cb4f1c2ccdEa0806'，//“从”或“到”    'addressTo'：'0x304C68D441EF7EB0E2c056E836E8293BD28F8129'，//接收者    与发件人关联的'tagFrom'，'0xabcdef'，//“ tag”或“ memo”或“ payment_id”    'tag'：'0xabcdef'//与该地址相关联的“ tag”或“ memo”或“ payment_id”    'tagTo'：'0xhijgklmn'，//与接收者相关联的“ tag”或“ memo”或“ payment_id”    'type'：'deposit'，//或'withdrawal'，字符串    'amount'：1.2345，//浮动（不包括费用）    'currency'：'ETH'，//通用统一货币代码，字符串    '状态'：'待定'，//'确定'，'失败'，'取消'，字符串    'updated'：undefined，//最近状态变化的UTC时间戳（以毫秒为单位）    '评论'：'用户定义的评论或消息（如果有），    'fee'：{//整个费用结构可能不确定        'currency'：'ETH'，//统一费用货币代码        'cost'：0.1234，//浮动        'rate'：未定义，//大约，fee ['cost'] /金额，浮动    }，}
```

**交易结构说明**

* `addressFrom`或可能是（如果有关交易所未指定交易的所有方面）`addressToundefined/None/null`
* 该字段的语义是特定于交换的。在某些情况下，它可以包含发送者的地址，在其他情况下，它可以包含接收者的地址。实际值取决于交换。`address`
* 该油田位于该资金运作的状态最近改变的毫秒UTC时间戳，无论是或。如果要跟踪静态快照之外的时间更改，则很有必要。例如，如果有问题的交易所报告并进行了交易，则该字段将采用的值，即状态的最新更改的时间戳记。`updatedwithdrawaldepositcreated_atconfirmed_atupdatedMath.max (created_at, confirmed_at)`
* 在某些特定于交易所的情况下，该字段可能会出现。`updatedundefined/None/null`
* 该子可能会丢失，如果不从交换来的回复中提供。`fee`
* 该字段可以是，否则它将包含用户在创建交易时定义的消息或注释。`commentundefined/None/null`
* 处理和时要小心。的是**不是一个武断的用户定义的字符串**的选择！您无法在中发送用户消息和评论。该字段的目的是正确处理您的钱包，因此必须正确。您只应使用与之打交道的交易所收到的款项，否则您的交易可能永远不会到达目的地。`tagaddresstagtagtagtag`

**存款**

```text
// JavaScript// fetchDeposits（代码=未定义，因为=未定义，限制=未定义，参数= {}）​如果（exchange.has ['fetchDeposits']）{    const deposits = await exchange.fetchDeposits（代码，因为限制，参数）}其他{    引发新错误（exchange.id +'没有fetchDeposits方法'）}
```

```text
＃Python＃fetch_deposits（代码=无，因为=无，限制=无，参数= {}）​如果exchange.has ['fetchDeposits']：    deposits = exchange.fetch_deposits（代码，因为限制，参数）其他：    引发异常（exchange.id +'没有fetch_deposits方法'）
```

```text
// PHP// fetch_deposits（$ code = null，$ since = null，$ limit = null，$ params = {}）​如果（$ exchange-> has ['fetchDeposits']）{    $ deposits = $ exchange-> fetch_deposits（$ code，$ since，$ limit，$ params）;}其他{    抛出新异常（$ exchange-> id。'没有fetch_deposits方法'）；}
```

**提款**

```text
// JavaScript// fetchWithdrawals（代码=未定义，因为=未定义，限制=未定义，参数= {}）​如果（exchange.has ['fetchWithdrawals']）{    const取款=等待exchange.fetchWithdrawals（代码，开始，限制，参数）}其他{    引发新错误（exchange.id +'没有fetchWithdrawals方法'）}
```

```text
＃Python＃fetch_withdrawals（代码=无，因为=无，限制=无，参数= {}）​如果exchange.has ['fetchWithdrawals']：    取款= exchange.fetch_withdrawals（代码，因为，限制，参数）其他：    引发异常（exchange.id +'没有fetch_withdrawals方法'）
```

```text
// PHP// fetch_withdrawals（$ code = null，$ since = null，$ limit = null，$ params = {}）​如果（$ exchange-> has ['fetchWithdrawals']）{    $ withdrawals = $ exchange-> fetch_withdrawals（$ code，$ since，$ limit，$ params）;}其他{    抛出新异常（$ exchange-> id。'没有fetch_withdrawals方法'）；}
```

**所有交易**

```text
// JavaScript// fetchTransactions（代码=未定义，因为=未定义，限制=未定义，参数= {}）​如果（exchange.has ['fetchTransactions']）{    const Transactions =等待exchange.fetchTransactions（代码，因为，限制，参数）}其他{    引发新错误（exchange.id +'没有fetchTransactions方法'）}
```

```text
＃Python＃fetch_transactions（代码=无，因为=无，限制=无，参数= {}）​如果exchange.has ['fetchTransactions']：    交易= exchange.fetch_transactions（代码，因为，限制，参数）其他：    引发异常（exchange.id +'没有fetch_transactions方法'）
```

```text
// PHP// fetch_transactions（$ code = null，$ since = null，$ limit = null，$ params = {}）​如果（$ exchange-> has ['fetchTransactions']）{    $ transactions = $ exchange-> fetch_transactions（$ code，$ since，$ limit，$ params）;}其他{    抛出新异常（$ exchange-> id。'没有fetch_transactions方法'）；}
```

### 费用 <a id="fees"></a>

**Unified CCXT API的这一部分正在开发中。**

费用通常分为两类：

* 交易费。交易费是应支付给交易所的金额，通常为交易量（已填充）的百分比。
* 资金费用。存款和取款时应支付给交易所的金额以及相关的加密交易费用（tx费用）。

因为费用结构可能取决于用户交易的实际货币量，所以费用可能是特定于帐户的。处理特定帐户费用的方法：

```text
fetchFees（参数= {}）fetchTradingFees（参数= {}）fetchFundingFees（参数= {}）
```

费用方法将返回一个统一的费用结构，通常在订单和交易中也存在。费用结构是一种通用格式，用于表示整个图书馆的费用信息。费用结构通常按市场或货币索引。

由于这仍在进行中，因此本次或此次交换可能缺少本节中介绍的部分或全部方法和信息。

**不要使用该属性，因为它最经常包含预定义/硬编码的信息，而现在已弃用。实际费用只能从市场和货币中获取。`.fees`**

#### 费用结构 <a id="fee-structure"></a>

```text
{    '类型'：takerOrMaker，    'currency'：'BTC'，//统一费用货币代码    '费率'：百分比，//费率，0.05％= 0.0005，1％= 0.01，...    'cost'：feePaid，//费用成本（金额*费用费率）}
```

#### 交换状态 <a id="exchange-status"></a>

交换状态描述了有关交换API可用性的最新已知信息。此信息可以硬编码到交换类中，也可以直接从交换API中实时获取。该方法可用于获取此信息。返回的状态是以下之一：`fetchStatus(params = {})fetchStatus`

* 硬编码到交换类中，例如，如果API被破坏或关闭。
* 使用交换ping或端点进行了更新，以查看其是否还存在`fetchTime`
* 使用专用的Exchange API状态端点进行了更新。

```text
fetchStatus（params = {}）
```

**交易所状态结构**

该方法将返回如下所示的状态结构：`fetchStatus()`

```text
{    '状态'：'确定'，//'确定'，'关机'，'错误'，'维护'    'updated'：未定义，//整数，如果通过API更新，则最后更新的时间戳（以毫秒为单位）    'eta'：undefined，//预计维护或停机将结束    'url'：未定义，//指向GitHub问题或该主题的交流文章的链接}
```

该字段中的可能值为：`status`

* `'ok'` 表示交换API完全可操作
* `'shutdown`'表示交易所已关闭，并且该字段应包含关闭的日期时间`updated`
* `'error'` 意味着交换API被破坏，或者CCXT中交换的实现被破坏
* `'maintenance'`表示需要定期维护，并且该字段应包含预计交易所可以再次运行的日期时间`eta`

#### 交易费用 <a id="trading-fees"></a>

交易费是市场的财产。通常，交易费用通过看涨期权被载入市场。但是，有时交易所会收取来自不同端点的费用。`fetchMarkets`

该方法可用于预先计算将要支付的交易费用。**警告！此方法是实验性的，不稳定，在某些情况下可能会产生错误的结果**。您只能谨慎使用它。实际费用可能与从中返回的值不同，这只是用于预先计算。不要依赖预先计算的值，因为市场情况经常变化。事先很难知道您的订单是做市商还是做市商。`calculateFeecalculateFee`

```text
computeFee（符号，类型，边，金额，价格，takerOrMaker ='taker'，params = {}）
```

对于具有指定参数的订单，该方法将返回带有预先计算的费用的统一费用结构。`calculateFee`

获取交易费率应通过酒店完成，例如：`.markets`

```text
exchange.markets ['ETH / BTC'] ['taker'] // ETH / BTC的收取者费率exchange.markets ['BTC / USD'] ['maker'] // BTC / USD的制造商费率
```

当您向交易所提供流动性时，即在您做_市价_单并由其他人执行时，支付制造商费用。制作者费用通常低于接受者费用。同样，当您从交易所_收取_流动性并执行其他人的订单时，_将_收取_接管_人费用。

#### 资助费用 <a id="funding-fees"></a>

资金费用是货币的属性（帐户余额）。

获取资金费率应通过酒店完成。这方面尚不统一，可能会发生变化。`.currencies`

```text
exchange.currencies ['ETH'] ['fee'] // ETH的收款/取款费率exchange.currencies ['BTC'] ['fee'] // BTC的收款/取款费率
```

### 分类帐 <a id="ledger"></a>

`UNDER CONSTRUCTION`

一些交易所提供了其他端点来获取多合一分类帐历史记录。分类账只是变化的历史记录，用户执行的操作或以任何方式改变用户余额的操作，即所有资金从/到用户所有帐户的移动历史。其中包括存款和取款（资金），交易或订单产生的进出款额，交易费用，账户之间的转账，回扣，现金返还以及其他需要核算的事件。

```text
异步fetchLedger（代码=未定义，因为=未定义，限制=未定义，参数= {}）
```

一些交易所不允许一次获取所有资产的所有分类帐条目，那些交易所要求将参数提供给方法。`codefetchLedger`

#### 分类帐分录结构 <a id="ledger-entry-structure"></a>

```text
{    'id'：'hqfl-f125f9l2c9'，//分类帐条目的字符串ID，例如订单ID    'direction'：'out'，//或'in'    'account'：'06d4ab58-dfcd-468a'，//帐户的字符串ID（如果有）    'referenceId'：'bf7a-d4441fb3fd31'，//交易，交易等的字符串ID ...    'referenceAccount'：'3146-4286-bb71'，//对方帐户的字符串ID（如果有）    'type'：'trade'，//字符串，引用类型，请参见下文    'currency'：'BTC'，//字符串，统一货币代码，'ETH'，'USDT'...    'amount'：123.45，//绝对数字，浮动（不包括费用）    'timestamp'：1544582941735，//自UTC的纪元时间以来的毫秒数    'datetime'：“ 2018-12-12T02：49：01.735Z”，//时间戳字符串，ISO8601    '之前'：0，//之前的余额余额    '之后'：0，//之后的余额余额货币    '状态'：'确定'，//'确定，'待定'，'取消'    'fee'：{//对象或未定义        'cost'：54.321，//金额之上的绝对数字        'currency'：'ETH'，//字符串，统一货币代码，'ETH'，'USDT'...    }，    'info'：{...}，//来自交易所的原始分类帐条目}
```

#### 关于分类帐分录结构的注释 <a id="notes-on-ledger-entry-structure"></a>

分类帐条目的类型是与其关联的操作的类型。如果金额来自卖单，则将其与相应的交易类型分类账条目关联，并且referenceId将包含关联的交易ID（如果所涉及的交易所提供了该ID）。如果金额是由于提款而产生，则与相应的交易相关联。

* `trade`
* `transaction`
* `fee`
* `rebate`
* `cashback`
* `referral`
* `transfer`
* `whatever`
* …

该字段保存通过将新项目添加到分类账而注册的相应事件的ID。`referenceId`

该字段在那里支持交换，包括分类账中的未决和已取消的更改。分类账自然地代表已经发生的实际更改，因此，在大多数情况下，状态为显示。`status'ok'`

分类账输入类型可以与常规交易或资金交易（存款或提款）或同一用户的两个帐户之间的内部关联。如果分类帐条目与内部转帐相关联，则该字段将包含正在使用相关分类帐条目更改的帐户的ID。该字段将包含资金转移到/来自的相对帐户的ID，具体取决于（或）。`transferaccountreferenceAccountdirection'in''out'`

### 覆盖Nonce <a id="overriding-the-nonce"></a>

**默认的随机数是32位Unix时间戳，以秒为单位。如果您要进行私人请求的频率大于每秒一次，则应以毫秒为单位重写它！如果您达到了汇率限制，大多数交易所都会限制您的请求，请仔细阅读**[**API文档以进行交流**](https://github.com/ccxt/ccxt/wiki/Exchanges)**！**

如果您需要重置随机数，则可以轻松创建另一对密钥以用于私有API。通常，在配置中创建新密钥并设置新的未使用的密钥对就足够了。

在某些情况下，由于缺少权限或其他原因，您无法创建新密钥。如果发生这种情况，您仍然可以覆盖随机数。为了方便起见，基本市场类别具有以下方法：

* `seconds ()`：以秒为单位返回Unix时间戳。
* `milliseconds ()`：相同（以毫秒为单位）（ms = 1000 \* s，千分之一秒）。
* `microseconds ()`：相同（以微秒为单位）（μs= 1000 \* ms，百万分之一秒）。

在他们的API文档中，有些交流会将毫秒与微秒相混淆，我们所有人都为此原谅。您可以使用上面列出的方法来覆盖现时值。如果需要在多个实例中使用相同的密钥对，请同时使用闭包或通用函数，以避免随机数冲突。在Javascript中，您可以通过为交换构造函数提供参数或在交换对象上显式设置它来覆盖现时值：`nonce`

```text
// JavaScript​// A：在构造函数参数中重新定义的自定义随机数让随机数= 1让kraken1 = new ccxt.kraken（{nonce：（）=> nonce ++}）​// B：现时显式重新定义让kraken2 = new ccxt.kraken（）kraken2.nonce = function（）{return nonce ++} //使用与kraken1相同的随机数​// C：毫秒级随机数让kraken3 = new ccxt.kraken（{    随机数：函数（）{返回this.milliseconds（）}，}）​// D：更新的ES语法让kraken4 = new ccxt.kraken（{    随机数（）{返回this.milliseconds（）}，}）
```

在Python和PHP中，您可以通过继承和覆盖特定交换类的nonce函数来实现此目的：

```text
＃Python​＃-最短coinbasepro = ccxt.coinbasepro（{'nonce'：ccxt.Exchange.milliseconds}）​＃B：自定义随机数类MyKraken（ccxt.kraken）：    n = 1    def nonce（个体）：        返回self.n + = 1​＃C：毫秒随机数类MyBitfinex（ccxt.bitfinex）：    def nonce（个体）：        返回self.milliseconds（）​＃D：毫秒级随机数内联hitbtc = ccxt.hitbtc（{    'nonce'：lambda：int（time.time（）* 1000）}）​＃E：随机数毫秒acx = ccxt.acx（{'nonce'：lambda：ccxt.Exchange.milliseconds（）}）
```

```text
// PHP​// A：自定义随机数值MyOKCoinUSD类扩展\ ccxt \ okcoinusd {    公共功能__construct（$ options = array（））{        parent :: __ construct（array_merge（array（'i'=> 1），$ options））;    }    公共功能随机数（）{        返回$ this-> i ++;    }}​// B：毫秒级随机数MyZaif类扩展\ ccxt \ zaif {    公共功能__construct（$ options = array（））{        parent :: __ construct（array_merge（array（'i'=> 1），$ options））;    }    公共功能随机数（）{        返回$ this-> milliseconds（）;    }}
```

## 错误处理 <a id="error-handling"></a>

CCXT的错误处理是通过所有语言固有的异常机制完成的。

要处理错误，您应该在对统一方法的调用周围添加一个块，并像通常使用语言那样捕获异常：`try`

```text
// JavaScript​//尝试调用统一方法尝试{    const response =等待exchange.fetchTicker（'ETH / BTC'）    console.log（响应）}抓住（e）{    //如果抛出异常，则被“捕获”，可以在这里处理    //处理反应取决于异常的类型    //以及应用程序的目的或业务逻辑    if（e instanceof ccxt.NetworkError）{        console.log（exchange.id，“ fetchTicker由于网络错误而失败：”，e.message）        //重试        // ...    } else if（e instanceof ccxt.ExchangeError）{        console.log（exchange.id，“ fetchTicker失败，由于交换错误：”，e.message）        //重试        // ...    }其他{        console.log（exchange.id，“ fetchTicker失败：”，e.message）        //重试        // ...    }}
```

```text
＃Python​＃尝试调用统一方法尝试：    响应=等待exchange.fetch_order_book（'ETH / BTC'）    打印（响应）ccxt.NetworkError除外，例如e：    print（exchange.id，'fetch_order_book由于网络错误而失败：'，str（e））    ＃重试或其他    ＃...ccxt.ExchangeError除外，例如e：    打印（exchange.id，'fetch_order_book由于交换错误而失败：'，str（e））    ＃重试或其他    ＃...例外，例如e：    打印（exchange.id，'fetch_order_book失败并显示：'，str（e））    ＃重试或其他    ＃...
```

```text
// PHP​//尝试调用统一方法尝试{    $ response = $ exchange-> fetch_trades（'ETH / BTC'）;    print_r（$ response）;} catch（\ ccxt \ NetworkError $ e）{    echo $ exchange-> id。“由于网络错误，fetch_trades失败：”。$ e-> getMessage（）。“ \ n”;    //重试    // ...} catch（\ ccxt \ ExchangeError $ e）{    echo $ exchange-> id。'fetch_trades由于交换错误而失败：'。$ e-> getMessage（）。“ \ n”;    //重试    // ...} catch（Exception $ e）{    echo $ exchange-> id。'fetch_trades失败，原因是：'。$ e-> getMessage（）。“ \ n”;    //重试    // ...}
```

### 异常层次 <a id="exception-hierarchy"></a>

所有异常均源自基本BaseError异常，而该异常又在ccxt库中定义，如下所示：

```text
// JavaScriptClassError类扩展Error {    构造函数（）{        超级（）        //一种使`instanceof BaseError`在ES5中工作的解决方法        this.constructor = BaseError        this .__ proto__ = BaseError.prototype    }}
```

```text
＃Python类BaseError（Exception）：    通过
```

```text
// PHPBaseError类扩展\ Exception {}
```

以下是异常继承层次结构的概述：

```text
+ BaseError|+ --- + ExchangeError| || + --- + AuthenticationError| | || | + --- +权限被拒绝| | || | + --- +帐户已暂停| || + --- +需要参数| || + --- + BadRequest| || + --- + BadResponse| | || | + --- + NullResponse| || + --- +资金不足| || + --- +无效地址| | || | + --- +地址待定| || + --- +无效订单| | || | + --- + OrderNotFound| | || | + --- + OrderNotCached| | || | + --- +取消待定| | || | + --- +立即订购| | || | + --- + OrderNotFillable| | || | + --- + DuplicateOrderId| || + --- +不支持|+ --- + NetworkError（可恢复）    |    + --- + InvalidNonce    |    + --- + RequestTimeout    |    + --- + ExchangeNotAvailable    | |    | + --- +维护中    |    + --- + DDoS保护        |        + --- + RateLimitExceeded
```

本类是各种错误，包括无障碍和请求/响应不匹配的一般错误类。如果不需要区分错误，则用户至少应捕获此异常。`BaseError`

错误层次结构中有两种特殊情况或子树的通用类，它们均源自：`BaseError`

* `NetworkError`
* `ExchangeError`

A 是非关键性的不间断错误，不是真正意义上的错误，而更像是暂时的不可用性情况，它可能是由任何状况或任何因素（包括维护，DDoS保护和临时禁令）引起的。之所以拥有一个庞大的家族，是为了将所有可能在以后的重试或从其他位置重试的情况下可能再次出现或消失的异常归为一组，其余所有条件都是相同的（使用相同的用户输入，简单地说，相同的定单价格和金额，相同符号等）。`NetworkErrorNetworkError`

相反，的确是一个严重错误，它与的错误非常不同-如果输入内容与相同，则在输入相同的内容时，应该始终保持相同。`ExchangeErrorNetworkErrorExchangeErrorExchangeError`

两个例外家族之间的区别是，一个家族是可恢复的，而另一个家族是不可恢复的。意味着您可以稍后重试，并且它可以自行消失，因此后续重试可能会成功，并且用户可以通过等待而从中恢复。An 是一个致命错误，因此，这意味着某些情况很糟糕，并且每次都将变得很糟糕，除非您更改输入。`NetworkErrorNetworkErrorExchangeError`

### ExchangeError <a id="exchangeerror"></a>

当交换服务器回复JSON错误时，抛出此异常。可能的原因：

* 端点被交换机关闭
* 在交易所未找到交易品种
* 缺少必需的参数
* 参数格式不正确
* 交易所回复答案不明确

其他异常源自：`ExchangeError`

* `NotSupported`注意：如果Exchange API不提供/不支持端点，则会引发此异常。
* `AuthenticationError`：在交易所需要您缺少的API凭证之一来指定时，或者在密钥对中存在错误或现时的现时时引发。大多数情况下，您需要并且有时也需要和/或。`apiKeysecretuidpassword`
* `PermissionDenied`：在无法执行指定操作或对指定权限不足时引发。`apiKey`
* `InsufficientFunds`：当您的帐户余额中没有足够的货币来下订单时，会引发此异常。
* `InvalidAddress`：此异常在遇到一个坏的资金地址或地址资金比较短的提出到一个呼叫（10个字符默认情况下），或。`.minFundingAddressLengthfetchDepositAddresscreateDepositAddresswithdraw`
* `InvalidOrder`：此异常是与统一订单API相关的所有异常的基类。
* `OrderNotFound`：在您尝试获取或取消不存在的订单时引发。

### 网络错误 <a id="networkerror"></a>

与网络相关的所有错误通常都是可恢复的，这意味着网络问题，流量拥塞，不可用通常与时间有关。通常，稍后重​​试通常足以从NetworkError中恢复，但是如果仍然无法解决，则可能表明交换机或您的连接存在一些持久性问题。

#### DDoS防护 <a id="ddosprotection"></a>

在以下两种情况之一中都会引发此异常：

* 对每个用户或区域/位置实施Cloudflare或Incapsula速率限制器限制时
* 当交换限制用户访问请求端点的频率太高时

除了默认错误处理外，ccxt库还在从交换机收到的响应中针对以下关键字之一进行不区分大小写的搜索：

* `cloudflare`
* `incapsula`
* `overload`
* `ddos`

#### 请求超时 <a id="requesttimeout"></a>

当与交换机的连接失败或在指定的时间内未完全接收到数据时，将引发此异常。这由选项控制。当上升时，用户不知道的请求的结果（无论它是由Exchange服务器接受与否）。`timeoutRequestTimeout`

因此，建议以以下方式处理此类异常：

* 用于获取请求，可以安全地重试呼叫
* 对于用户的请求，要求第二次重试相同的呼叫。相反，如果重试的用户呼叫，，或马上不重试调用，这可能会导致缓存下跌不同步。后续重试将返回以下可能结果之一：`cancelOrderfetchOrderfetchOrdersfetchOpenOrdersfetchClosedOrderscancelOrder.orderscancelOrder`
  * 请求已成功完成，这意味着订单已被立即正确取消
  * 引发异常，这意味着该订单或者在第一次尝试中已经被取消，或者在两次尝试之间的同时已经执行（执行和关闭）。请注意，该订单在缓存中仍将具有状态。要确定实际的订单状态，您需要调用以正确更新缓存（可从交易所获得）。如果方法是ccxt库，则将订单标记为。如果余额未更改（未发生交易），则用户必须调用并将订单状态设置为手动。`OrderNotFound'open'.ordersfetchOrderfetchOrder'emulated''closed'fetchBalance'canceled'`
* 如果用户请求失败，则应该：`createOrderRequestTimeout`
  * 更新缓存中调用，，以检查请求下订单成功，现在的顺序是开放的`.ordersfetchOrdersfetchOpenOrdersfetchClosedOrders`
  * 如果不是订单，则用户应检查自第一次运行创建订单以来余额是否已更改，然后在第二次检查之前已完成并关闭了余额。请注意，依靠缓存进行余额推断，因此仅应在更新缓存后调用！`'open'fetchBalancefetchBalance.orders`

#### ExchangeNotAvailable <a id="exchangenotavailable"></a>

当基础交换不可达时，抛出这种类型的异常。

如果ccxt库检测到以下任何关键字作为响应，也会引发此错误：

* `offline`
* `unavailable`
* `busy`
* `retry`
* `wait`
* `maintain`
* `maintenance`
* `maintenancing`

#### InvalidNonce <a id="invalidnonce"></a>

当您的现时数小于与密钥对一起使用的前一个现时数时引发，如“ [身份验证”](https://github.com/ccxt/ccxt/wiki/Manual#authentication)部分所述。在以下情况下会抛出这种类型的异常（按检查的优先顺序）：

* 您不是在限制请求的速率，也不是发送太多的请求。
* 您的API密钥不是新的（已经与某些其他软件或脚本一起使用，仅在添加此或那个交换时始终创建一个新的密钥对）。
* 跨交换类的多个实例共享同一密钥对（例如，在多线程环境中或在单独的进程中）。
* 您的系统时钟不同步。由于时钟漂移，系统时间应在非DST时区中与UTC同步，频率为每十分钟一次或什至更频繁。**在Windows中启用时间同步通常是不够的！**您必须使用操作系统注册表（操作系统的Google _“时间同步频率”_）进行设置。

## 故障排除 <a id="troubleshooting"></a>

如果您在连接到特定交换机时遇到任何困难，请按照优先顺序执行以下操作：

* 确保您拥有最新版本的ccxt。
* 检查[问题](https://github.com/ccxt/ccxt/issues)以获取最新更新。
* 转以获取有关它的更多详细信息。`verbose = true`
* 通过在代码的开头添加以下两行，Python人员可以使用标准的pythonic logger来打开DEBUG日志记录级别：

  ```text
  导入日志logging.basicConfig（level = logging.DEBUG）
  ```

* 使用详细模式以确保所使用的API凭据与您打算使用的密钥相对应。确保密钥对没有混淆。
* **如果可能，请尝试使用新的新密钥对。**
* 在交换网站上检查密钥对上的权限！
* 如果是Cloudflare保护错误，请尝试以下示例：
  * [https://github.com/ccxt/ccxt/blob/master/examples/js/bypass-cloudflare.js](https://github.com/ccxt/ccxt/blob/master/examples/js/bypass-cloudflare.js)
  * [https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare.py](https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare.py)
  * [https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare-with-cookies.py](https://github.com/ccxt/ccxt/blob/master/examples/py/bypass-cloudflare-with-cookies.py)
* 检查您的现时。如果您将API密钥与其他软件一起使用，则很可能应该覆盖您的现时函数以匹配您以前的现时值。通常，可以通过生成新的未使用的密钥对来轻松重置随机数。如果您在使用现有密钥时出现随机数错误，请尝试使用尚未使用的新API密钥。
* 如果您遇到随机数错误，请检查您的请求率。您的私人要求不应很快跟进。您不应该在瞬间或短时间内将它们一个接一个地发送。如果您在发送每个新请求之前不拖延时间，则交易所很可能会禁止您。换句话说，您不应通过过于频繁地发送无限制的私人请求来达到其速率限制。延迟您的后续请求或启用内置的速率限制器，如长轮询器[示例](https://github.com/ccxt/ccxt/tree/master/examples)（也在[此处）所示](https://github.com/ccxt/ccxt/wiki/Manual#order-book--market-depth)。
* 阅读[文档以进行交流](https://github.com/ccxt/ccxt/wiki/Exchanges)，并将详细输出与文档进行比较。
* 通过使用浏览器访问交换机来检查与交换机的连接。
* 通过代理检查与交换机的连接。阅读“ [代理”](https://github.com/ccxt/ccxt/wiki/Install#proxy)部分以了解更多详细信息。
* 尝试从另一台计算机或远程服务器访问交换，以查看这是交换的本地还是全局问题。
* 检查最近是否有来自交易所的任何有关停机维护的消息。有些交易所会定期离线（例如每周一次）以进行更新。

### 笔记 <a id="notes"></a>

* 使用该选项或实例化麻烦的交换，以查看HTTP请求和响应的详细信息。如果您在GitHub上提交问题，则详细输出也将用于我们对其进行调试。`verbose = truenew ccxt.exchange ({ 'verbose': true })`
* 在Python中使用DEBUG记录！
* 如上所述，某些交易所在某些国家/地区不可用。您应该使用代理服务器或将服务器放置在距离交易所较近的地方。
* 如果您收到验证错误或_“无效密钥”_错误，则最有可能是由于随机数问题引起的。
* 如果某些交易所无法验证您的请求，则不会明确说明。在这种情况下，他们可能会使用异常的错误代码进行响应，例如HTTP 502错误的网关错误或与错误的实际原因无关的东西。
* …

`UNDER CONSTRUCTION`

