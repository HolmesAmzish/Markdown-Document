# 通过区块链增强物联网部署中的SDN安全性

**摘要**

在我们这个日益一体化和互联的世界中，商业活动主要发生在基于跨越国界、地理区域和司法边界的云计算基础设施的网络中。这种高效的实体互联得益于一种新兴的网络范式——软件定义网络（SDN）。SDN旨在极大简化策略执行和网络配置的动态调整。然而，尽管这种新型网络范式带来了显著的优势，但与传统网络部署相比，它的攻击面更大，特别是当应用于安全关键的场景时，这一点引起了人们的质疑。尤其是在SDN用于支持物联网（IoT）相关的网络元素时，由于这种部署对特定攻击类型的高度脆弱性以及物联网应用所需的跨云通信，额外的安全问题随之而来。联网节点的总数量使得所有实体的高效监控成为一项巨大的挑战，必须加以解决以防止系统性能下降和服务中断。本文概述了SDN与物联网云连接时的常见安全问题，介绍了区块链这一新兴范式的设计原则，并阐述了区块链在SDN和物联网应用中作为显著安全因素的理由。

​	关键词：云，虚拟化，SDN，物联网，区块链。

---

## 一、引言

在当今一体化和互联的世界中，大多数在线活动发生在基于云计算基础设施的商业网络中，这些网络通常跨越国家、地理和司法边界。它们通常通过专用接口连接，设计目标是为所有互联实体提供最高程度的灵活性、可扩展性、扩展性和安全性。这种高效的实体互联是通过一种新兴的网络范式——软件定义网络（SDN）实现的。SDN旨在打破传统网络的垂直整合，通过将核心网络控制逻辑与底层路由和交换设备分离，并希望创建一个逻辑上集中的控制器，以进一步简化策略执行和动态网络重配置。在SDN中，网络元素仅根据预定义的策略充当数据包转发器，这些策略由单独的控制器创建或修改，然后推送到网络的边缘。这种方式极大地帮助了网络提供商以集中的方式动态调整网络配置，无需单独访问和重新配置分散在整个网络中的设备。通过这种方式，网络升级以及必要的调整可以在几分钟内完成，从而以接近实时的方式解决潜在问题。

SDN提供的快速更改网络配置的能力对全球拥有数千个数据中心的大规模云计算部署的运营商来说具有颠覆性。然而，尽管这种新型网络范式带来了明显的优势，但仍存在一些问题，阻碍了它对传统解决方案的全面统治。SDN的一个主要缺点是与传统网络部署相比，其攻击面更大，一旦控制器被攻破，成功攻击的影响将大大增加。正如文献所指出的，SDN带来了一个有趣的两难困境：它到底是一种可取的网络架构演进，还是一种危险的攻击面扩展？有人可能会争辩说，可以通过仔细确保后者的安全来保留前者的好处，但正如我们将在本文中所展示的，当新的有趣应用和垂直领域（如物联网）出现时，有必要退一步，从整体上彻底解决安全问题。

本文的其余部分组织如下：第二部分指出SDN网络的主要安全挑战；第三部分描述了物联网范式引入的额外安全考虑；第四部分介绍了区块链的基本要素及其如何通过一个整体案例来增强网络安全性；最后，本文的第五部分总结了本文的内容并讨论了未来的研究和实施步骤。

---

## 二、SDN的安全挑战

SDN的设计原则要求这样的网络完全由软件控制，并确保一个专用节点（控制器）中存在中央网络智能。

### A. 应用层

由于大多数网络功能可以作为SDN应用程序实现或被SDN应用程序使用，潜在的恶意软件执行可能对网络各层的拓扑结构造成严重破坏。软件开发缺乏标准和指南也可能导致安全策略冲突，甚至固有的互操作性限制，因为许多参与者，从网络提供商到第三方人员，可能同时在相同的SDN控制基础设施中工作。应用层的主要安全挑战如下所示：

1. **未经授权/未认证的访问控制**：SDN的管理站、设计不良的第三方应用程序及所有互联的SDN实体都容易受到各种类型的攻击，这些攻击旨在访问其核心功能，从而能够破坏SDN控制器并对网络造成最大程度的破坏。像暴力攻击等攻击在传统网络部署中存在，而在SDN中，这些攻击由于所有SDN应用程序都具有访问控制器和直接访问网络资源与配置机制的特权而变得更加严重。SDN网络可以很容易地从单一位置重新编程，任何安全漏洞都被认为是潜在的危险。
2. **不当的网络规则插入**：一旦恶意应用程序部署或合法应用程序被破坏，它可能会开始生成流量，阻止正确的信号传输和数据包传递，或尝试强制执行错误的流规则，最初针对相邻节点，但迟早会波及整个SDN网络。

### B. 控制平面

强化SDN控制平面以防范潜在威胁被认为是防止攻击者完全控制核心网络基础设施的决定性策略。例如，设计不当或恶意的软件可能成为一个潜在的安全漏洞，允许重新编程控制器、路由器或交换机，生成不当的流量，甚至因转发表的破坏导致网络连接中断。控制层中最常见的攻击形式如下所示：

