[![Tweet](https://img.shields.io/twitter/url/http/Hktalent3135773.svg?style=social)](https://twitter.com/intent/follow?screen_name=Hktalent3135773) [![Follow on Twitter](https://img.shields.io/twitter/follow/Hktalent3135773.svg?style=social&label=Follow)](https://twitter.com/intent/follow?screen_name=Hktalent3135773) [![GitHub Followers](https://img.shields.io/github/followers/hktalent.svg?style=social&label=Follow)](https://github.com/hktalent/)
<p align="center">
   <a href="/README_EN.md">README_EN</a>
   <a href="/static/Installation.md">编译/安装/运行</a> •
   <a href="/static/usage.md">参数说明</a> •
   <a href="/static/running.md">如何使用</a> •
   <a href="/static/scenario.md">使用场景</a> •
   <a href="/static/pocs.md">POC列表</a> •
   <a href="/static/development.md">自定义扫描</a>
</p>

# 特性

<h1 align="center">
<img width="928" alt="image" src="https://user-images.githubusercontent.com/18223385/175768227-098c779b-6c5f-48ee-91b1-c56e3daa9c87.png">
</h1>

- 快速端口扫描，指纹检测功能
- 快速登录密码爆破功能
- 快速POC检测功能
- 快速敏感文件检测
- 轻量级、开源、跨平台使用
- 支持多种类型的输入 - STDIN/HOST/IP/CIDR/URL/TXT
- 支持多种输出类型 - JSON/TXT/CSV/STDOUT
- 可配置将结果统一存储到Elasticsearch
- 带有上下文路径的url列表，启用精确扫描 UrlPrecise=true ./main -l xx.txt
- 开启智能子域遍历， export EnableSubfinder=true
- 自动识别域（DNS）关联多个IP的情况，并自动扫描关联的多个IP
- 预处理，当列表中多个域名的ip相同时，合并端口扫描，提高效率
- 深入分析，自动关联扫描：自动获取ssl中的域名信息，如*.xxx.com，并配置允许自动子域遍历，子域遍历自动完成，添加目标到扫描列表
- 自动化供应链分析和扫描，需要授权才能使用
- 允许通过config/config.json配置定义自己的字典，或者设置相关的开关，可以在这里定义nuclei、httx、naabu的几个Options
- 配置说明如下：
```json
{
  "CacheName": ".DbCache", // 提速、优化、避免重复，缓存目录
  "autoRmCache": "true",   // 程序自动删除缓存，如果你希望保留下次相同目标提速，可以保留
  //////////各种不需要我说对可自定义字典，你可以配置相同文件 start///////////////
  "ssh_username": "pkg/hydra/dicts/ssh_user.txt",
  "ssh_pswd": "pkg/hydra/dicts/ssh_pswd.txt",
  "ssh_default": "pkg/hydra/dicts/ssh_default.txt",
  "ftpusername": "pkg/hydra/dicts/ftp_user.txt",
  "ftp_pswd": "pkg/hydra/dicts/ftp_pswd.txt",
  "ftp_default": "pkg/hydra/dicts/ftp_default.txt",
  "rdpusername": "pkg/hydra/dicts/rdp_user.txt",
  "rdp_pswd": "pkg/hydra/dicts/rdp_pswd.txt",
  "rdp_default": "pkg/hydra/dicts/rdp_default.txt",
  "mongodbusername": "pkg/hydra/dicts/mongodb_user.txt",
  "mongodb_pswd": "pkg/hydra/dicts/mongodb_pswd.txt",
  "mongodb_default": "pkg/hydra/dicts/mongodb_default.txt",
  "mssqlusername": "pkg/hydra/dicts/mssql_user.txt",
  "mssql_pswd": "pkg/hydra/dicts/mssql_pswd.txt",
  "mssql_default": "pkg/hydra/dicts/mssql_default.txt",
  "mysqlusername": "pkg/hydra/dicts/mysql_user.txt",
  "mysql_pswd": "pkg/hydra/dicts/mysql_pswd.txt",
  "mysql_default": "pkg/hydra/dicts/mysql_default.txt",
  "oracleusername": "pkg/hydra/dicts/oracle_user.txt",
  "oracle_pswd": "pkg/hydra/dicts/oracle_pswd.txt",
  "oracle_default": "pkg/hydra/dicts/oracle_default.txt",
  "postgresqlusername": "pkg/hydra/dicts/postgresql_user.txt",
  "postgresql_pswd": "pkg/hydra/dicts/postgresql_pswd.txt",
  "postgresql_default": "pkg/hydra/dicts/postgresql_default.txt",
  "redisusername": "pkg/hydra/dicts/redis_user.txt",
  "redis_pswd": "pkg/hydra/dicts/redis_pswd.txt",
  "redis_default": "pkg/hydra/dicts/redis_default.txt",
  "smbusername": "pkg/hydra/dicts/smb_user.txt",
  "smb_pswd": "pkg/hydra/dicts/smb_pswd.txt",
  "smb_default": "pkg/hydra/dicts/smb_default.txt",
  "telnetusername": "pkg/hydra/dicts/telnet_user.txt",
  "telnet_pswd": "pkg/hydra/dicts/telnet_pswd.txt",
  "telnet_default": "pkg/hydra/dicts/telnet_default.txt",
  "tomcatuserpass": "brute/dicts/tomcatuserpass.txt",
  "jbossuserpass": "brute/dicts/jbossuserpass.txt",
  "weblogicuserpass": "brute/dicts/weblogicuserpass.txt",
  "filedic": "brute/dicts/filedic.txt",
  "top100pass": "brute/dicts/top100pass.txt",
  "bakSuffix": "brute/dicts/bakSuffix.txt",
  "fuzzct": "brute/dicts/fuzzContentType1.txt",
  "fuzz404": "brute/dicts/fuzz404.txt",
  "page404Content1": "brute/dicts/page404Content.txt",
  "eHoleFinger": "pkg/fingerprint/dicts/eHoleFinger.json",
  "localFinger": "pkg/fingerprint/dicts/localFinger.json",
  "HydraUser": "",
  "HydraPass": "",
  //////////各种不需要我说对可自定义字典，你可以配置相同文件 end///////////////
  // naabu 扫描到到端口后自动调用nmap跑指纹，然后自动调用弱口令检测，windows自动加.exe你不需要关注
  "nmap": "nmap -n --unique --resolve-all -Pn --min-hostgroup 64 --max-retries 0 --host-timeout 10m --script-timeout 3m -oX {filename} --version-intensity 9 --min-rate 10000 -T4",
  "UrlPrecise": true, // -l 传入文件清单如果是http[s]带上下文，默认启动精准扫描
  "ParseSSl": false,  // HW打点默认关闭，互联网赏金目标建议设置true
  "EnableSubfinder": false, // 默认关闭ssl中证书子域名爆破,互联网赏金目标建议设置true
  "naabu_dns": {},  // naabu工具对dns配置
  "naabu": {"TopPorts": "1000","ScanAllIPS": true}, // naabu配置
  "nuclei": {}, // nuclei配置，例如线程等
  "httpx": {}   // httpx 配置,
  "enableEsSv": true,        // 开启结果send 到es
  "esthread": 8 // 结果写入Elasticsearch的线程数,
  "esUrl": "http://127.0.0.1:9200/%s_index/_doc/%s" // Elasticsearch url
}
```

# 工作流程

<img src="static/workflow.jpg">

- 0.【智能子域名爆破】集成Subfinder,当通过 export EnableSubfinder=true 开启后，ssl证书中的域名信息包含"*."开头时自动启动子域名遍历
- 1.【端口扫描】集成Nuclei官方产品naabu ( > 2.1k)
- 2.【服务识别】naabu调用系统安装的nmap，请先自行安装nmap
  * 2.1 nmap扫描后，自动启动集成当kscan进行弱密码检测，密码字典支持自定义字典，可以通过config.json进行配置
- 3.【网页扫描】集成httpx（ > 3.2k），Nuclei官方出品
  * 3.1 【指纹识别】集成优化的EHole（ > 1.4k）
- 4.【漏洞扫描】
  * 集成核（ > 8.6k）+核模板（4.5k优化版，https://github.com/hktalent/nuclei-templates）
  * 集成 xray 2.0 (6.9k)，共 354 个 POC
  * 集成 vscan 实现了8个fuzz组件，同时实现了集成14类常用组件的漏洞检测

# 如何安装
```bash
go install github.com/hktalent/scan4all@2.4.8
scan4all -h
```
# 如何使用
- 1、启动 Elasticsearch, 当然你可以使用传统方式输出、结果
```bash
mkdir -p logs data
docker run --restart=always --ulimit nofile=65536:65536 -p 9200:9200 -p 9300:9300 -d --name es -v $PWD/logs:/usr/share/elasticsearch/logs -v $PWD/config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml -v $PWD/config/jvm.options:/usr/share/elasticsearch/config/jvm.options  -v $PWD/data:/usr/share/elasticsearch/data  hktalent/elasticsearch:7.16.2
# 初始化es 索引,每种工具的结果结构不一样，分开存储
./config/initEs.sh

# 搜索语法，更多的查询方法，自己学 Elasticsearch
http://127.0.0.1:9200/nmap_index/_doc/_search?q=_id:192.168.0.111
其中92.168.0.111 是要查询的目标

```
- 使用前请自行安装nmap
<a href=https://github.com/hktalent/scan4all/discussions>使用帮助</a>
```bash
go build
# 精准扫描 url列表 UrlPrecise=true
UrlPrecise=true ./scan4all -l xx.txt
```

# 变更日志
- 2022-06-30 嵌入式集成私人版本nuclei-templates 共3744个YAML POC； 1、集成Elasticsearch存储中间结果 2、嵌入整个config目录到程序中
- 2022-06-27 优化模糊匹配，提高正确率、鲁棒性;集成ksubdomain进度
- 2022-06-24 优化指纹算法；增加工作流程图
- 2022-06-23 添加参数ParseSSl，控制默认不深度分析SSL中的DNS信息，默认不对SSL中dns进行扫描；优化：nmap未自动加.exe的bug；优化windows下缓存文件未优化体积的bug
- 2022-06-22 集成11种协议弱口令检测、密码爆破：ftp、mongodb、mssql、mysql、oracle、postgresql、rdp、redis、smb、ssh、telnet，同时优化支持外挂密码字典
- 2022-06-20 集成Subfinder，域名爆破，启动参数导出EnableSubfinder=true，注意启动后很慢； ssl证书中域名信息的自动深度钻取
  允许通过 config/config.json 配置定义自己的字典，或设置相关开关
- 2022-06-17 优化一个域名多个IP的情况，所有IP都会被端口扫描，然后按照后续的扫描流程
- 2022-06-15 此版本增加了过去实战中获得的几个weblogic密码字典和webshell字典
- 2022-06-10 完成核的整合，当然包括核模板的整合
- 2022-06-07 添加相似度算法来检测 404
- 2022-06-07 增加http url列表精准扫描参数，根据环境变量UrlPrecise=true开启

# Donation
| Wechat Pay | AliPay | Paypal | BTC Pay |BCH Pay |
| --- | --- | --- | --- | --- |
|<img src=https://github.com/hktalent/myhktools/blob/master/md/wc.png>|<img width=166 src=https://github.com/hktalent/myhktools/blob/master/md/zfb.png>|[paypal](https://www.paypal.me/pwned2019) **miracletalent@gmail.com**|<img width=166 src=https://github.com/hktalent/myhktools/blob/master/md/BTC.png>|<img width=166 src=https://github.com/hktalent/myhktools/blob/master/md/BCH.jpg>|