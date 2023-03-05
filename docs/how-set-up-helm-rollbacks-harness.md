# 如何在线束|线束中设置舵回卷

> 原文：<https://www.harness.io/blog/how-set-up-helm-rollbacks-harness>

让我们为 Helm 部署建立一个管道，并创建一个回滚来启动和恢复以前的版本。

现代软件交付系统是复杂而庞大的，当它们失败时，它们可以摧毁整个公司的运营能力。为了防止不可预见的停机，系统设计有内置的故障策略，如回滚。回滚是指系统自动恢复到先前的已知健康状态。这种逆转可以防止系统在中断状态下继续运行并造成进一步的损害。

在本帖中，我们将使用 Harness 来创建舵图的部署管道。Helm 是 Kubernetes 的一个包管理器，允许您在 Kubernetes 环境中灵活地打包和部署应用程序。在这个例子中，我们将使用 Nginx 作为我们的舵图。我们将设置管道，以便它运行一个 Helm 部署，如果出现问题，回滚将启动并恢复以前的版本。

## 为什么需要失败策略？

组织有责任迎合他们的客户，并为他们的产品和服务提供正常运行时间。无论你是一名软件工程师还是客户成功的工作人员，交付一个工作产品的责任都落在你的肩上。即使对于最有经验的工程师来说，也不可能预测到每一种情况，并建立一个能够承受所有可能故障的健壮系统。

故障策略旨在将故障的影响降至最低，并保持系统始终运行。失败策略应该自动化，因为依靠人类及时执行策略是不可行的。人类永远不会像计算机一样快，在某些情况下，人们不可能及时干预以防止故障发生。此外，它可以帮助建立对组织管理失败能力的信任和信心。

## 什么是回滚？

部署回滚是撤消部署的过程。这可能是由于各种原因造成的，例如遇到了需要用新部署进行修复的意外问题，或者当需要恢复原始部署时。

例如，假设一个软件更新破坏了您生产环境中的某些东西。回滚是指恢复到软件先前版本的过程，该版本按预期运行。

## 设置线束连续部署管道

线束管线将包含以下零件:

1.  **服务**–利用服务从逻辑上代表您的微服务/应用。您可以根据需要将同一服务传播到任意多个阶段。[了解更多](https://docs.harness.io/article/hv2758ro4e)
2.  **环境**–环境代表您的部署环境(QA、Prod 等)，包含列出您的目标集群、主机、名称空间等的基础架构定义。
3.  **执行**–执行是指在需要或出现故障时，如何调配和管理您的应用和基础架构的指令。
4.  **连接器**–连接器帮助您连接到您的 SCMs (GitHub、GitLab 等。)、秘密管理器、日志工具、云、票务系统和跟踪系统。

该演示将只关注执行部分，并详细探索其他部分。你可以阅读下面关于【Helm 入门的帖子。

## 创建项目

Harness 支持本地掌舵服务，您可以利用该服务在管道中使用掌舵图表。使用本地 Helm 服务设置舞台，如下所示:

## 流水线执行

要设置服务，请在克隆之后使用存储库后面的[，因为您将需要在横向阶段编辑文件。](https://github.com/harness-community/helm-samples)

1.  清单名称–为您添加一个名称以引用您的清单
2.  Git 提取类型–定义如何提取图表
3.  分支–定义图表所在的分支
4.  图表路径–这是您的图表的根目录
5.  Helm 版本–这是 Helm 的版本，在本教程中，您将使用 Helm V3
6.  values . YAML–添加将覆盖默认值的文件

转到执行阶段，并确保您已经配置了舵部署。接下来，保存要执行的管道。

运行管道后，成功的执行如下所示:

## 回滚执行

Harness 提供了回滚策略。对于 Helm 部署，您应该使用类似的回滚策略。要实施，点击右上角的“回滚”。

点击添加一个步骤，并从步骤库中选择舵回滚。

将 Helm Rollback 添加到您的步骤之后，您就可以使用失败策略处理管道执行了。

## 测试故障策略

回滚的工作方式是返回到以前的版本。例如，如果您有一个单元，并将其扩展到两个，当检测到故障时，它可以再次回到一个单元。通常，不使用 pod，而是使用新图像。为简单起见，您可以将 pod 视为通过您的终端进行调查的可视数据。

打开您的终端并使用“ku bectl get pods–watch ”,同时确保您位于您在服务中定义的名称空间上。

下一步是编辑 values.yaml 文件，使您的副本计数为 2。

部署后，您的集群将有两个单元。然后，我们希望注入一个失败，这样我们就可以看到回滚在起作用。

### 注入失败

回到你的执行阶段，再加一个步骤。

选择“Shell 脚本”步骤。

用一个带有“exit 1”的脚本来配置它，这样就有一个强制退出。应用更改。

新步骤如下所示:

保存，运行您的管道，并观察您的终端。您将看到您的副本增加到两个，然后在到达退出步骤时恢复为一个。当退出步骤失败时，就会触发回滚步骤。

执行流程如下:

恭喜你！您已经成功实现了回滚。

## **接下来的步骤**

现在您的集群已经可以运行了，您可以使用 kubectl 实用程序向它添加资源。查看我们的[在 5 分钟内开始部署，采用委托优先的方法](https://www.harness.io/technical-blog/deploy-in-5-minutes-with-a-delegate-first-approach)教程来安装委托，并继续创建您的 CI/CD 管道。

## 了解 Harness 如何管理回滚

[免费开始](https://app.harness.io/auth/#/signup/?module=cd)线束连续交付。

欢迎在 [community.harness.io](https://community.harness.io/c/harness/7) 或[提出问题，加入社区 slack](https://join.slack.com/t/harnesscommunity/shared_invite/zt-y4hdqh7p-RVuEQyIl5Hcx4Ck8VCvzBw) 与我们的工程师在特定于产品的渠道中聊天，如: