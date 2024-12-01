# System-Papers-Reading-Lists
阅读论文的笔记，大体上是系统，存储，数据库，分布式等方向的。
## Basic
### [Paxos Made Simple](https://www.scs.stanford.edu/20sp-cs244b/sched/readings/paxos_made_simple.pdf)
- 作者本人对Paxos算法的简要说明。看完以后感觉还是云里雾里的。

### [Socrates: The New SQL Server in the Cloud](https://dl.acm.org/doi/abs/10.1145/3299869.3314047)
- Socrates。相比于传统存算分离，他进一步解耦，将持久性和可用性分离。
- 存储层进一步解耦为：日志服务器和数据页服务器，二者有一个RBPEX作为back up，只缓存次热点数据。XStore负责保存全量数据。
- XStore 在 Socrates 中扮演着与传统数据库系统中硬盘和磁带相同的角色，而计算节点和 Page Server 的主内存与 SSD 缓存（RBPEX）则在 Socrates 中扮演着传统系统中主内存的角色。

## ByteDance
### [Accelerating Cloud-Native Databases with Distributed PMem Stores](https://ieeexplore.ieee.org/document/10184639)
- 在字节跳动，基于计算存储分离架构构建了一个名为 veDB 的分布式数据库，为了满足关键业务对低延迟和高吞吐的需求，本文修改了系统的存储以利用持久内存 (PMem)
和远程直接内存访问 (RDMA) 网络来减少读/写延迟并提高吞吐量。还提出了一个查询下推框架，将部分计算推送到 PMem 存储层以加速分析查询并减少
计算层中事务工作负载的影响。TODO。

### [CDSBen: Benchmarking the Performance of Storage Services in Cloud-native Database System at ByteDance](https://www.vldb.org/pvldb/vol16/p3584-tang.pdf)
- 当前云原生数据库系统在各种云应用中广泛使用，该研究聚焦于此类系统中存储服务的性能基准测试问题。这些系统的核心思想是将传统单体 OLTP 数据库中的计算与存储分离。
呈现字节跳动云原生数据库 veDB 存储层的两个具有代表性的真实 I/O 工作负载的特征。为克服这些局限性，设计了一种基于学习的 I/O 工作负载基准测试工具 CDSBen。
通过在字节跳动进行部署，证明了 CDSBen 的优越性，其生成的 I/O 轨迹能够准确地模拟生产环境中的真实 I/O 轨迹。通过生成具有不同 I/O 特征的广泛 I/O 工作负载，验证了 CDSBen 的准确性和灵活性。