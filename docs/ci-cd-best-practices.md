# 开发运维团队的 CI/CD 最佳实践|管理

> 原文：<https://www.harness.io/blog/ci-cd-best-practices>

7 供您的团队考虑的 CI/CD 最佳实践，以及与构建 CI/CD 管道相关的常见陷阱。

DevOps 是团队如何与人员、流程和技术合作，向他们的消费者交付价值。在 DevOps 生命周期中，团队不仅仅关注于发布他们的可交付成果，相反，为了在 DevOps 中取得成功，团队需要以快速、安全和可重复的方式交付价值。[持续集成](https://harness.io/blog/what-is-continuous-integration/)和[持续交付](https://harness.io/blog/what-is-continuous-delivery/) (CI/CD)通过为软件交付过程提供自动化、治理、长寿和安全来帮助跨职能团队履行他们的职责。这篇博文将在 DevOps 实践的背景下讨论 [CI/CD](https://harness.io/blog/what-is-ci-cd/) ，并分享为您的 DevOps 团队实施的最佳 CI/CD 实践。

## CI/CD 和 DevOps 的历史

在 21 世纪，由于技术的进步和采用，敏捷原则和实践在不同的软件开发组织中流行起来。敏捷思维降低了开发新应用程序功能所需的时间，鼓励开发团队尽早并经常发布。然而，由于部署到生产环境仍然需要几周或几个月的时间，因此某些灾难性的结果仍然存在。

到 2010 年，云的引入允许组织和团队快速开发他们的应用程序，并在几小时或几分钟内将版本部署到生产中。DevOps 的出现是为了让组织将这一过程常规化和低风险化。

如今，组织正在采用 [DevOps 原则和实践](https://harness.io/blog/ci-cd-best-practices/)来每天多次部署他们的变更。竞争优势取决于快速上市和创新，而 DevOps 的核心是 CI/CD。

## 7 开发运维团队的 CI/CD 最佳实践

这里有 7 个 CI/CD 最佳实践供您的团队考虑，以及与构建 CI/CD 管道相关的常见陷阱。

### **#1。失败更快更便宜**

使用瀑布方法交付的组织努力满足不断变化的环境和期望。管道中的快速失败类似于借用敏捷和精益方法，这通常是软件开发团队中事实上的思维模式。我们希望做的是转移交付软件过程中留下的责任和活动。例如，您可能希望引入开发人员环境，以允许早期测试，而不是在开发团队做出更改后的几周或几个月，在部署过程中在环境中进行测试。“左移”心态赋予开发人员能力和工具，让他们在不破坏东西的情况下快速移动。

[CI 管道](https://harness.io/blog/what-is-continuous-integration/)的主要目的是自动化构建过程。您的构建过程应该包括版本控制和问题跟踪。它还应该集成和运行单元测试，这样对于不满足功能需求的代码构建就会失败。CI 中的一个常见缺陷是没有足够的单元测试或代码覆盖率。这可能导致构建通过了 CI 管道，但是在软件交付过程中进一步失败。

在 [CI/CD 管道](https://harness.io/blog/ci-cd-pipeline/)中更快地失败在成本和工作量方面是有益的，因为端到端(E2E)测试是昂贵的，难以调试，并且可能需要在基础设施上运行多个服务。大多数产品团队更愿意在问题到达客户手中之前发现它。将一套健康的单元测试集成到您的 CI 管道中，允许团队在较低的环境中快速失败，并避免频繁的生产事故。

使用瀑布方法交付的组织努力满足不断变化的环境和期望。采用快速失败的心态是 CI/CD 管道成功的一个好方法。

### **#2。每日提交**

软件团队应该尽早地将他们的代码集成到他们代码仓库的主要分支中。随着开发人员在功能开发上的进展，这防止了功能和主要分支的维护混乱。即使特性开发仍然是一项进行中的工作，这项工作对于任何最终用户或者主分支的测试人员来说仍然是不可见的。如果您在最小化合并冲突和分支方面有问题，我推荐您看看[渐进式交付](https://harness.io/blog/progressive-delivery/)技术，比如特性标志管理，它可以帮助您实现交付管道。

### **#3。修复损坏的构建**

第三个实践涉及修复代码的不完整版本。持续集成假设您的软件开发团队正在已知的稳定版本的代码上进行开发。如果您的团队正在努力保持您的应用程序代码稳定和良好的测试，我建议确保您的构建和测试过程对您的开发团队是可用的和可见的。

理想情况下，每个版本的代码只由 CI 管道构建一次，这样就可以很容易地跟踪和理解失败和相应的代码更改。按需构建并与其他应用程序活动隔离的干净的测试环境也是 CI/CD 管道可以保证的有用的实施。构建 CI/CD 管道来提供和控制质量保证(QA)或测试环境，对于希望高质量和高速度交付的软件开发和 QA 团队来说是非常有益的。

### **#4。持续自动化交付生命周期**

每个组织都有一个创建和交付代码的过程。由于新技术、团队或流程的出现，这一流程可能会随着时间的推移而改变。一个重要的实践是不断地评估哪些过程和测试需要被集成或者自动化到 CI/CD 管道中。

连续交付(CD)管道是我们软件交付生命周期(SDLC)的反映。典型的交付职责包括供应基础架构、部署应用程序、批准部署变更、质量保证/测试和监控。并非所有这些职责和能力都包含在您的 CI/CD 管道的第一次迭代中。

没有一个模板化的 CI/CD 管道来管理所有的部署场景，因此在许多情况下，通常有许多 CI/CD 管道来支持基于应用程序架构设计的不同类型的部署。例如，您用来部署[整体应用](https://en.wikipedia.org/wiki/Monolithic_application)的 CI/CD 管道可能不同于一组或一组微服务。

我建议投资于[价值流映射](https://harness.io/blog/value-stream-mapping-guide/)或基于度量的过程映射练习，以将关键的软件交付利益相关者与新的或复杂的软件计划或服务联系起来。这些练习通常有助于形成 DevOps 之旅和 CI/CD 成熟流程。

### **#5。定义发布和回滚策略**

第五个实践是定义一个发布和回滚策略。软件发布是软件向消费者的分发。每当我们发布软件时，我们都会引入漏洞、问题、错误和非性能软件的风险。回滚部署或生成修补程序可能有许多原因。定义适合您的 CD 流程的发布策略，以降低部署风险。

基础设施即代码或 [GitOps](https://harness.io/blog/what-is-gitops/) 帮助团队供应、配置和管理基础设施资源。回滚策略倾向于镜像发布策略。在部署新实例时，是否决定保持应用程序的当前版本运行取决于您。只要确保您有一个解决任何停机和数据丢失的工作流程。

还值得将您的指标、监控和警报解决方案集成到您的 CI/CD 管道中，以实施您的部署。就像我们如何在 CI/CD 管道的早期阶段利用单元测试一样，确保部署后的质量非常重要。数据驱动的持续交付允许我们提高我们的交付能力，并放大反馈以鼓励开发运维团队的持续改进。

### **#6。采取安全第一的方法**

关于 CI/CD 管道的一个常见误解是，它们的唯一目的是允许您的软件更改可用。持续部署允许组织按需将他们的更改部署到生产环境中。CI/CD 实践侧重于我们如何持续实现这一成果。因此，应该鼓励和激励许多 DevOps 团队利用平台和解决方案现在提供的 CI/CD 管道功能。

基于角色的访问控制(或称 [RBAC](https://harness.io/blog/rbac/) )限制系统中的用户访问。一个很好的想法是，每个用户应该只拥有足够的权限来履行他们必要的职责。这些用户组可以基于角色或组织结构(如团队)来定义。CI/CD 平台中的访问控制的一个例子是为特定的管道或部署资源创建读取和执行权限。

CI/CD 管道的一些安全功能还可能涉及利用机密管理来确保敏感的部署或环境信息得到正确存储和保护，或者引入漏洞扫描。

DevSecOps 实践适用于 CI/CD 管道。DevSecOps 是 development，security，and operations 的缩写，它是组织在其有价值的可交付成果中交付和做出安全决策和行动的方式。请记住，安全自动化是 DevSecOps 的核心原则。

启用 DevSecOps 的一个很好的方法是通过您的持续集成和持续交付(CI/CD)管道。如果您的团队能够持续地将安全性集成到软件开发生命周期中，这是一种很好的思维方式和工作方式，这样安全性就处于我们的团队交付商业价值的最前沿。

### **#7。放大反馈**

可靠性是每个人的责任，但有时这种说法会让人觉得它与创新和快速交付功能不一致。站点可靠性工程(SRE)是去年的热门话题，因为围绕这个角色的指南越来越多，越来越多的人开始扮演这个角色。 [SRE 实践](https://harness.io/blog/sre-vs-devops/)帮助我们实现可靠交付。即使您没有 SRE 团队或个人，您仍然可以利用这些帮助您改进软件交付过程的实践。

要采用的一个主要做法是放大反馈。通常，软件交付或软件开发问题是由反模式和实践引起的症状。在回顾之后确定具体的结果有助于改善和减轻与事件、错误和缺陷相关的棘手问题。一些事件是由已知的错误或缺陷引起的，因此即使是设置错误或事件错误也有助于更好的软件交付。鉴于应用程序性能不佳或事故频发的历史，冻结或锁定生产部署是很常见的。

如果你正在寻找一个解决方案来帮助促进在线回顾和团队协作，像谷歌的 [Jamboard](https://jamboard.google.com/) 或 [Miro](https://miro.com/) 这样的解决方案很好。

建造 CI/CD 管道的困难

如今，工程师可以利用许多解决方案来创建 CI/CD 管道。然而，随着当今不断变化的云和容器原生生态系统，软件交付解决方案需要快速、轻松地随着组织和团队推进其软件交付能力而扩展。并非每个体系结构解决方案都旨在随您而扩展。建造 CI/CD 管道的一些常见困难包括:

*   部署脚本的创建和管理
*   缺乏自助服务交付能力
*   插件的升级、配置和管理
*   平台稳定性和可扩展性

考虑一下 [CI/CD 挑战](https://harness.io/blog/ci-cd-challenges/)以及随着应用程序工作负载水平和垂直扩展，这对支持您的组织意味着什么。

## 利用 Harness 自动化构建和测试过程

CI/CD 管道定义并自动化了我们的开发运维生命周期。它确定了软件何时、何地以及如何到达客户手中。这篇文章关注的是作为一个 DevOps 团队建立适当的 CI/CD 管道的重要性，但是如果你想了解更多关于 CI/CD 的信息，请查看我们今天关于 [CI/CD 挑战](https://harness.io/blog/ci-cd-challenges/)的文章。