---
timezone: UTC+8
---

> 请在上边的 timezone 添加你的当地时区(UTC)，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区


# Calvin Sun

1. 自我介绍: 我來自中国，是一名前端开发工程师，目前在上海工作
2. 你认为你会完成本次残酷学习吗？   会
3. 你的联系方式（推荐 Telegram）  https://t.me/calvinsun_hk

## Notes

<!-- Content_START -->

### 2025.03.10

#### 以太坊的设计
想要明白以太坊的设计，我们就得了解下他的先驱还有文化。Unix的模块化对以太坊的影响很大，以太坊的模块化设计也是受到了Unix的影响。自由软件运动对以太坊的影响也很大，以太坊的智能合约就是受到了自由软件运动的影响。非对称加密开启了加密货币的时代，以太坊的智能合约也是受到了非对称加密的影响。

#### 以太坊协议的设计
以太坊从比特币，还有别的背景（上面有，比如Unix，自由软件行动等）出汲取灵感，这些在黄皮书中有。[执行规范](https://github.com/ethereum/execution-specs), 还有[共识规范](https://github.com/ethereum/consensus-specs)，目前都是用Python实现的。

#### 以太坊的实现与开发
一个以太坊客户端会实现共识层还有执行层，运行了这个客户端并且联网的，我们称之为节点。以太坊里面不限制开发语言。

#### 以太坊里面里面的测试

以太坊里面会有各种各样的改动，还有各种技术实现的客户端，所以需要各种各样的测试。有一些是在测试客户端，还有些是在模拟测试网络。

#### 协调
一般协调是由[PM repo](https://github.com/ethereum/pm)定期会议发起的，社区的idea还有proposal，是通过[EIP process](https://eips.ethereum.org/EIPS/eip-1)来协调的。

#### 额外的学习和练习
1. [以太坊解谜](https://ethereum.org/quizzes)
2. [Absolute Essentials of Ethereum](https://www.routledge.com/Absolute-Essentials-of-Ethereum/Dylan-Ennis/p/book/9781032334189)
3. [Mastering Ethereum](https://github.com/ethereumbook/ethereumbook)

#### 额外的笔记
质押：从2022年the merge开始，以太坊从PoW转向了PoS。质押是验证者为了保护网络，还有获得收益而采取的行动。验证者会锁定一定数量的ETH，然后运行一个全节点，然后验证交易。如果验证者诚实的去验证交易，那么他们就可以获得奖励。如果他们作恶，或者长期离线，那么他们就会被惩罚。

有了质押之后，以太坊就不需要像比特币那样需要大量的算力来保证网络安全了，这样也降低了能源的消耗，减少对环境的影响。

### 2025.03.11

#### 共识机制
共识机制是一整套由协议，激励和想法构成的体系。以太坊采用的是权益共识机制，以太坊的共识机制需要66%以上的节点的意见达成一致。

#### 权益证明
共识机制里面常见的由3中机制，比如比特币的Proof of Work，以太坊后期采用的Proof of Stake，以及Solana采用的另一种Proof of History。另外在以太链的私有链中还有Proof of Authority的实现，这个不是得需要中心化的权威节点？感觉不太符合区块链的去中心化的哲学哦。

权益证明的意思是，验证者以交押金（32以太币）为前提，来参与以太链的建设，比如验证新加入的区块是否是有效的，也可以创建新的区块。如果他们有不诚信的行为，比如把无效区块认为是有效区块，或者尝试欺诈，或者太懒惰啥也不干，那他交的押金就会被扣掉，甚至是斩首。

验证者需要运行三个客户端，执行客户端，共识客户端还有验证客户端。与之相对应的比特币链上的验证者只有一个客户端。这种设计反映了以太链的设计哲学，类似Unix的设计哲学，大的功能模块是由多个小的功能模块组合在一起完成的。

#### 私有链
相比于以太链这种大家都可以访问和参与的公有链，有些区块链是只有被批准的人才能参与，这些就称为私有链，通常应用于公司内部或者组织内部。

#### 拜占庭容错
Byzantine fault tolerance，描述了一个分布式系统，在面对部分节点故障或者恶意的时候，仍能保持运行并且达成共识的能力。

#### Beacon Chain
Beacon Chain是以太坊2.0引入的，他是新的共识层，也是在beacon chain里面，以太链引入了PoS来替代PoW。

### 2025.03.12
以太坊里面的节点指的是以太坊客户端的运行实例，每个节点都需要两个软件：执行客户端和共识客户端。

1. 共识客户端：实现PoS算法，让来自执行客户端的数据达成一致。
2. 执行客户端：监听网络中广播的交易，执行这些交易，然后保存当前以太坊的最新状态和数据库。

客户端可以用不同的技术栈实现，这个没有限制。

#### 跟踪网络中的节点

由于去中心化的特性，我们只能通过爬虫来获取这些节点的状态，而且不同爬虫获取的结果可能不一样。

#### 节点类型

节点有三种类型：全节点，轻节点和归档节点。

##### 全节点

现在一个全节点的大小大约500 ~ 700 GB。

1. 全节点会存储全部区块链数据（会定期清理，通常也只保留最近的大概128个区块的数据）
2. 参与区块验证
3. 为网络提供服务，并提供相关数据

##### 归档节点

归档节点保存了从创世区块到现在的所有数据，目前估计需要15 ~ 20 TB。

##### 轻节点

轻节点只下载区块头，当轻节点需要额外的信息的时候，它会向别的全节点请求这些数据。轻节点不参与共识。目前大多数客户端默认是以全节点或者裁剪节点来参与的。

#### 运行节点和替代方案

运行自己的节点可以让我私密的、安全的、自给自足的去使用以太坊。但运行节点需要一台高性能电脑，也需要大量磁盘空间。如果不运行自己的节点，也可以使用第三方供应商提供的服务。

#### 执行层同步模式

1. 完全同步。同步从创世区块以来的所有区块，并验证所有交易。具有最大的安全性
2. 快熟同步。类似完全同步，但不会重新处理历史交易。
3. 快照同步。只从最近一个已知的真实区块链一部分的受信任检查点开始同步，这个是默认策略，节省大量磁盘空间和网络带宽，同时不牺牲安全性。
4. 轻量同步。下载所有区块头和区块数据，然后进行一些随机验证。不支持权益证明以太坊。

#### 共识层同步模式

1. 乐观同步。合并后的同步策略。
2. 检查点同步。连接到远程服务，从最近的最终确认状态开始继续验证数据。

### 2025.03.13

#### 执行层测试
EVM(Ethereum Virtual Machine)测试：
1. 主要目的是验证每个执行客户端都遵守了规范，否者就没法达成共识，造成分叉。
2. 相同的输入，在不同的执行客户端里面应该得到相同的输出。

#### EVM 测试格式
1. 状态测试：基于相同的前置状态，合约，不同的客户端应该生成相同的结果，比如相同的后置状态，跟状态，改变的账户数据等。
2. 模糊测试和差分测试：输入大量合法、边界还有不合法的数据，不同的客户端应该生成相同的结果（正确结果）。
3. 区块链测试：主要是测试完整的区块相关逻辑
4. 区块链负面测试：主要是对于恶意节点，不能让他破坏区块链。

#### 共识层测试
相同的输入在不同的客户端上面也应该产出相同的结果

#### 跨链测试
简单来说就是从创世区块开始构建链到某个点，然后检查在执行层和共识层之间发生过的所有交互。

#### Hive
Hive是一个对以太坊客户端执行集成测试的系统。通用的CI基础设施以及对以太坊客户端的集成还有其他功能，使变得与其他测试系统很不一样

#### Devnets
有限的节点，用来验证idea以及硬分叉的早期阶段

#### 测试网络
Goerli testnent（已被废弃）
Sepolia testnet（2021.10.23上线）
Holesky testnet（2023.9.28上线）

#### 安全
##### 执行层面
要做有效性验证，还有无效性验证

##### 共识层面
故障节点和最终确认

* <33% 有可能会有丢失的插槽，但最终确认仍然会有
* 33% ~ 50% 最终确认会被延迟
* 50% ~ 66% 可能会影响分叉选择逻辑
* >66% 主链会受影响

#### Q&A
因为EVM的测试需要Gas，那Gas本身要是有bug咋办？后面我们会让测试不依赖Gas

### 2025.03.14

#### 以太坊的roadmap
主要是5个方面：
1. Merge。从 PoW 转向更节能的权益证明（PoS），通过beacon chain来实现。
2. Surge。聚焦于扩展网络容量，主要目标是通过分片技术（sharding）和其他扩容方案提升吞吐量。
3. Verge：目标是提升效率，比如简化验证，优化数据可用性和网络效率，减少数据冗余，提高节点运行效率。从Merkle tree换成了 Verkle tree。同时也支持Zero Knowledge。
4. Purge：致力于清理不必要的数据和状态，使网络更轻量化、运行更高效。
5. Splurge：作为最后的润色阶段，对整个系统做最后的优化和用户体验改进，确保网络在高负载下依然流畅稳定。

<!-- Content_END -->
