---
description: integration-faq
---

# 整合常见问题

## 整合常见问题

## 积分 <a id="integration"></a>

### 列入CCXT或与CCXT集成意味着什么？ <a id="what-does-it-mean-to-get-listed-or-integrated-with-ccxt"></a>

请参阅我们的报价的描述在这里：[https://ccxt.trade/offer](https://ccxt.trade/offer)

集成交换API意味着要在CCXT框架内实现该API，并添加对使用CCXT进行交换的自动算法交易的支持。集成后，该交换将置于“ [支持的交换](https://github.com/ccxt/ccxt#supported-cryptocurrency-exchange-markets) ”列表中。

### 如何将交换与CCXT库集成在一起？ <a id="how-to-integrate-an-exchange-with-the-ccxt-library"></a>

通常，有两种方法可以使交换与CCXT集成在一起。

首先是通过GitHub提交请求请求。如果您还没有机会，请查看我们的“ [贡献](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md)准则”和“ [要求”](https://github.com/ccxt/ccxt/wiki/Requirements)。他们应该为您提供所需的信息，以便我们提交所需的Javascript。

当您提交代码时，我们的CI系统会自动对其进行检查。如果失败，它将显示您的代码不符合我们要求的地方。错误将为您列出，您将可以修复这些错误并再次提交。通过所有自动化测试后，我们将进行最终的人工审查，并且我们的开发团队会非常积极地评论PR，并在您处理提交的问题时提供对问题的反馈。`.js`

一个关键的注意事项是，用于提交的是Javascript的受限且形式化的子集。这是因为我们的编译器需要理解100％的代码才能从中生成PHP和Python代码。因此，所有提交内容都必须遵循我们的`.js`[贡献](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md)文档中所述的**字面意义**。

强迫开发人员在这一子集中工作通常会导致延迟，但这是我们将每种三种语言都集成到CCXT库中的唯一方法。违反`.js`[贡献](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md)准则的PR 必须先进行修复，然后再进行合并。

根据我们的经验，外部开发人员需要6到8周的时间才能成功通过自动化测试，即使这样，通常也无法正确实施所有方法。对于某些贡献者来说，这可能很好，但我们也了解，有时交易所希望快速完成集成，以便他们可以利用机会。

因此，第二种选择是雇用CCXT开发团队为您完成集成。所有CCXT认证的集成都是由我们的开发团队以及其他更多受欢迎的交易所完成的。我们不负责整合交易所本身或其他贡献者完成的实现。如果交易所希望CCXT开发团队在保证的时间内快速完成高质量的工作，我们只会收取费用。

### 雇用CCXT开发团队需要多少费用？ <a id="how-much-does-it-cost-to-hire-the-ccxt-dev-team"></a>

我们对集成的定价**为10000美元起，**用于对标准和常规集中式RESTful Exchange API进行优先级排序和集成。

非标准，非常规和分散式API具有其自身的复杂性，因此集成分布式REST API的成本为**15000美元起**，最终报价取决于所讨论API的具体情况。我们要求您先支付50％的预付款才能开始工作。积分以稳定币支付。

### 雇用CCXT开发团队后需要多长时间进行整合？ <a id="how-long-does-it-take-to-get-integrated-after-hiring-the-ccxt-dev-team"></a>

如果您雇用我们进行集成，则通常会在10-12天内使用所有可用方法完成并发布。非标准集成可能需要更长的时间。如果以后发现错误，我们将保证工作。

### 我们没有REST API，但是有WebSocket API，是否可以集成WS API？ <a id="we-dont-have-a-rest-api-but-we-have-a-websocket-api-is-it-possible-to-integrate-a-ws-api"></a>

CCXT当前是仅用于REST的库，但是，CCXT开发团队意识到了对WS API的需求，并[宣布了发布**CCXT Pro的**](https://github.com/ccxt/ccxt/issues/56#issuecomment-507290536)[计划，](https://github.com/ccxt/ccxt/issues/56#issuecomment-507290536)[**CCXT Pro**](https://github.com/ccxt/ccxt/issues/56#issuecomment-507290536)是CCXT的专业附加组件，支持WebSockets等。CCXT Pro将在2019年底之前发布。

CCXT Pro WebSocket集成成本：

* 子WS API，**超过$ 10000**
* Sub + pub WS API，**15000美元以上**

## 资质认证 <a id="certification"></a>

### 获得CCXT认证意味着什么？ <a id="what-does-it-mean-to-get-certified-with-ccxt"></a>

为了交流，我们还提供[认证](https://github.com/ccxt/ccxt/wiki/Certification)计划。

这样一来，该交易就在我们首页的顶部，显示在我们的“ [认证交易”](https://github.com/ccxt/ccxt#certified-cryptocurrency-exchanges)列表中，并为用户提供了醒目的醒目的“ Certified”徽标。认证有助于交易所获得流动性并扩大用户基础。

认证徽章是优质商标，因此交换API必须符合[要求](https://github.com/ccxt/ccxt/wiki/Requirements)。

### 获得认证需要多少费用？ <a id="how-much-does-it-cost-to-be-certified"></a>

认证是每年预付款的，因此是经常性付款。它的费用**为每年$ 5000**，在那一年，CCXT开发团队将保证提供支持，更新，快速修复和维护，以确保为算法交易者提供最佳的API体验。

### 获得认证需要多长时间？ <a id="how-long-does-it-take-to-get-certified"></a>

对于CCXT开发团队进行的集成–在您支付认证费用后即可立即获得认证。对于通过PR提交的集成，可能需要花费一些时间先清理代码。

### 我们可以在认证交易所列表中排名更高吗？ <a id="can-we-get-higher-in-the-list-of-certified-exchanges"></a>

不，所有列表均以自然字母数字顺序排序。

## 晋升 <a id="promotion"></a>

### 您提供哪种广告或促销？ <a id="what-kinds-of-advertisement-or-promotion-do-you-offer"></a>

我们提供以下广告选项：

* 主要的横幅“赞助商推广”一节中我们的页面在GitHub上：[https://github.com/ccxt/ccxt\#sponsored-promotion](https://github.com/ccxt/ccxt#sponsored-promotion)
* 包含一个班轮广告的“参见”部分：[https://github.com/ccxt/ccxt\#see-also](https://github.com/ccxt/ccxt#see-also)

### 促销费用是多少？ <a id="how-much-does-promotion-cost"></a>

* Sponsored Promotion横幅广告费用**为每月$ 3000**（预付），至少需要1个月。
* “另请参阅”单层广告**每月**收费**500美元**，至少要预付3个月的费用。

## 统计 <a id="statistics"></a>

### 集成后，您能否提供有关用户响应交换的统计信息？ <a id="can-you-provide-statistics-on-the-user-response-the-exchange-after-the-integration"></a>

* 在这里，我们是比特币后3：[https://github.com/topics/bitcoin](https://github.com/topics/bitcoin)
* 在这里，我们是＃2复仇后：[https://github.com/topics/ethereum](https://github.com/topics/ethereum)

目前，我们每个月的下载量超过50万。今年早些时候，我们每月下载量达到100万。我们的更多统计信息：[https](https://github.com/ccxt/ccxt/wiki/Stats) : [//github.com/ccxt/ccxt/wiki/Stats](https://github.com/ccxt/ccxt/wiki/Stats)。

### 关于广告的可能性，能否请您每月分享一些点击/观看次数？ <a id="regarding-ads-possibilities-can-you-share-some-numbers-of-clicks-views-monthly-for-each-one-please"></a>

每月的网页浏览量统计数据每月超过100000次浏览，其中20000-25000位是唯一主机。GitHub页面上的链接是直接链接，我们不控制点击率。我们的流量是高度集中的专业交易流量，这意味着它带来了流动性和交易资本，因为CCXT库每天被公司和私人交易商使用。

