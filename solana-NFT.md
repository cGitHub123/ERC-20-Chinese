首先，eth用的solidity,但是sol用的是rust

### Metaplex
![Screenshot from 2022-06-18 20-29-44](/assets/Screenshot%20from%202022-06-18%2020-29-44.png)

### 下载必须的工具

#### hashlips_art_engine

![Selection_016](/assets/Selection_016.png)

#### solana cli

![Screenshot from 2022-06-18 20-35-30](/assets/Screenshot%20from%202022-06-18%2020-35-30.png)

安装完之后记得配置环境变量，它会有提示

![Screenshot from 2022-06-18 20-43-39](/assets/Screenshot%20from%202022-06-18%2020-43-39.png)

#### 浏览器安装solana钱包

solana钱包不是小狐狸，而是phontam

![Screenshot from 2022-06-18 20-48-47](/assets/Screenshot%20from%202022-06-18%2020-48-47.png)

然后通过助记词导入钱包即可

![Screenshot from 2022-06-18 21-00-59](/assets/Screenshot%20from%202022-06-18%2021-00-59.png)

#### 通过solana cli创建一个基于文件系统的钱包

```
mkdir ~/my-solana-wallet
solana-keygen new --outfile ~/my-solana-wallet/my-keypair.json
```

这里会让你输入一个密码，输入就行，然后就成功了

#### 安装Candy Machine V2

![Screenshot from 2022-06-18 21-17-44](/assets/Screenshot%20from%202022-06-18%2021-17-44.png)

#### 把下载的移到同一个文件夹

![Screenshot from 2022-06-18 21-57-04](/assets/Screenshot%20from%202022-06-18%2021-57-04.png)

### 配置和空投sol

#### 配置

```
caibin@caibin-MS-7C82:~/solana-project$ solana config set --keypair ./my-keypair.json
Config File: /home/caibin/.config/solana/cli/config.yml
RPC URL: https://api.mainnet-beta.solana.com
WebSocket URL: wss://api.mainnet-beta.solana.com/ (computed)
Keypair Path: ./my-keypair.json
Commitment: confirmed
```
但是，看输出我们发现，URL指向的是solana的主网，所以需要执行:
```
caibin@caibin-MS-7C82:~/solana-project$ solana config set --url https://metaplex.devnet.rpcpool.com/
Config File: /home/caibin/.config/solana/cli/config.yml
RPC URL: https://metaplex.devnet.rpcpool.com/
WebSocket URL: wss://metaplex.devnet.rpcpool.com/ (computed)
Keypair Path: ./my-keypair.json
Commitment: confirmed
```
然后我们用solana config get查看一下:
```
caibin@caibin-MS-7C82:~/solana-project$ solana config get
Config File: /home/caibin/.config/solana/cli/config.yml
RPC URL: https://metaplex.devnet.rpcpool.com/
WebSocket URL: wss://metaplex.devnet.rpcpool.com/ (computed)
Keypair Path: ./my-keypair.json
Commitment: confirmed
```

#### 空投一些solana

```
caibin@caibin-MS-7C82:~/solana-project$ solana airdrop 2
Requesting airdrop of 2 SOL

Signature: 2JFTHyaHbXnic7zFFY4jUse4HEctdrcu66Ezd2iLLFiqxXSCWsYt37M6S9ZSqwUNuW7TmwcRhMcqufnE3t62C68Q

2 SOL
```

检查一下是否空投成功

```
caibin@caibin-MS-7C82:~/solana-project$ solana balance
2 SOL
```

### hashlips_art_engine构建art

#### 解压缩hashlips_art_engine-1.1.2_patch_v6

这个就是用来生成图片的，和solana没关系，它生成图片可以被
metaplex和solana认可

![Screenshot from 2022-06-18 22-55-48](/assets/Screenshot%20from%202022-06-18%2022-55-48.png)

#### 用vscode打开解压后的hashlips_art_engine-1.1.2_patch_v6

#### 安装依赖
![Screenshot from 2022-06-18 22-58-55](/assets/Screenshot%20from%202022-06-18%2022-58-55.png)

#### 修改配置文件
![Selection_017](/assets/Selection_017.png)

#### 开始生成

```
caibin@caibin-MS-7C82:~/solana-project/hashlips_art_engine-1.1.2_patch_v6$ yarn generate
yarn run v1.22.19
$ node index.js
Created edition: 0, with DNA: ab40c455bf9dec78b50909d414d873442f5dd4f7
Created edition: 1, with DNA: 594219bfa83c650c4811a0db3ad0c2ec03f5bdf2
Created edition: 2, with DNA: 286d53c27fa6498baf7003aa85a5aab0f72e0264
Created edition: 3, with DNA: 0697faddf45aa21aa7952b94adcf3ab1c57e15d1
Created edition: 4, with DNA: 5f34550a61642e6484671b7b40ca1b6489efcb91
Created edition: 5, with DNA: 7ec28193dc58bb1c84659383c8ce5051e5b33404
Created edition: 6, with DNA: a636d95ade44e435d6bcc3dce6760c03c05c2970
Created edition: 7, with DNA: 3de84bb3b620a7ba0e8397a27e8e8d4a7214e0c4
Created edition: 8, with DNA: 73e12fadafeb9b826cd31ecc9779b99f5942c6e3
Created edition: 9, with DNA: c100cb4bb0b08a900640ce891811d76f2625e75d
Done in 1.03s.
```