1. **拒绝服务（DoS）攻击**：由于SDN通过设计引入了控制平面与数据平面的分离，拒绝服务（DoS）和分布式拒绝服务（DDoS）攻击对SDN控制器来说非常具有威胁性。攻击者可以利用这两个平面之间的通信通道，插入伪造或虚假的流量，使控制器或其他网络实体需要采取额外的行动，从而使它们无法为合法用户提供服务。例如，攻击者可能会通过网络扫描仪操纵流量响应时间以识别底层SDN节点。一旦发现SDN网络，攻击者会通过数据路径向控制器传输特殊格式的流请求，增加数据路径中的流量数量，导致控制器的流设置请求急剧增加，最终导致服务中断。DoS攻击还可以通过持续发送带有随机头部的IP数据包，使控制器进入无响应状态，或通过信号洪泛攻击资源有限的网络节点，从而使整个网络瘫痪。
2. **SDN控制器攻击**：这是SDN网络时代的典型攻击类型，因为在传统网络中，并不存在这样一个关键节点，而一旦该节点受到攻击，所有互联的节点都可能面临威胁。由于第三方被允许在控制器上部署应用程序，缺陷或恶意应用程序可能会重新配置整个网络，因为控制器仅提供抽象层，将这些抽象层翻译成对底层基础设施的配置命令。应对这种攻击的对策包括：使用复制技术来检测、移除或隔离异常行为，增强组件多样性以消除单点故障的可能性，以及采用机制定期将系统恢复到稳定可靠的状态。

### C. 数据平面

数据平面和控制平面的分离简化了所有转发设备（如路由器）的结构，它们现在只需要通过专用接口来进行远程操作。尽管这种分离提高了灵活性，但数据平面依然存在一些需要有效应对的安全问题。最常见的数据平面攻击包括：

1. **伪造的交换机流规则和洪泛攻击**：在OpenFlow网络中，控制器与网络交换机相连，并将流规则安装到专用表中。这些规则可以预先安装，或者在主机发送初始数据包时动态安装。然而，交换机只包含有限的流表存储空间，使它们易受伪造流规则的攻击。攻击者可能会试图利用交换机的有限缓冲区，使其陷入饱和状态。
2. **TLS和TCP相关问题**：由于传输层安全协议（TLS）配置的复杂性，OpenFlow的最近版本中已经将其设置为可选项。这使得交换机在传输层面临更大的安全风险，特别是可能暴露于中间人攻击中。

------

## 三、物联网中的安全考虑

物联网（IoT）是近年来获得显著发展的新兴范式。它依赖于一种无处不在的网络，这种网络将大量分布广泛、差异巨大的设备无缝连接在一起。尽管物联网在诸多领域展现出了巨大的应用潜力，但它也引入了许多新的安全风险和挑战。以下是物联网相关部署中的主要安全考虑：

1. 保护资源受限且无人值守的设备
大多数物联网节点是无人值守的，且物理上分布广泛，容易受到物理攻击。而当前的云计算基础设施中的网络安全解决方案无法直接应用于此类设备。由于这些节点通常为执行特定任务而设计，其计算能力和资源有限，难以为自身提供足够的安全保护。因此，如何在物联网设备的整个生命周期中保护其免受攻击是一个未解的基本问题。

2. 可信的安全状态评估
物联网旨在支持大规模分布式系统。例如，一个智能城市可能在其范围内部署数千个设备，并将其分类为多个子系统用于监控、数据收集和内容聚合。对于此类系统，必须确保能够可信地评估这些设备是否正常运行。然而，由于物联网节点的数量庞大和资源限制，现有的安全状态评估方法在实际应用中会遇到复杂的管理问题和高昂的成本。

3. 对安全漏洞的适当响应
当前的事件响应机制通常依赖于停止系统运行并回滚软件到安全状态。然而，这种方法在关键任务系统中（如智能交通、工业控制系统等）是不可接受的。因此，物联网需要一种更加容错且不会中断系统运行的响应机制。

------

## 四、区块链

区块链作为一种分布式的、防篡改的数据结构，能够为物联网和SDN的安全提供一种新的解决方案。区块链将所有节点生成的交易数据存储在一个分布式账本中，允许所有参与方实时验证数据的完整性和真实性。

区块链的分布式特点使其非常适合物联网中大量分散节点的场景。通过引入区块链，物联网设备的安全性可以得到极大的增强。每个设备可以将其生成的数据记录在区块链中，任何节点都可以通过验证区块链的最新记录来确保数据的真实性。

------

## 五、结论

SDN是全球云部署的网络骨干，尽管它通过控制和转发平面的物理分离极大地改变了网络架构，但仍然存在一些安全问题。随着物联网的崛起和5G网络时代的到来，通过区块链技术提升SDN与物联网的安全性是一个有效的解决方案。