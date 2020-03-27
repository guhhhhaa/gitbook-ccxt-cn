# contributing

## 贡献

```text
-该文件正在开发中，有关贡献的准则正在制定中！
```

## 如何提交问题 <a id="how-to-submit-an-issue"></a>

如果您要提交问题，并且希望快速解决问题，请参考以下清单：

* 阅读《[手册》](https://github.com/ccxt/ccxt/wiki/Manual)，尤其要仔细阅读以下各节：
  * [交换性能](https://github.com/ccxt/ccxt/wiki/Manual#exchange-properties)
  * [限速](https://github.com/ccxt/ccxt/wiki/Manual#rate-limit)
  * [DDoS保护](https://github.com/ccxt/ccxt/wiki/Manual#ddos-protection-by-cloudflare--incapsula)
  * [认证](https://github.com/ccxt/ccxt/wiki/Manual#authentication)
  * [API密钥设置](https://github.com/ccxt/ccxt/wiki/Manual#api-keys-setup)
* 阅读[故障排除](https://github.com/ccxt/ccxt/wiki/Manual#troubleshooting)部分，并按照故障排除步骤进行操作。
* 阅读[FAQ](https://github.com/ccxt/ccxt/wiki/FAQ)中最常见的问题。
* 阅读[API文档](https://github.com/ccxt/ccxt/wiki/Exchange-Markets)以进行交换。
* 首先搜索类似的问题，以避免重复。
* 如果您的问题是唯一的，以及故障的基本描述，则**需要**执行以下操作：
  * **在调用交换实例的函数或方法之前，在交换实例上设置属性`exchange.verbose = true`**
  * **不要发布代码或错误的消息，请以纯文本形式发布输出和代码！**
  * **具有三行反引号的环绕代码和输出：**
  * 不要将反引号（\`）与引号（\'）混淆：'''BAD'''
  * 不要将单个反引号与三个反引号相混淆：\`BAD\`
  * 粘贴您遇到困难的完整代码段，避免单行
  * 粘贴失败方法的**完整详细输出**，而无需使用键
  * 详细输出应包括交换的请求和响应（而不仅仅是错误调用栈）
  * 写你的语言**和版本**
  * 编写ccxt库版本
  * 是哪个交易所
  * 您尝试调用哪种方法

## 报告漏洞和关键问题 <a id="reporting-vulnerabilities-and-critical-issues"></a>

如果您发现安全问题或严重漏洞，并在公共场合举报将会带来风险–请随时向我们发送消息至[info@ccxt.trade](mailto:info@ccxt.trade)。

## 如何贡献代码 <a id="how-to-contribute-code"></a>

* [**确保您的代码统一**](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#derived-exchange-classes)**！**

  ↑这是最重要的规则。

* **请不要在拉动请求中提交以下文件：**
  * `/doc/*`（这些文件是从生成的，将您的编辑放在此处）`/wiki/*`
  * `/build/*` （这些是自动生成的）
  * `/php/*` （基本类除外）
  * `/python/*` （基本类除外）
  * `/ccxt.js`
  * `/README.md` （交换列表是自动生成的）
  * `/package.json`
  * `/package.lock`
  * `/wiki/*` （除了真正的编辑，交换列表是自动生成的）
  * `/dist/ccxt.browser.js` （这也会自动浏览）

这些文件已生成（在[下面说明](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#multilanguage-support)），并且在构建时将被覆盖。请不要提交它们，以免膨胀已经很大的存储库。通常，您只需要提交一个源文件即可提交对交换实现的编辑。

* **请提交原子编辑，一次交换一次拉动请求，请勿混合**
* **通过运行来确保您的代码通过所有语法检查** **`npm run build`**

## 待处理的任务 <a id="pending-tasks"></a>

下面列出了我们现在想首先在库中实现并完全**统一**的功能。这些任务大多数已经在进行中，已经为某些交流实施了，但并不是全部：

* 保证金交易
* 杠杆作用
* 衍生产品（期货，期权）
* 主账户/子账户
* 有条件的订单（止损，止盈）
* `transfer` 子帐户和主帐户之间
* `fetchTransfer`
* `fetchTransfers`
* `fetchLedger`
* `fetchPositions`
* `closePosition`
* `closePositions`

如果您想通过提交部分实现来做出贡献，请确保在库中（已实现的地方）查找有关其完成方式的示例，并复制采用的实践。

如果您的提案，建议或改进在提交之前与上述任务清单无关，请确保它是：1.大多数ccxt用户确实需要2.旨在作为通用解决方案，未针对您的特定要求进行硬编码需求3.以与所有交易所兼容的通用方式完成（并非特定于交易所）4.便携式（所有受支持的语言均可用）5.健壮6.明确地在做什么7.不会破坏任何内容（如果您更改方法，请确保其他所有调用了edited方法的方法均未损坏）

以下是有助于ccxt库代码库的一组规则。

## 你需要什么 <a id="what-you-need-to-have"></a>

最简单的方法是使用Docker在安装了所有依赖项的情况下运行隔离的构建和测试环境：

```text
docker-compose运行--rm ccxt
```

这将建立一个容器并打开一个外壳，在该外壳中，and 命令应直接使用即可。`npm run buildnode run-tests`

CCXT文件夹已映射到容器内部，但该文件夹除外-容器将具有自己的临时副本-这样就不会弄乱本地安装的模块。这意味着您可以使用自己喜欢的编辑器在主机上编辑源，并在运行的容器中构建/测试它们。`node_modules`

这样，您可以使构建工具和过程保持隔离状态，而不必经历将所有这些依赖项手动安装到主机的痛苦过程。

如果您选择困难的方式，那么这里是您将需要的依赖项列表。它可能不完整且过时，因此您可能需要查看和脚本，以获取我们用于安装构建和测试CCXT所需的最新依赖关系的命令列表。[`Dockerfile`](https://github.com/ccxt/ccxt/blob/master/Dockerfile)[`.travis.yml`](https://github.com/ccxt/ccxt/blob/master/.travis.yml)

* [Node.js的](https://nodejs.org/en/download/) 8+
* [Python的](https://www.python.org/downloads/) 3.5.3+和Python 2.7+
  * 毒物（或）`brew install toxpip install tox`
  * 要求（）`pip install requests`
  * aiohttp（）`pip install aiohttp`
* [PHP](https://secure.php.net/downloads.php) 5.3+具有以下扩展名安装并启用：
  * 卷曲
  * 图标
  * mbstring
  * 聚四氟乙烯
  * bcmath（php &lt;7.1）
* [Pandoc](https://pandoc.org/installing.html) 1.19+

## 你需要知道什么 <a id="what-you-need-to-know"></a>

### 储存库结构 <a id="repository-structure"></a>

存储库的内容结构如下：

```text
/＃根目录，也就是Node.js的npm module / package文件夹/.babelrc＃用于创建库的ES5版本的babel配置/.eslintrc＃林特/.gitattributes＃包含用于回购中语言检测的语言学家设置/.gitignore＃忽略它/.npmignore＃从NPM软件包中排除的文件/.travis.yml＃travis-ci的YAML配置（连续集成）/CONTRIBUTING.md＃此文件/LICENSE.txt＃MIT/README.md＃适用于GitHub，npmjs.com，npms.io，yarn等的master markdown/ build /＃构建脚本/build/export-exchanges.js＃用于在构建过程中在文档中创建交换表/build/transpile.js＃编译脚本/build/update-badges.js＃一个JS脚本来更新自述文件和文档中的徽章/build/vss.js＃从package.json读取单源版本并将其写入到各处/ dist /＃生成的CCXT浏览器捆绑包的文件夹/ccxt.js＃ccxt库的主JS版本的入口点/ccxt.php＃ccxt库的PHP版本的入口点/ doc /＃Sphinx为http://ccxt.readthedocs.io/生成的rst-docs/ js /＃库的JS版本/ php /＃PHP ccxt模块/软件包文件夹/ python /＃PyPI的Python ccxt module / package文件夹/python/__init__.py＃ccxt.library的Python版本的入口点/python/async/__init__.py＃ccxt.library的异步版本（适用于Python 3.5.3+ asyncio）/ python / base /＃ccxt库的Python版本的基本代码/python/MANIFEST.in＃一个PyPI软件包文件，列出了额外的软件包文件（许可证，配置等...）/python/README.rst＃为PyPI生成了reStructuredText/python/setup.cfg＃Python软件包的wheel配置文件/python/setup.py＃Python中ccxt的pip / setuptools脚本（构建/安装）/python/tox.ini＃Python的tox配置/ examples /＃不言自明/ examples / js＃.../ examples / php＃.../ examples / py＃.../exchanges.cfg＃自定义捆绑包配置，仅包括您需要的交换/package.json＃npm软件包文件，也用于setup.py中，用于版本单源/run-tests.js＃前端，用于以所有语言（JS / PHP / Python）运行所有交换的独立测试/ wiki /＃所有文档的来源（编辑在此处）
```

### 多语言支持 <a id="multilanguage-support"></a>

ccxt库提供三种不同的语言（以后还会提供）。我们鼓励开发人员设计_可移植的_代码，以便单语言用户可以阅读其他语言的代码并轻松理解它。这有助于图书馆的采用。主要目标是为尽可能多的现有加密货币交易所提供通用，统一，一致且健壮的接口。

首先，所有特定于语言的版本都是并行开发的，但彼此分开。但是，当在所有支持的语言中维护和保持代码的一致性变得太困难时，我们决定切换到所谓的_源/生成_过程。现在有一种语言的单一源代码版本，即JavaScript。其他特定于语言的版本是从源版本自动语法导出（编译，生成）的。但这并不意味着您必须是JS编码人员才能做出贡献。可移植性原则允许Python和PHP开发人员也有效地参与源代码版本的开发。

模块入口点是：

* `./python/__init__.py` 用于Python pip包
* `./python/async/__init__.py` 适用于Python 3.5.3+ ccxt.async\_support子软件包
* `./ccxt.js` 用于Node.js npm包
* `./dist/ccxt.browser.js` 用于浏览器捆绑
* `./ccxt.php` 对于PHP

通过命令从源文件和文件中编译生成的版本和文档。`ccxt.js./js/npm run build`

### 转译（生成的）文件 <a id="transpiled-generated-files"></a>

* 所有派生的交换类都是从源JS文件自动转译的。源文件与语言无关，可以轻松地线对线映射到任何其他语言，并以跨语言兼容的方式编写。任何编码器都​​可以读取（通过设计）。
* **不是**编译所有基类，**而是**针对特定语言。

#### 的JavaScript <a id="javascript"></a>

所述与从巴别源产生。`ccxt.browser.js`

#### 蟒蛇 <a id="python"></a>

这些包含派生交换类的文件从JS转换为Python：

* `js/[_a-z].js` → `python/ccxt/async/[_a-z].py`
* `python/ccxt/async[_a-z].py`→ （Python 3异步→Python 2同步转换阶段）`python/ccxt/[_a-z].py`
* `python/test/test_async.py`→ （同步测试是通过异步测试生成的）`python/test/test.py`

这些Python基类和文件不会被转译：

* `python/ccxt/base/*`
* `python/ccxt/async/base/*`

#### 的PHP <a id="php"></a>

这些包含派生交换类的文件从JS转换为PHP：

* `js/[_a-z].js` → `php/[_a-z].php`

这些PHP基类和文件不会被转译：

* `php/base/*`

#### 打字稿 <a id="typescript"></a>

* `js/[_a-z].js` → `ccxt.d.ts`

### 基类 <a id="base-class"></a>

`UNDER CONSTRUCTION`

### 派生交易所类别 <a id="derived-exchange-classes"></a>

Transpiler基于正则表达式，在很大程度上依赖于特定的格式设置规则。如果破坏它们，则编译器将完全无法生成Python / PHP类，或者将生成格式错误的Python / PHP语法。

以下是有关如何保持JS代码可移植性的主要说明。

在建造之前，请使用棉绒。它将涵盖许多（但不是全部）问题，因此如果移植失败，仍然需要手动检查。`npm run lint js/your-exchange-implementation.js`

如果您在运行时看到异常或任何其他翻译错误，请检查您的代码是否满足以下规则：`[TypeError] Cannot read property '1' of nullnpm run build`

* 不要在您的方法中放入空行
* 始终使用Python样式的缩进，所有语言都保留原样
* **精确**缩进4个空格，避免使用制表符
* 在每个方法之间放置一个空行
* 避免混合使用注释样式，请在JS中对行注释使用双斜杠`//`
* 避免多行注释

如果转译过程成功完成，但是生成了错误的Python / PHP语法，请检查以下内容：

* 每个开口支架都喜欢或应该在其前面有一个空格！`({`
* 即使您确实想使用特定语言的代码语法糖
* 将所有映射和理解展开为基本的for循环
* 不要更改被重写的继承方法的参数，在所有交换中保持一致
* 仅使用基类方法执行所有操作（例如，用于将对象转换为json）。`this.json ()`
* 总是在每个语句的末尾加上分号，如PHP / C风格`;`
* 所有相关键在任何地方都必须是单引号字符串， `array['good'], array.bad`
* 变量应在语义上用或关键字声明（否！），在任何地方都应首选`constletvarconst`

并且在结构上：

* 如果您需要其他基本方法，则必须用所有三种语言来实现
* 不要从统一方法发出多个HTTP请求
* 尝试将语法简化为基本的一线表达
* 多行是可以的，但是您应该避免使用大量括号进行深度嵌套
* 避免将引用传递给参数和参数的内容更改为函数调用
* 不要使用过于复杂的条件语句（如果用括号括起来的话）
* 不要使用繁重的三元条件
* 避免操作混乱（**不这样做**：）`a && b || c ? d + 80 : e ** f`
* 不要使用，而是使用！`.includes().indexOf()`
* 永远不要在浮点数上使用：`.toString()Number (0.00000001).toString () === '1e-8'`
* 不要使用闭包，或者在派生类中不可接受`a.mapa.filter (x => (x === 'foobar'))`
* 不要使用运算符检查值是否在非关联数组（列表）中`in`
* 不添加自定义货币或符号/货币对转换和格式，而是从现有代码中复制
* **不要访问不存在的密钥，将无法使用其他语言！`array['key'] || {}`**
* 保持简单，一行不要多于一条语句

#### 发送市场编号 <a id="sending-market-ids"></a>

大多数交易所的API端点都需要在请求中指定特定于交易所的市场代码或交易对或工具。

**我们不会将统一符号直接发送给交易所！**它们不可互换！_交易所专用的市场编号_和_统一的符号_之间有很大的区别！这在《手册》中有解释：

* [https://github.com/ccxt/ccxt/wiki/Manual\#markets](https://github.com/ccxt/ccxt/wiki/Manual#markets)
* [https://github.com/ccxt/ccxt/wiki/Manual\#symbols-and-market-ids](https://github.com/ccxt/ccxt/wiki/Manual#symbols-and-market-ids)

**永远不要这样做：**

```text
异步fetchTicker （symbol ，params = { } ）{       const request = {       'pair' ：symbol ，//非常糟糕，直接向交易所发送统一的符号    } ;   const response = 等待此。publicGetEndpoint （请求）;      //以统一的方式解析...}
```

**不要这样做：**

```text
异步fetchTicker （symbol ，params = { } ）{       const request = {       'symbol' ：symbol ，//非常糟糕，直接向交易所发送统一的符号    } ;   const response = 等待此。publicGetEndpoint （请求）;      //以统一的方式解析...}
```

我们**始终没有**将统一的CCXT符号发送给交易所，而是**始终**采用与该符号对应的特定于交易所的市场。如果发生这种情况，则特定于交易所的市场ID与CCXT统一符号完全相同–这是一个巧合，但是我们从不依赖于统一CCXT API。`id`

要通过统一的CCXT符号获取特定于交易所的市场ID，请使用以下方法：

* `this.market (symbol)`-返回整个统一市场结构，包含，，，和许多其他有趣的事情`idbaseIdquoteId`
* `this.marketId (symbol)`– 通过统一的符号仅返回特定于市场的交易（如果您不需要其他任何内容）`id`

**好的例子：**

```text
异步fetchTicker （symbol ，params = { } ）{       const market = this 。市场（符号）; //整个市场结构      const request = {       'pair' ：market [ 'id' ] ，//好，我可能相等，但经常有所不同，没关系    } ;   const response = 等待此。publicGetEndpoint （此。延伸（请求，PARAMS ））;       //以统一的方式解析...}
```

```text
异步fetchTicker （symbol ，params = { } ）{       const marketId = this 。marketId （符号）; //只是ID      const request = {       'symbol' ：marketId ，//好，我可能相等，但经常有所不同，没关系    } ;   const response = 等待此。publicGetEndpoint （此。延伸（请求，PARAMS ））;       //以统一的方式解析...}
```

#### 解析符号 <a id="parsing-symbols"></a>

当向交易所发送请求时，统一符号必须被_“转换”_到交易所特定的市场，如上所示。另一面也是如此-收到交换响应时，它内部具有特定于交换的市场，必须将其_“转换回”_为统一的CCXT符号。`idid`

**我们不会将交易所专用市场直接放入统一结构中！**我们不能自由地将符号与ID互换！_特定_于_交易所的市场编号_和_统一符号_之间存在显着差异！这在《手册》中有解释：**`id`**

* [https://github.com/ccxt/ccxt/wiki/Manual\#markets](https://github.com/ccxt/ccxt/wiki/Manual#markets)
* [https://github.com/ccxt/ccxt/wiki/Manual\#symbols-and-market-ids](https://github.com/ccxt/ccxt/wiki/Manual#symbols-and-market-ids)

**永远不要这样做**：

```text
parseTrade （trade ，market = undefined ）{     //解析代码...   返回{       'info' ：贸易，      'symbol' ：trade [ 'pair' ] ，//非常糟糕，以统一的结构返回交易所特定的市场编号！       //其他字段...   } ;}
```

**不要这样做**

```text
parseTrade （trade ，market = undefined ）{     //解析代码...   返回{       'info' ：贸易，      'symbol' ：trade [ 'symbol' ] ，//非常糟糕，以统一的结构返回特定于交易所的市场ID！       //其他字段...   } ;}
```

为了正确处理市场，必须在此交换中缓存的信息中查找：`idloadMarkets()`

**好的例子：**

```text
parseTrade （trade ，market = undefined ）{     让symbol = undefined ;   const marketId = this 。safeString （trade ，'pair' ）;      如果（marketId ！== 未定义）{        如果（marketId 在此。markets_by_id ）{            //首先在预先加载的市场中按交易所特定的ID查找         市场= 这个。market_by_id [ 市场] ;          符号= 市场[ '符号' ] ;      } 其他{           //如果已知格式，请尝试以某种方式解析         const [ baseId ，quoteId ] = marketId 。分割（'/' ）;            const base = this 。safeCurrencyCode （baseId ）; //统一            const quote = this 。safeCurrencyCode （quoteId ）;           符号= 基础+ '/' + 引号;        }   }   //解析代码...   返回{       'info' ：贸易，      'symbol' ：symbol ，//很好，现在是这里的统一符号       //其他字段...   } ;}
```

#### 访问字典键 <a id="accessing-dictionary-keys"></a>

在JavaScript中，可以用两种表示法来访问字典键：

* `object['key']` （单引号的字符串键符号）
* `object.key` （属性符号）

两者的工作原理几乎相同，并且在执行JavaScript代码时会隐式转换为另一种。

尽管以上内容在JavaScript中都可以使用，但在Python或PHP中则无法使用。在大多数语言中，关联字典键与属性的处理方式不同。因此，在Python中与并不相同。在PHP 中也不一样。区分关联键和属性的语言对两者使用不同的符号。`object.keyobject['key']$object->key$object['key']`

为了保持代码的可移植性，请记住以下简单规则：_始终使用单引号的字符串键表示法来访问整个库中所有语言的所有关联字典键！`object['key']`_

#### 使用- 方法对输入进行消毒`safe` <a id="sanitizing-input-with-safe-methods"></a>

JavaScript比其他语言的限制要少。它将允许尝试取消引用不存在的键，而其他语言将引发异常：

```text
// JavaScript​const someObject = { } ​如果（someObject [ 'nonExistentKey' ] ）{      //此条件的主体不会在JavaScript中执行    //因为someObject ['nonExistentKey'] ===未定义===否    //但JavaScript不会在if子句上引发异常}
```

但是，上述带有_“默认为未定义值”的_逻辑在Python或PHP中不起作用。

```text
＃Pythonsome_dictionary = { } ​＃休息如果some_dictionary [ 'nonExistentKey' ] ：    ＃在Python中尝试取消引用nonExistentKey值    ＃将引发标准的内置KeyError异常​＃作品如果'nonExistentKey' 在some_dictionary 和some_dictionary [ 'nonExistentKey' ] ：      ＃这是在访问值之前检查密钥是否存在的方法​＃也可以如果some_dictionary 。get （'nonExistentKey' ）：    ＃另一种在访问值之前检查键是否存在的方法...
```

大多数语言将不允许尝试访问对象中不存在的键。

由于上述原因，请**不要**在已编译的JS文件中**执行此**操作：

```text
// JavaScriptconst value = object [ 'key' ] || other_value ; //在Python或PHP中不起作用！  if （object [ 'key' ] || other_value ）{ / *在Python或PHP中不起作用！* / }     
```

因此，我们具有一系列功能：`safe*`

* `safeInteger (object, key)`， `safeInteger2 (object, key1, key2)`
* `safeFloat (object, key)`， `safeFloat2 (object, key1, key2)`
* `safeString (object, key)`， `safeString2 (object, key1, key2)`
* `safeValue (object, key)`， `safeValue2 (object, key1, key2)`

该函数用于对象内部的对象，对象内部的数组和布尔值。`safeValuetrue/false`

上面的安全功能将检查对象中是否存在键，并将正确返回JS / Python / PHP的值。每个函数也接受要返回的默认值，而不是最后一个参数。`undefined/None/nullundefined/None/null`

或者，您可以先检查密钥是否存在...

因此，您必须更改此设置：

```text
if （params [ 'foo' ] ！== undefined ）{   }
```

↓

```text
const foo = this 。safeValue （params ，'foo' ）;   如果（foo ！== undefined ）{  }
```

要么：

```text
如果（'富' 在PARAMS ）{   }
```

#### 使用基类密码学方法进行身份验证 <a id="using-base-class-cryptography-methods-for-authentication"></a>

不要重新发明轮子。始终使用基类方法进行加密。

CCXT库支持以下身份验证算法和加密算法：

* HMAC
* JWT（JSON Web令牌）
* RSA
* ECDSA椭圆曲线密码术
  * NIST P256
  * secp256k1
* OTP 2FA（一次性密码2要素身份验证）

基类提供了几种方法，这些方法对于该库中的几乎所有密码学都是关键的。派生交换实现不得将外部依赖项用于加密，所有操作都应仅使用基本方法来完成。`Exchange`

* `hash (message, hash = 'md5', digest = 'hex')`
* `hmac (message, secret, hash = 'sha256', digest = 'hex')`
* `jwt (message, secret, hash = 'HS256')`
* `rsa (message, secret, alg = 'RS256')`
* `ecdsa (request, secret, algorithm = 'p256', hash = undefined)`
* `totp (secret)`
* `stringToBase64()`，，...`base64ToBinary()binaryToBase64()`

该方法支持以下算法：`hash()hash`

* `'md5'`
* `'sha1'`
* `'sha3'`
* `'sha256'`
* `'sha384'`
* `'sha512'`
* `'keccak'`

的编码参数接受下列值：`digest`

* `'hex'`
* `'binary'`

该方法还支持该参数。这是唯一的，其他的实现应该使用有。`hmac()'base64'digesthmac()'binary'binaryToBase64()`

#### 时间戳记 <a id="timestamps"></a>

**该库中所有统一结构中的所有时间戳都是整数时间戳，**_**以毫秒为单位**_**！**

为了将时间戳转换为毫秒，CCXT实现了以下方法：

```text
const data = {    'unixTimestampInSeconds' ：1565242530 ，    'unixTimestampInMilliseconds' ：1565242530165 ，    'stringInSeconds' ：'1565242530' ， } ;​//如果基础值已经以毫秒为单位，则转换为整数const timestamp = this 。safeInteger （data ，'unixTimestampInMilliseconds' ）; // === 1565242530165    ​//转换为整数并乘以一千（如果该值是以秒为单位的UNIX时间戳记）const timestamp = this 。safeTimestamp （data ，'unixTimestampInSeconds' ）; // === 1565242530000    ​//转换为整数，如果以秒为单位，则乘以千const timestamp = this 。safeTimestamp （data ，'stringInSeconds' ）; // === 1565242530000    
```

#### 使用数组长度 <a id="working-with-array-lengths"></a>

在JavaScript中，获取字符串或数组长度的常见语法是引用属性，如下所示：`.length`

```text
someArray 。长度​// 要么​someString 。长度
```

它适用于字符串和数组。在Python中，这是通过类似的方式完成的：

```text
len （some_array ）​＃ 要么​仅（some_string ）
```

因此，对于字符串和数组，都可以以相同的方式访问长度，并且都可以正常工作。

但是，对于PHP，这是不同的，因此字符串长度和数组长度的语法也不同：

```text
计数（some_array ）;​// 要么​strlen （some_string ）; //或mb_strlen 
```

因为transpiler逐行工作，并且不进行代码自省，所以它无法从字符串中分辨出数组，也无法在没有其他提示的情况下正确地转换为PHP。它将始终将JS转换为PHP，并且比字符串长度更喜欢字符串长度。为了正确指示数组长度，我们必须执行以下操作：`.length.lengthstrlen`

```text
const arrayLength = someArray 。长度;//以上行以.length结尾；//结束符是对将识别someArray的编译器的提示//作为此处的数组变量，而不是字符串类型的变量//现在我们可以使用arrayLength进行算术运算
```

该行结尾可以解决问题。数组优先于字符串而不是字符串的唯一情况是循环。在循环的标题中，始终指数组长度（而不是字符串长度）。`.length;.length.lengthforfor.length`

#### 加数字和连接字符串 <a id="adding-numbers-and-concatenating-strings"></a>

在JS中，算术加法运算符同时处理字符串和数字。因此，它可以将字符串连接在一起，也可以对数字求和。Python也是如此。在PHP中，这是不同的，因此它具有不同的字符串连接运算符（“点”运算符）和算术加法运算符（“ plus”运算符）。再一次，由于编译器不进行代码自省，因此它无法确定您是在JS中添加数字还是字符串。在您希望将其转换为其他语言（无论是PHP还是其他语言）之前，它都可以正常工作。为了帮助编译器，我们必须使用算术加法。`+++.+this.sum`

经验法则是：**仅适用于字符串连接（！）**，**适用于算术加法**。运算符与运算符的逻辑相同- 在这些情况下也必须使用。**`+this.sum (a, b, c, ...)`**`+=.=this.sum()`

#### 格式化小数精度 <a id="formatting-decimal-numbers-to-precision"></a>

该方法`.toFixed ()`在JavaScript中具有[已知的舍入错误](https://www.google.com/search?q=toFixed+bug)，其他语言中的其他舍入方法也是如此。为了始终如一地使用数字格式，我们需要使用[《手册》中所述](https://github.com/ccxt/ccxt/wiki/Manual#methods-for-formatting-decimals)的[方法](https://github.com/ccxt/ccxt/wiki/Manual#methods-for-formatting-decimals)。[`decimalToPrecision`](https://github.com/ccxt/ccxt/wiki/Manual#methods-for-formatting-decimals)

#### 转义的控制字符 <a id="escaped-control-characters"></a>

当使用含有像控制字符的字符串，总是将它们用双引号（），而不是单引号（）！单引号字符串不会解析为控制字符，并且会像JavaScript以外的许多语言一样处理。因此，为了使制表符和换行符能够在PHP中使用，我们需要在它们之间加上双引号（尤其是在实现中）。`"\n""\t""'sign()`

坏：

```text
const a = 'GET' + 方法。toLowerCase （）+ '\ n' + 路径;      const b = 'api \ nfoobar.com \ n' ; 
```

好：

```text
const a = 'GET' + 方法。toLowerCase （）+ “ \ n” + 路径；// eslint-disable-line引号       // eslint-disable-next-line引号const b = “ api \ nfoobar.com \ n” ; 
```

**↑** **评论是强制性的！`eslint-*`**

#### 使用三元条件 <a id="using-ternary-conditionals"></a>

不要使用重的三元（）条件，请**始终在三元运算符中使用括号！**`?:`

尽管编程语言本身具有运算符优先级，但编译器是基于正则表达式的，并且不进行代码自省，因此将所有内容均视为纯文本。

需要括号来提示转译者条件的哪一部分。在没有括号的情况下，很难理解开发人员的思路和意图。

以下是一些错误设计的代码示例，这些代码会破坏转译器：

```text
//这是不良代码风格的示例，可能会破坏翻译器const foo = {    'bar' ：'a' + qux === 'baz' 吗？这个。a （）：这个。b （）+ 'b' ，           } ;
```

```text
//这会使翻译员和人工开发人员感到困惑const foo = 'bar' + baz + qux 吗？'a' ：'' + 这个。c （）;        
```

在相应的零件上添加括号将是解决该问题的一种或多或少正确的方法。

```text
const foo = {    '酒吧' ：（qux === '巴兹' ）？这个。a （）：这个。b （），//现在好多了         } ;
```

解决该问题的通用方法是将复杂的行分解为一些简单的行，甚至以增加额外的行和条件为代价：

```text
//之前：// const foo = {//'bar'：'a'+ qux ==='baz'吗？this.a（）：this.b（）+'b'，//};// ------------------------------------------------ ----------------------------//之后：const bar = （qux === 'baz' ）？这个。a （）：这个。b （）；        const foo = {    'bar' ：'a' + bar + 'b' ，   } ;
```

甚至：

```text
//之前：// const foo ='bar'+ baz + qux吗？'a'：''+ this.c（）;// ------------------------------------------------ ----------------------------//之后：让foo = 'bar' + baz ;  如果（qux ）{     foo + = 'a' ; } ;foo + = this 。c （）;  
```

### 新的Exchange集成 <a id="new-exchange-integrations"></a>

**记住：**完全使用此库的关键原因是**Unification**。开发新的交换文件时，目标不是以某种方式实现它，而是以一种非常有趣，精确和精确的方式来实现它，就像实现其他交换一样。为此，我们必须从其他交易所复制逻辑位，并确保新交易所在以下方面符合《手册》：

* 市场IDS，交易对符号，货币标识，标记代码，象征性的统一，必须在所有分析方法进行标准化（，，，，...）`commonCurrenciesfetchMarketsfetchCurrenciesparseTradeparseOrder`
* 所有统一的API方法名称和参数都是标准的-不能随意添加或更改它们
* 所有解析器输入必须为-sanitized `safe`如上所述
* 对于批量操作应中使用的碱的方法（，，注意复数结尾）`parseTradesparseOrderss`
* 尽可能多地使用基本功能，不要重造车轮，自行车或自行车车轮
* 尊重-methods中的默认参数值，检查and和are 而不将其发送给交易所，在这种情况下，我们有意使用交易所的默认值`fetchsincelimitundefined`
* 当实现带有一些参数的统一方法时，我们不能忽略或遗漏任何这些参数
* 统一方法返回的所有结构必须符合《手册》中的规定

请参阅新的集成下列文件：[https://github.com/ccxt/ccxt/wiki/Requirements](https://github.com/ccxt/ccxt/wiki/Requirements)

快速合并新交换集成的拉取请求取决于对上述统一规则和标准的一致性和遵从性。打破其中之一是不合并“拉取请求”的主要原因。

**如果要添加（支持）另一个交换，或为特定的交换实现新方法，则使之保持一致改进的最佳方法是从示例中学习。看一下其他交换所（建议使用经过认证的交换所）中如何实现相同的内容，并尝试复制代码流和样式。**

新交换集成的基本JSON框架如下：

```text
{   'id'：'示例'，   'name'：'Example Exchange'，   '国家/地区'：['美国'，'欧盟'，'CN'，'RU']，   'rateLimit'：1000，   'version'：'1'，   'comment'：'此评论是可选的'，   '网址'：{      '徽标'：'https://example.com/image.jpg'，      'api'：'https://api.example.com/api'，      'www'：'https://www.example.com'，      'doc'：[         'https://www.example.com/docs/api'，         'https://www.example.com/docs/howto'，         'https://github.com/example/docs'，      ]，   }，   'api'：{      '上市'： {         “获取”：[            “端点/示例”，            “订单/ {pair} /满”，            '{pair} / ticker'，         ]，      }，      '私人的'： {         “帖子”：[            '平衡'，         ]，      }，   }，}
```

### 隐式API方法 <a id="implicit-api-methods"></a>

在每次交换的代码中，您会注意到发出API请求的函数没有明确定义。这是因为交换描述JSON中的定义用于在交换子类内部创建_魔术函数_（也称为_部分函数_或_闭包_）。该隐式注入是通过基本交换方法完成的。`apidefineRestApi/define_rest_api`

每个部分函数都有一个字典，并返回API响应。在上面的示例JSON中，结果是注入一个函数。类似地，结果产生一个带有参数的函数（再次传入参数）。`params'endpoint/example'this.publicGetEndpointExample'orderbook/{pair}/full'this.publicGetOrderbookPairFullpairparams`

实例化时，基本交换类从端点列表中获取每个URL，将其拆分为单词，然后使用部分构造从这些单词中组成一个可调用的函数名。在JS，Python和PHP中，该过程也相同。这里也有描述：

* [https://github.com/ccxt/ccxt/wiki/Manual\#api-methods--endpoints](https://github.com/ccxt/ccxt/wiki/Manual#api-methods--endpoints)
* [https://github.com/ccxt/ccxt/wiki/Manual\#implicit-api-methods](https://github.com/ccxt/ccxt/wiki/Manual#implicit-api-methods)
* [https://github.com/ccxt-dev/ccxt/wiki/Manual\#api-method-naming-conventions](https://github.com/ccxt-dev/ccxt/wiki/Manual#api-method-naming-conventions)

`UNDER CONSTRUCTION`

### 持续集成 <a id="continuous-integration"></a>

使用[Travis CI](https://travis-ci.org/ccxt/ccxt)可以自动进行构建。文件中描述了Travis CI的构建步骤。[`.travis.yml`](https://github.com/ccxt/ccxt/blob/master/.travis.yml)

Windows版本通过[Appveyor](https://ci.appveyor.com/project/ccxt/ccxt)自动化。Appveyor的构建步骤在文件中。[`appveyor.yml`](https://github.com/ccxt/ccxt/blob/master/appveyor.yml)

CI服务会自动验证传入的请求请求。您可以在此处在线观看构建过程：[travis-ci.org/ccxt/ccxt/builds](https://travis-ci.org/ccxt/ccxt/builds)。

### 如何在本地计算机上构建和运行测试 <a id="how-to-build-and-run-tests-on-your-local-machine"></a>

在首次构建之前，请安装Node依赖项（如果运行的是Docker映像，请跳过此步骤）：

```text
npm安装
```

下面的命令将构建所有内容，并从源JS文件生成PHP / Python版本：

```text
npm运行构建
```

以下命令将测试生成的生成文件（用于所有交换，符号和语言）：

```text
节点运行测试
```

您可以将测试限制为特定的语言，特定的交换方式或符号：

```text
节点运行测试[--php] [--js] [--python] [--python3] [exchange] [symbol]
```

例如，以下第一行将仅测试库（）的源JS版本。它不需要先运行即可（如果您需要快速验证您的更改是否破坏了代码，可能会很有用）：`ccxt.jsnpm run build`

```text
节点运行测试--js＃测试主ccxt.js，所有交换​＃其他示例需要'npm run build'才能运行​节点运行测试--python＃测试Python 2版本，所有交换节点运行测试--php bitfinex＃使用PHP测试Bitfinex节点运行测试--python3 kraken＃使用Python 3测试Kraken，需要'npm run build'
```

## 提交对存储库的更改 <a id="committing-changes-to-the-repository"></a>

构建过程会在转译的交换文件中生成许多更改，例如，对于Python和PHP。**您不应该将它们提交到GitHub，请仅提交基本（JS）文件更改**。

您可以通过运行以下命令在生成的文件中隐藏更改（此后，生成的文件不再标记为已更改）：

```text
npm运行git-ignore-generated-files
```

以前，我们已将该命令实现为最后的构建步骤，但它在后续选择命令和分支选择命令中都引起了问题（当在那些标记为忽略的文件中发生冲突时）。因此，如果遇到此问题，可以通过执行以下操作忽略这些文件：`git pull`

```text
npm运行git-unignore-generated-files
```

## 财政贡献 <a id="financial-contributions"></a>

我们也欢迎[公开集体](https://opencollective.com/ccxt)完全透明地捐款。任何人都可以报销。如果费用对社区的发展有意义，那么核心贡献者将“合并”到我们的公开集体的分类帐中，并且将报销费用的人退还给您。

```text
ETH 0x26a3CB49578F07000575405a57888681249c35Fd（仅ETH！）比特币33RmVRfhK2WZVQR1R83h2e9yXoqRNDvJvaBCH 1GN9p233TvNcNQFthCgfiHUnj5JRKEc2ZeLTC LbT8mkAqQBphc4yxLXEDgYDfEax74et3bP
```

## 学分 <a id="credits"></a>

### 贡献者 <a id="contributors"></a>

感谢所有为ccxt做出贡献的人们！

### 支持者 <a id="backers"></a>

谢谢所有支持者！\[ [成为支持者](https://opencollective.com/ccxt#backer) \]

### 支持者 <a id="supporters"></a>

通过成为支持者来支持该项目。您的头像将显示在这里，并带有指向您网站的链接。

\[ [成为支持者](https://opencollective.com/ccxt#supporter) \]

### 赞助商 <a id="sponsors"></a>

感谢所有赞助商！（请要求您的公司通过[成为赞助商](https://opencollective.com/ccxt#sponsor)也支持此开源项目）

\[ [成为赞助商](https://opencollective.com/ccxt#sponsor) \]

