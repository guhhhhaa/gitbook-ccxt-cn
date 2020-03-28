# 常问问题

## Frequently Asked Questions

## 经常被问到的问题

### I'm trying to run the code, but it's not working, how do I fix it?

### 我试图运行代码，但它不工作，我该如何解决？

If your question is formulated in a short manner like the above, we won't help. We don't teach programming. If you're unable to read and understand the [Manual](https://github.com/ccxt/ccxt/wiki) or you can't follow the guides from the [CONTRIBUTING](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md) doc on how to report an issue, we won't help either. Read the Manual. You should not risk money and time without reading the entire Manual very carefully. Namely, when asking a question:  
如果你的问题是像上述那样简短的话，我们将无法提供帮忙。我们不教授编程。如果您无法阅读并理解[ 本手册 ](https://github.com/ccxt/ccxt/wiki)，或者没有依照[贡献](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md)文档中关于如何反馈问题的指南，我们也无法提供帮助。请首先阅读手册。在没有仔细阅读整手册的情况下，您不应该冒险地投入金钱和时间。换句话说，在提出一个问题（ Issue ）前：  

* Use the search button for duplicates first!
* 首先使用搜索按钮查看是否有重复项 / 已提出的类似Issue。
* **Post your output in verbose mode!** It's written and mentioned everywhere, in the [Troubleshooting](https://github.com/ccxt/ccxt/wiki/Manual#troubleshooting) section, in the [README](https://github.com/ccxt/ccxt/blob/master/README.md) and in many answers to similar questions among [previous issues](https://github.com/ccxt/ccxt/issues) and [pull requests](https://github.com/ccxt/ccxt/pulls).
* **以详细模式提交您的输出**！它在每个地方都有写入和提及，在[故障排除](https://github.com/ccxt/ccxt/wiki/Manual#troubleshooting)部分，[README](https://github.com/ccxt/ccxt/blob/master/README.md)文件中，以及对许多以前的 [issues](https://github.com/ccxt/ccxt/issues) 和 [pull requests](https://github.com/ccxt/ccxt/pulls) 中类似问题的诸多回复。
* Post your code to reproduce the problem. Make it a complete short runnable program, don't swallow the lines and make it as compact as you can \(5-10 lines of code\), including the instantation code.
* 发布您的代码好让我们重现问题。使它成为一个较短的完整的可运行程序，不要删除必要的代码，并尽可能地紧凑（5-10行代码），包括实例化代码。
* Post your version number of ccxt
* 请贴出您使用的 CCXT 版本号
* Post your language version number, how do you think we can guess it otherwise?
* 贴出您使用的语言版本号，您该不会认为我们能猜出来吧？

### I am calling a method and I get an error, what am I doing wrong?

### 我正在调用一个方法，并且出现错误，我做错了什么？

You're not reporting the issue properly \) Please, help the community to help you \) Read this and follow the steps: [https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md\#how-to-submit-an-issue](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#how-to-submit-an-issue)  
您没有以正确的方式反馈问题，请阅读本文并按照以下步骤操作，以便社区能够提供帮助： [https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md\#how-to-submit-an-issue](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#how-to-submit-an-issue)

### Can you implement feature `foo` in exchange `bar`?

### 你们可以实现某交易所的某种特性 / 方法吗？

Yes, we can. And we will, if nobody else does that before us. There's very little point in asking this type of questions, because the answer is always positive. When someone asks if we can do this or that, the question is not about our abilities, it all boils down to time and management needed for implementing all accumulated feature requests. Moreover, this is an open-source library which is a work in progress. This means, that this project is intended to be developed by the community of users, who are using it. All contributions are welcome! What you're asking is not whether we can or cannot implement it, in fact you're actually telling us to go do that particular task and this is not how we see a voluntary collaboration.  
是的，可以实现。如果没有其他人在我们之前完成这个特性，我们会完成它。询问这种问题几乎没有意义，因为答复往往是肯定的。当有人问我们是否可以做到这样或者那样，症结不在于我们的能力，而在于实现所有累积的特性请求所需的时间和管理工作。 另外，这是一个还处于开发中的开源项目。这意味着，该项目旨在由正在使用它的社区用户进行开发，我们欢迎任何贡献！你所问的不是我们是否能够实现它，事实上你是在具体的告诉我们要去做某个特定的任务，这不是我们希望看到的志愿协作方式。

### When will you add feature `foo` for exchange `bar` ? What's the estimated time? When should we expect this?

### 你们什么时候可以为某交易所添加某种特性 / 方法？预计什么时候？我们什么时候可以看到它？

We don't give promises or estimates on the open-source work. The reasoning behind this is explained in the previous paragraph.  
我们没有对本开源工作做出承诺或预估。上一段落解释了这背后的原因。

### What's your progress on adding the feature `foo` that was requested earlier? How do you do implementing exchange `bar`?

### 之前提出的添加某种功能的进展如何？打算如何实现某交易所？

This type of questions is usually a waste of time, because answering it usually requires too much time for context-switching, and it often takes more time to answer this question, than to actually satisfy the request with code for a new feature or a new exchange. The progress of this open-source project is also open, so, whenever you're wondering how it is doing, take a look into commit history.     回答这种问题通常是浪费时间，因为这通常需要太多的时间来进行上下文切换，并且回答一个这种问题通常需要比实际完成这个新特性 / 新交易所的代码花费更多的时间。这个开源项目的进展也是公开的，每当你想知道它进展到什么地步了，看一看 commit 历史。

### 您何时将添加对“问题”中要求的交易所的支持？

同样，由于上述原因，我们无法保证添加该交易所或该交易所的日期。答案将始终保持不变：_我们将尽快_。

### 您在添加先前请求的功能方面取得了什么进展？您如何实现交流？`foobar`

这种类型的问题通常是浪费时间，因为回答问题通常需要太多时间来进行上下文切换，并且与使用新功能或新代码来实际满足请求相比，回答此问题通常需要更多时间交换。这个开源项目的进度也是开放的，因此，每当您想知道它的状态时，请查看提交历史。

### 该PR的状态如何？任何更新？

如果未合并，则表示PR包含错误，应首先修复。如果可以原样合并–我们将合并它，而您根本不会问这个问题。不合并PR的最常见原因是违反任何[CONTRIBUTING准则](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#derived-exchange-classes)。这些准则应按字面理解，如果您希望快速合并PR，则不能从那里跳过一行或一个单词。不违反准则的代码贡献几乎会立即合并（通常在几个小时之内）。

### 您能否指出错误，或者我应该在PR中进行哪些编辑以使其合并到master分支中？

不幸的是，我们并非总是有时间快速列出阻止合并的代码中的每个错误。通常，更正和解决错误而不是说明应该采取的纠正措施更加容易和快捷。其中的大多数内容已在“ [贡献准则”中](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#derived-exchange-classes)进行了概述。经验法则是**从字面上**遵循**所有准则**。

### 嘿! 您上传的修复程序是用JS编写的，请问您也可以修复Python / PHP吗？

我们的构建系统会自动为我们生成特定于交易所的Python和PHP代码，因此它是从JS编译而来的，无需一一修复所有语言。因此，如果在JS中修复，则在Python pip和PHP Composer中也修复。自动构建通常需要5-10分钟。只要在新版本到来时或在新版本到来之后升级您的版本，就可以了。更多关于它在这里：`pipcomposer`[https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md\#multilanguage-support](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#multilanguage-support)

