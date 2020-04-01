
```
ETX全节点机器配置：
    最低配置:
        CPU: 4 core
        内存: 8G
        硬盘: 100G 高速硬盘
        网络: 2M
    
    推荐配置:
        CPU: 8 core
        内存: 16G
        硬盘: 200G SSD (固态硬盘)
        网络: 5M+

        
1.节点文件下载
    etx 下载地址：wget https://github.com/Ethereum-x/Ethereum-x-go/releases/download/etx-v1.0/etx-v1.0-stable-linux.zip
    
2.创世文件下载：
    wget https://github.com/Ethereum-x/Ethereum-x-go/blob/master/docs/etx-genesis.json
    
    保持etx 和 etx-genesis.json 在同一个目录
    
3.解压
    unzip etx-v1.0-stable-linux.zip 

4.赋予getx可执行权限：
    sudo chmod 777 getx

5.进入解压目录，启动（命令解释，详情请见附录一）
    第一次运行getx, 需要使用创世文件：etx-genesis.json
    在命令行执行： ./getx  --datadir ~/etx/data  init ./etx-genesis.json 

6.启动节点，进入控制台模式：
    ./getx  --rpc --datadir ~/etx/data --rpcport 8888 --networkid 66666 --port 61918 --rpcapi "personal,eth,net,web3" --rpccorsdomain "*"  --wsport 8588 --wsapi "personal,eth,net,web3" --wsorigins "*" console 
    
    这一步，不要加--mine指令，还没有挖矿账户，否则会报错。
    
7.生成挖矿地址，密码"12345", 可以修改为自己设定的
    在控制台输入命令：personal.newAccount("12345") 

8.正常执行节点启动程序,如果是后台运行，请使用挂起操作
    如果要挖矿，请添加--mine指令。
    控制台运行：
    ./getx  --rpc --datadir ~/etx/data --rpcport 8888 --networkid 66666 --port 61918 --rpcapi "personal,eth,net,web3" --rpccorsdomain "*"  --wsport 8588 --wsapi "personal,eth,net,web3" --wsorigins "*" --mine 

    后台挂起运行：
    nohup ./getx  --rpc --datadir ~/etx/data --rpcport 8888 --networkid 66666 --port 61918 --rpcapi "personal,eth,net,web3" --rpccorsdomain "*"  --wsport 8588 --wsapi "personal,eth,net,web3" --wsorigins "*" --mine  >> getx.log &

ETX 相关操作命令：
eth：包含一些跟操作区块链相关的方法
net：包含以下查看p2p网络状态的方法
admin：包含一些与管理节点相关的方法
miner：包含启动&停止挖矿的一些方法
personal：主要包含一些管理账户的方法
txpool：包含一些查看交易内存池的方法
web3：包含了以上对象，还包含一些单位换算的方法

附录一
命令
   account     管理账户
   attach      启动一个交互式的JavaScript环境，（通过连接到远程节点） 
   bug         打开一个窗口来反馈bug
   console     启动一个交互式的JavaScript环境
   copydb      复制一个datadir，需要指定另一个datadir的路径
   dump        从区块链上dump指定的区块
   dumpconfig  显示配置信息
   export      导出区块信息到文件
   import      从文件导入区块信息
   init        初始化一个新的创世区块
   js          执行指定的js文件
   license     显示license信息
   makecache   生成 ethash验证信息缓存?(用于测试) 
   makedag     生成ethash挖矿DAG(用于测试)
   monitor     监控，显示节点指标  
   removedb    删除区块链和状态数据库
   version     打印版本号
   wallet      管理以太坊钱包
   help, h     显示所有的命令，和帮助信息

以太坊选项
ETHEREUM OPTIONS:
  --config value                        TOML 配置文件
  --datadir "/home/karalabe/.ethereum"  制定datadir位置
  --keystore                            制定keystore位置(默认在datadir里面)
  --nousb                               关闭监控usb钱包
  --networkid value                     网络标识符(数字，1=Frontier, 2=Morden (没有使用), 3=Ropsten, 4=Rinkeby)(默认: 1)
  --testnet                             测试网络: 预设为工作量证明模式的测试网络
  --rinkeby                             测试网络: 预设为权益证明模式的测试网络
  --syncmode "fast"                     区块同步模式（'fast','full',"light"）
  --ethstats value                      ethstats服务器的URL(nodename:secret@host:port)
  --identity value                      自定义节点名称
  --lightserv value                     最大允许的轻量级节点服务百分比 requests (0-90) (default: 0)
  --lightpeers value                    最多允许接入的轻量级节点数量（默认：20)
  --lightkdf                            减少秘钥生成时 内存和cup的使用量

开发者选项
DEVELOPER CHAIN OPTIONS:
  --dev                启动一个 权益证明 方式的网络，预先存一笔钱到开发者账户，并且启动挖矿 
  --dev.period value   区块处理时间?，在开发模式下（0=事务被处理时挖矿） (默认: 0)


ETHASH算法相关选项
ETHASH OPTIONS:
  --ethash.cachedir                         存储ethash验证缓存的目录（目录：在datadir里面 
  --ethash.cachesinmem value                ethash 保存在内存中的数量，每16mb（默认2） 
  --ethash.cachesondisk value               缓存在磁盘的ethash caches的百分比(默认: 3) 
  --ethash.dagdir "/home/karalabe/.ethash"  存储ethash挖矿DAG的目录地址，默认（home目录） 
  --ethash.dagsinmem value                  Number of recent ethash mining DAGs to keep in memory (1+GB each) (default: 1)
  --ethash.dagsondisk value                 Number of recent ethash mining DAGs to keep on disk (1+GB each) (default: 2)


事务池相关选项
TRANSACTION POOL OPTIONS:
  --txpool.nolocals             禁止对于本地提交的交易的价格豁免
  --txpool.journal value       本地事务磁盘日志（用于磁盘重启?）Disk journal for local transaction to survive node restarts (default: "transactions.rlp")
  --txpool.rejournal value     Time interval to regenerate the local transaction journal (default: 1h0m0s)
  --txpool.pricelimit value    Minimum gas price limit to enforce for acceptance into the pool (default: 1)
  --txpool.pricebump value     Price bump percentage to replace an already existing transaction (default: 10)
  --txpool.accountslots value  Minimum number of executable transaction slots guaranteed per account (default: 16)
  --txpool.globalslots value   Maximum number of executable transaction slots for all accounts (default: 4096)
  --txpool.accountqueue value  Maximum number of non-executable transaction slots permitted per account (default: 64)
  --txpool.globalqueue value   所有账户最大非执行事务槽数量  (默认: 1024)
  --txpool.lifetime value      最大非执行的事务队列时间总量 (默认: 3h0m0s)


性能调优选项
PERFORMANCE TUNING OPTIONS:
  --cache value            分配多少给内部缓存（兆字节） (最小 16MB / 数据库要求) (默认: 128)
  --trie-cache-gens value  保存在内存中的 trie node数量 (默认: 120)


账户相关选项
ACCOUNT OPTIONS:
  --unlock value    账户解锁，只有这个参数需要交互式输入密码
  --password value  账户的密码，非交互式输入


控制台API相关选项
API AND CONSOLE OPTIONS:
  --rpc                  启动http-rpc 服务 
  --rpcaddr value        http rpc 位于哪一个地址（ip） (默认: "localhost")
  --rpcport value        http rpc 位于哪一个端口 (默认: 8545)
  --rpcapi value         HTTP-RPC 提供哪些服务（可选：personal,db,eth,net,web3等）
  --ws                   启动 WS-RPC 服务
  --wsaddr value         WS-RPC 位于哪一个地址（ip） (默认: "localhost")
  --wsport value         WS-RPC 位于哪一个端口 (默认: 8546)
  --wsapi value          API's 提供哪些服务（可选：personal,db,eth,net,web3等）
  --wsorigins value      允许哪些域可以以访问websockts服务
  --ipcdisable           禁止 IPC-RPC 服务（windows多节点可选）
  --ipcpath              ipc服务 文件/管道地址  (转译后的)
  --rpccorsdomain value  prc服务允许的跨域访问的地址。
  --jspath loadScript    执行本地js文件的路径 （默认 .）
  --exec value           执行JavaScript 
  --preload value        预加载到控制台的JavaScript文件列表(逗号分隔)


网络相关选项
NETWORKING OPTIONS:
  --bootnodes value      用于P2P发现引导的节点（启动节点），用逗号隔开(轻量级服务使用v4+v5代替) Comma separated enode URLs for P2P discovery bootstrap (set v4+v5 instead for light servers)
  --bootnodesv4 value   Comma separated enode URLs for P2P v4 discovery bootstrap (light server, full nodes)
  --bootnodesv5 value   Comma separated enode URLs for P2P v5 discovery bootstrap (light server, light nodes)
  --port value          网络监听端口  (默认: 30303)
  --maxpeers value      最大节点数（设置为0时，网络被禁用）默认25 
  --maxpendpeers value  最大连接节点数，默认0 
  --nat value           NAT端口映射机制(any|none|upnp|pmp|extip:<IP>) (默认: "any")
  --nodiscover          禁止节点发现机制（手工添加）
  --v5disc              Enables the experimental RLPx V5 (Topic Discovery) mechanism
  --netrestrict value   Restricts network communication to the given IP networks (CIDR masks)
  --nodekey value       P2P 节点 秘钥文件
  --nodekeyhex value    十六进制的P2P节点密钥(用于测试)


挖矿相关选项
MINER OPTIONS:
  --mine                    启动挖矿
  --minerthreads value      挖矿时启动的CPU线程数量(默认：8)
  --etherbase value         挖矿奖励账户（默认account[0]）无账号时默认0 
  --targetgaslimit value    gas限制，低于该值的事务无法被记录 (默认：4712388) 
  --gasprice "18000000000"  挖矿接受交易的最低gas价格
  --extradata value         矿工对区块设置的扩展数据内容，默认客户端版本号 


GAS价格相关选项
GAS PRICE ORACLE OPTIONS:
--gpoblocks value      通过最近的块数量来计算gas价格  (默认: 10)
--gpopercentile value  参考近期交易区块gas价格的百分比来计算gas价格 (默认: 50)


虚拟机相关选项
VIRTUAL MACHINE OPTIONS:
  --vmdebug  记录VM和合约相关的debug信息 


日志和调试相关选项
LOGGING AND DEBUGGING OPTIONS:
  --metrics                 启动指标收集和报告 
  --fakepow                 关闭POW工作量证明验证 
  --nocompaction            输入框导入后禁止压缩? Disables db compaction after import
  --verbosity value         日志等级  0=安静, 1=错误, 2=警告, 3=info, 4=debug, 5=详细 (默认: 3)
  --vmodule value           Per-module verbosity: comma-separated list of <pattern>=<level> (e.g. eth/*=5,p2p=4)
  --backtrace value         Request a stack trace at a specific logging statement (e.g. "block.go:271")
  --debug                   突出显示调用位置日志(文件名及行号)
  --pprof                   启动pprof http服务（一种go语言的调试服务器） 
  --pprofaddr value         pprof HTTP 服务监听ip (默认: "127.0.0.1")
  --pprofport value         pprof HTTP 服务监听端口 (默认: 6060)
  --memprofilerate value    Turn on memory profiling with the given rate (default: 524288)
  --blockprofilerate value  Turn on block profiling with the given rate (default: 0)
  --cpuprofile value        将cpuWrite CPU profile to the given file
  --trace value             将错误信息写给定的文件中


WHISPER相关选项
WHISPER 是一种信息检索协议，它允许节点间直接以一种安全的形式互发信息，并对第三方组织窥探者隐藏发送者和接收者的信息。 引用：
WHISPER (EXPERIMENTAL) OPTIONS:
  --shh                       启动 Whisper
  --shh.maxmessagesize value  最大接收的消息大小 (默认: 1048576)
  --shh.pow value             可接受的最小的POW (默认值: 0.2)


```
