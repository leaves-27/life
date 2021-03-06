# 简介：

1.区块链的定义：是由包含交易信息的区块从后到前有序链接起来的数据结构。
2.区块链的存储：可以被存储成文件或存储到简单的数据库中。
3.区块链的结构：类似于栈的结构，创世区块位于栈底，最新的区块位于栈顶，区块与首区块之间的距离是区块高度。
4.区块链历史不可改变的原因：区块与区块之间通过父区块哈希值相连，每个父区块内容的变化会影响父区块哈希值的变化，父区块哈希值的变化又会影响子区块内容的变化，子区块内容的变化又会影响子区块哈希值的变化，这样依次递推。使得要改变一个区块的内容将要改变整个区块链所有区块的内容。这样对于较长一点的区块链来说，工作量是非常巨大的，任何人几乎都不可能完成。

# 区块结构：

由区块头和区块主体构成
区块头由一系列元数据组成。大约80字节。
区块主体由一长串交易组成。每一个交易平均至少250字节，而每个区块主体平均至少500个交易。

# 区块头
由三组区块元数据组成.

1.父区块哈希值:用于将该区块与区块链中前一区块相连接。
2.merkle树根数据:用来有效的总结区块中所有的交易。
3.挖矿相关：
  难度:
  nonce:
  时间戳:

# 区块标识符
1.区块哈希值
2.区块高度

# 创世区块
创世区块的产生时间
创世区块的所在位置

# 区块的链接
在网络中接受到一个区块时，如何将其链接到区块链上：获取该区块元数据中的父区块哈希值字段，获取到父区块的哈希值，然后把其链接到相应的父区块上。

# Merkle树
1.Merkle树的定义：
  Merkle树是一种哈希二叉树，它是一种用作快速归纳和校验大规模数据完整性的数据结构。
2.Merkle树的用途:
  (1)被用来归纳一个区块中的所有交易
  (2)生成整个交易集合的数字指纹
  (3)提供了一种校验区块是否存在某交易的高效途径
3.Merkle树的生成:
  递归地对哈希节点对进行哈希，并将新生成的哈希节点插入到Merkle树中，直到只剩一个哈希节点，该节点就是Merkle树的根.

4.Merkle树校验区块是否存在某交易的高效途径的原理：
当N个数据元素经过加密后插入Merkle树时，你至多计算2*log2(N)次就能检查出任意某数据元素是否在该树中，这使得该数据结构非常高效。

# Merkle树和简单支付验证
1.简单支付验证(SPV)的概念：
SPV节点不保存所有交易也不会下载整个区块，仅仅保存区块头。它们使用认证路径或者Merkle路径来验证交易存在于区块中，而不必下载区块中所有交易.