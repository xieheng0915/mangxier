##### 02-BTC密码学原理
###### hash function propreties: 
- collision resistance
- hiding: one direction 单向性
但暴力求解是可以求解的。

以上两个属性结合使用：
digital commitment / digital equivalent of a sealed envelope

H(x||nonce) nonce:是一个随机数，
nonce的选取要保证随机均匀分布

- 比特币用hash函数的第三个特性： puzzle friendly -> mining
Mining: H(block header) <= target
->PoW 随机，因此需要工作量-> 工作量证明： PoW -> 公布出去， -> 其他矿工验证。
挖矿很难，验证很容易
difficult to solve, but easy to verify

比特币所用hash: SHA-256


###### 比特币的数字签名管理：去中心化签名

(public key, private key)
比特币是不加密的，签名用于交易

比特币中，一般先对message 进行Hash，再对此签名

##### 03-BTC数据结构
1. 哈希指针 hash pointers
   - 结构体的位置pointer
   - 所连接的结构体的H(x),用于检测数据结构的完整性
  Block chain is a linked list with hash pointers.

   改变任何一个区块，会引发多米诺骨牌效应，导致之后所有区块都被改变
   因此只需要保存最近的区块，就可以保持整个区块链的完整性。
   如果需要用到自己保存的区块之前的区块的内容，可以从别的节点上获取。
   每个区块都保持着前一个区块的哈希值。
   对于恶意节点给出的区块，只要将收到的区块哈希值和自己保存的区块哈希值进行对比，就可以知道是否是恶意节点的区块

2. 默克尔树 Merkle tree
   Merkle tree 和 常见的binary tree 的区别：
    - 用hash pointer 替代了普通pointer
    - 效率更高，二叉树形式
    - Merkle pool: 
        比特币中有两种节点，full nodes, 和 light nodes, 轻节点只保存block header, 而全节点包含blok header 和 block body, 对于比特币钱包，保存的是轻节点。

        