然后看看生成的图片:
![Screenshot from 2022-06-18 23-35-16](/assets/Screenshot%20from%202022-06-18%2023-35-16.png)

### metaplex-master

#### 解压缩
```
caibin@caibin-MS-7C82:~/solana-project$ unzip metaplex-master.zip
```

#### 在解压后的文件夹下建立assets

然后把上面build的那几个图片和json复制过来

![Screenshot from 2022-06-19 01-48-28](/assets/Screenshot%20from%202022-06-19%2001-48-28.png)

#### 然后在VSCODE里面打开解压后的文件

我们先看:

![Screenshot from 2022-06-19 01-50-49](/assets/Screenshot%20from%202022-06-19%2001-50-49.png)

做一些改动,主要是price(价格),number(数量),solTreasuryAccount(交易地址，这个不需要用前面生成的那个)，还有goLiveDate(发行时间)

```
{
  "price": 0.01,
  "number": 10,
  "gatekeeper": null,
  "solTreasuryAccount": "wdNb5Ri42xWvmPSebaFV7yK7Bbhzt9uuwFLLrXvJ8bB",
  "splTokenAccount": null,
  "splToken": null,
  "goLiveDate": "26 May 2022 00:00:00 GMT",
  "endSettings": null,
  "whitelistMintSettings": null,
  "hiddenSettings": null,
  "storage": "arweave",
  "ipfsInfuraProjectId": null,
  "ipfsInfuraSecret": null,
  "awsS3Bucket": null,
  "nftStorageKey": null,
  "noRetainAuthority": false,
  "noMutable": false
}
```
#### 部署candy Machine

首先在metaplex-master/js目录下安装依赖

```
caibin@caibin-MS-7C82:~/solana-project/metaplex-master/js$ yarn
yarn install v1.22.19
[1/5] Validating package.json...
[2/5] Resolving packages...
[3/5] Fetching packages...
```

然后找到需要upload的地方
![Screenshot from 2022-06-19 02-12-11](/assets/Screenshot%20from%202022-06-19%2002-12-11.png)

```
ts-node ~/solana-project/metaplex-master/js/packages/cli/src/candy-machine-v2-cli.ts upload \
    -e devnet \
    -k ~/solana-project/my-keypair.json \
    -cp ~/solana-project/metaplex-master/js/packages/cli/example-candy-machine-upload-config.json \
    ~/solana-project/metaplex-master/assets
```

输出:
```
Candy machine address:  ESjRWnyBNcVVmjhgXiw33GCnjWivg8HiZHvg8uxxKqAs
Collection metadata address:  6rCUit4ugLDYZ1gDAGWLUKkZk2uyddmmLhB95nWnTc9j
Collection metadata authority:  BTDw4bK8XthkN6GLGTQbu7RZSKxcByYiqJuAGzTF9thb
Collection master edition address:  BP1kSFNz9Mhj11bEuByE3wAhnoxfcyxyMVUmo7VFupFE
Collection mint address:  GqSggk1DuqC4TrvKRKjk6sQjqtN3F8YT3TtV7JwsFFYr
Collection PDA address:  BUBkHiTiPBducytG5skU3T5YmWbcrDjpxxmGFvb7T5E8
Collection authority record address:  H4xMASQXTwxP4W5dgdtibv8wjxjx84BfpVvC9mCG6E3m
Collection:  {
  collectionMetadata: '6rCUit4ugLDYZ1gDAGWLUKkZk2uyddmmLhB95nWnTc9j',
  collectionPDA: 'BUBkHiTiPBducytG5skU3T5YmWbcrDjpxxmGFvb7T5E8',
  txId: '3foQpuG51CjTkKzheRQWKwU31NBow6JqVU9wjVn1q72dqRnQmqtxYNxyF4ga623tYHoaRT6unx6rkkopGvqrdgPT'
}
```

#### 配置UI

进入/js/packages/candy-machine-ui

首先安装依赖

```
caibin@caibin-MS-7C82:~/solana-project/metaplex-master/js/packages/candy-machine-ui$ yarn
```
然后我们吧.env.example改成.env，并修改里面的MACHINE_ID为ESjRWnyBNcVVmjhgXiw33GCnjWivg8HiZHvg8uxxKqAs

然后执行在candy-machine-ui下执行yarn start

切换网络到devnet

![Screenshot from 2022-06-19 02-37-54](/assets/Screenshot%20from%202022-06-19%2002-37-54.png)

然后导入我们最开始的私钥

我们cat下那个keypair.json，里面的数组就是私钥

然后从界面上连接钱包，点击mint即可

![Screenshot from 2022-06-19 03-21-11](/assets/Screenshot%20from%202022-06-19%2003-21-11.png)
