# ERC-20-Chinese

### 安装metamask

在谷歌商店，安装Metamask

![Screenshot from 2022-06-17 00-40-59](/assets/Screenshot%20from%202022-06-17%2000-40-59.png)

### 切换到测试网络

![Screenshot from 2022-06-17 00-43-15](/assets/Screenshot%20from%202022-06-17%2000-43-15.png)

### 拷贝地址

![Screenshot from 2022-06-17 00-44-34](/assets/Screenshot%20from%202022-06-17%2000-44-34.png)

也就是Account3下面那个地址

### 去申请测试的ETH

https://faucet.egorfine.com/ 然后填上地址

然后稍等一会，就可以看到账户里多了几个ETH


### 开始编写合约

进入:

http://remix.ethereum.org/#optimize=false&runs=200&evmVersion=null&version=soljson-v0.5.0+commit.1d4f565a.js&language=Solidity

新建erc20.sol,将code.md代码复制过去

### 编译合约

![Selection_002](/assets/Selection_002.png)

### 部署合约

![Selection_004](/assets/Selection_004.png)

### 查看

https://ropsten.etherscan.io/tx/0xd1cc1ce4ca4eb382f5f9e4187020bafb2cc5e543d1428f1cd63addde79ab7eee

然后我们就可以看到我们的合约地址

![Selection_006](/assets/Selection_006.png)

查看合约:

![Selection_007](/assets/Selection_007.png)

### 验证:

我们点击contract, 然后点击verify，

![Selection_008](/assets/Selection_008.png)

把代码粘贴上，就完成了:

![Selection_010](/assets/Selection_010.png)

然后回来之后，我们可以看到已经验证完成:

![Selection_011](/assets/Selection_011.png)

然后在这里我们可以查查拥有的token:

![Selection_012](/assets/Selection_012.png)

### 操作:

![Selection_013](/assets/Selection_013.png)
