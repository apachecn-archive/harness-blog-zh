# Jenkins | Harness 的依赖和插件地狱

> 原文：<https://www.harness.io/blog/dependency-plugin-hell-jenkins>

詹金斯的外挂模式已经成为 CI/CD 的“拖鞋猫鸭”故事。情况不妙。

詹金斯的外挂模式已经成为 [CI/CD](https://harness.io/blog/what-is-ci-cd/) 的“拖鞋猫鸭”故事。这并不好——正如你所想象的，当有人觉得有必要把你的模型称为“依赖地狱”时。

你看过拖鞋猫的视频吗？你知道，就是拖鞋带着一只完整的活鸭子进他家，而他的主人惩罚他说，“拖鞋，你这只笨猫！你做了什么？！“如果你还没有，你应该[现在就看](https://www.youtube.com/watch?v=G3-sie5pNUE)然后再回来。去吧，我等着。

*You stupid cat.*

现在告诉我不是超级适用于詹金斯:*詹金斯，你这个愚蠢的工具！你是如何通过猫扑获得超过 1700 个插件的？！*

我将暂时放弃拖鞋的类比**，但是说实话，看看 Jenkins 插件索引不会让你有点紧张吗？随着[1788 个插件](https://plugins.jenkins.io/)目前可用，仔细阅读列表有点让人不知所措。当然，有大量的选择是很好的，但是有如此多的插件，很有可能很多已经失效或者被放弃了。**

**更糟糕的是，几乎所有这些插件都依赖于其他插件，这产生了依赖链——这是 Jenkins 插件模型的最大问题。詹金斯的依赖地狱足以让你重新思考你的整个 CI/CD 战略，我不会责怪你一点——因为，对我来说，这听起来像一大堆*不*。**

## **我们来谈谈插件**

**现在让我澄清一下:不，不是所有的插件都是不好的。Jenkins 插件“商店”上有一些非常棒的插件，它们非常有用，从长远来看，会为你节省大量的工时。另外，插件通常提供大量的可扩展性。但是当你看那 1788 个插件的列表时，其中有多少是实际可用的、维护良好的、没有依赖性的、没有安全漏洞的呢？**

**在你找到一个完全符合你要求的之前，你需要经历多少次呢？由于依赖链，除了你想要的插件，你还需要安装和维护多少其他插件？当所有这些依赖关系之间发生冲突时会发生什么？**

**最后，如果插件创建者决定停止维护它会怎样——你能承担这个任务吗，或者你需要找一个替代者(希望)做旧的那个？**

***“Your pain brings me joy,” says Devil Butler.***

## **欢迎来到依赖地狱！人口:你。**

**鲜为人知的事实:第七层地狱也被称为詹金斯附属地狱。**

**依赖关系就像它们听起来的那样:你安装/升级了一个插件，现在必须安装/升级 5-6 个其他插件以确保第一个插件正常工作——通常，那些插件是你根本不用的东西；它们只是你的原始插件所需要的。**

**我能找到的最好/最差的依赖例子是[蓝海](https://plugins.jenkins.io/blueocean/#dependencies)——看看那个依赖列表。这只是为了一个漂亮的用户界面！不难相信，但是他们之前已经被要求提供荒谬的依赖。**

#### **情况变得更糟了...**

**说到依赖，事情会变得*非常*复杂，*非常*迅速。你拥有的插件越多，更新时就越有可能出现问题——其中一个问题就是**版本依赖**。**

**假设你安装了插件 A 和插件 B。插件 A 目前的版本是 2.4，但是要兼容插件 B，你得用 1.8 版本。理论上，这不是一个大问题——但实际上，如果插件 A 的 1.8 版本与你想安装的新插件 C 不兼容怎么办？简而言之:这破坏了工作。**

***Pictures are worth a thousand words.***

**像这样的情况使得你**不能在你的插件上启用自动更新**。在这种情况下，您现在需要脑力劳动来跟踪哪些插件需要保持当前版本，哪些可以更新。由于大多数人不想在这上面浪费精力，他们会干脆停止更新插件，这会带来漏洞的风险。**

#### **更糟的是...**

**如果这还不够，用户有时会遇到另一种情况:一个插件可能有一个版本中的**漏洞的报告，但是依赖它的插件还没有更新。你的选择是要么接受安全风险，要么切断与插件的联系——这可能会导致下游影响。更复杂的是，**某些插件只与 Jenkins 的某些版本兼容**。****

**最后，还有向后兼容性的问题。[一位用户](http://jenkins-ci.361315.n4.nabble.com/Third-party-dependencies-APIs-and-Jenkins-Proposals-td4978928.html)分享了他对库依赖的体验:“ *[...]简单地在 Jenkins 中包含这些常见的依赖关系本身会导致一些问题，比如如果它稍微破坏了向后兼容性，就再也不能升级那个库了。这是一个很容易被忽视的问题，直到出现问题——看看用户提出的四个解决方案，没有一个看起来简单或直观。***

## **正如我们常说的:解雇你的管家。**

**几年前，Jenkins 做了其他 CI/CD 平台做不到的事情。它曾有过辉煌的一天。但是现在，管理和维护插件、依赖项，尤其是当需要数百个脚本时，是如此的痛苦，以至于不再值得。尤其是当有一些非常好的平台时，所有的可扩展性都是内置的。**

**例如，我们可以自吹自擂，大声而自豪地宣称 Harness 只有 150 个插件——而且没有**依赖项！你没看错，**插件之间没有依赖关系**！每个插件都作为一个自包含的 Docker 容器执行，其中运行的总是最新版本。你从不下载插件或者以任何方式维护它们——除非你*希望*为开源做出贡献。为什么不获得一个让生活更轻松的 [CI/CD 平台](https://harness.io/blog/what-is-cicd-platform-why-should-i-care/)的[免费试用版](https://app.harness.io/auth/#/signup/)？不要成为组织的拖鞋:对依赖和插件地狱说不。****