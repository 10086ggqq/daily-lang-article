# 素材卡 · 第 11 期 PHP · 热点版

(工作流第 3 步产物,按 `references/素材收集模板-热点版.md` 填写;查不到的条目写「暂缺」,不编造。)

## 基本信息

- 期数:第 11 期(用户指定;与同日成稿的哲学版为姊妹篇,文件名以「-热点版」后缀区分)
- 主题语言:PHP
- 版本:热点版
- 热点来源:用户上传(2026-10-24 会话,含事件全文、1024 节贺图 asset/1024.jpg、梗图 asset/php搞笑漫画.jpg);已另行检索独立信源交叉
- 客串语言及连接点:Ada——本期两个漏洞是教科书级的内存安全错误(内存损坏、释放后使用),而 Ada(1983 年美国国防部标准 ANSI/MIL-STD-1815A,首席设计师 Jean Ichbiah,CII Honeywell-Bull)想手动释放内存必须先实例化名为 Unchecked_Deallocation 的库过程,等于犯错前先签字;与 PHP「先跑起来」的脾气构成同年代两极(出处:Wikipedia Ada 条目、AdaIC、learn.adacore.com)

## 热点事件卡(钩子的原料)

- 事件一句话:2026-10-21,PHP 因两个内核级未认证 RCE 漏洞(合称 PHP2Shell)提前发布紧急补丁,受影响的是支撑近七成网站的解释器内核,多国网络安全机构同日发警报
- 关键细节(逐条带信源):
  1. CVE-2026-109618 / CVE-2026-109619,CVSS 4.0 评分 9.2,无需认证即可远程代码执行;mod_php 与 PHP-FPM 部署均受影响(信源:CISA 2026-10-21 警报;Watchtowr《PHP2Shell FAQ》;Zscaler、Unit 42、Datadog Security Labs 分析文)
  2. 官方修复版本:PHP 8.5.12、8.4.27、8.3.36、8.2.35,2026-10-21 发布;升级后必须重启所有 PHP 进程并重建容器,内存中旧进程不替换则补丁无效(信源:PHP 基金会博客《Today's PHP Security Release, and How We're Strengthening PHP Security》2026-10-21)
  3. 披露流程被泄露打乱:10-20 细节外流,含演示视频与「CVSS 10.0」说法(PHP 官方澄清非其评分,官方定为 9.2),发布日由原协调披露计划提前至 10-21(信源:The Hacker News 2026-10 报道)
  4. AI 参与发现:安全公司 Calif 的研究员用 OpenAI GPT-5.6 Sol 模型审计 PHP C 源码发现漏洞,Wiz 独立报告;OpenAI 称之为给防御者打开「防御者窗口」;NSA、CISA 等 21 日当天发警报(信源:用户素材为主,聚合报道 aiaulis.com 等交叉;信源等级中等,正文一律间接表述,不写模型名)
  5. 政府与游戏影响:德国、法国(含巴黎警察局)、荷兰(DigiD)等政府网站预防性下线;FF14 暂停新登录、赛马娘全面停服;《World Quest》《Please Save My Pandemonium!》两款运营 10 年以上的老游戏永久停服(信源:Inven Global、Kotaku、The Verge;政府名单仅用户素材,正文未采用)
  6. Cloudflare 报告出现早期利用尝试,截至 2026-10-24 无大规模得手的公开报道(信源:检索摘要转述;正文未写)
  7. 临时缓解:与公网隔离/下线、禁用 session.upload_progress、在 Web 服务器层拦 multipart 请求,均只能缩暴露面(信源:用户素材;dev.to 按 SAPI 整理的 stopgaps 文)
- 发生日期与后续:发生 2026-10-20(泄露)、2026-10-21(补丁与各机构警报);后续:PHP 基金会发安全流程强化说明,Laravel Forge 等平台发修补指南;截至 10-24 事件仍在监测中
- 信源(两条以上独立信源 ✓):CISA(https://www.cisa.gov/news-events/alerts/2026/10/21/critical-vulnerabilities-php-require-immediate-patching)、PHP 基金会博客(thephp.foundation/blog/2026/10/21/…)、The Hacker News、Watchtowr、Unit 42、Zscaler、Datadog、Sansec、Inven Global、Kotaku
- 与主题语言的连接点(直接):出事的就是 PHP 解释器内核本身——正文讲的请求处理模型、mod_php/PHP-FPM 部署方式,正是漏洞成立的土壤
- 切入面:一个时刻(补丁提前落地,响应窗不到 24 小时)

## 方向一:梗、绰号与社区声音

- 绰号或梗:PHP2Shell(安全社区对本组漏洞的统称);「以后禁止 AI 挖洞!」——用户上传中文社区漫画(asset/php搞笑漫画.jpg):会议室三格,汇报 PHP 大洞、各抒己见、喊话者下格飞出窗外
- 真实吐槽 / 论坛语录:①OpenAI「防御者窗口」表述(正文间接转述);②《World Quest》停服公告大意「Shutting Down Because We Can't Fix It」(Inven Global 报道标题);③「PHP 是世界上最好的语言」梗哲学版已用,本期不复用
- 可写进文章的点:漫画与「防御者窗口」均已入正文

## 方向二:人物小故事(热点版专属)

- 故事 1:Magnus Manske,德国程序员,2001 年夏用 PHP + MySQL 为 Wikipedia 重写 wiki 程序(替换 Perl 写的 UseModWiki),2002-01-25 切换上线(维基人称「Manske 日」),后继版本 2003 年定名 MediaWiki;Wikipedia 常年位居全球访问量前十(出处:mediawiki.org《MediaWiki history》、Wikimedia Diff 2016-01-18 回顾文、AOSA v2 MediaWiki 章)
- 与热点的呼应点:本次受影响系统名单里就有 MediaWiki;出事的那类系统,当年正是用它写成的。呼应一句话带过,已入正文,不展开

## 方向三:名言与硬细节

- 名言 1:「a set of small tight cgi binaries written in C」——Rasmus Lerdorf,1995-06-08 Usenet 发帖宣布 PHP Tools 1.0 开源(出处:php.net《History of PHP》)。正文为控制术语数量改为间接表述
- 名言 2:「Shutting Down Because We Can't Fix It」——《World Quest》停服公告大意(Inven Global 报道标题,正文注明系大意)
- 名言 3:「以后禁止 AI 挖洞!」——中文社区漫画(用户上传)
- 硬细节:
  1. CVE-2026-109618 / 109619,CVSS 4.0 均为 9.2;修复版本 8.5.12 / 8.4.27 / 8.3.36 / 8.2.35,2026-10-21 发布(信源同事件卡 1、2)
  2. Rasmus Lerdorf 格陵兰出生、加拿大长大;1995-06-08 新闻组发帖开源 PHP Tools(出处:php.net《History of PHP》)
  3. PHP 基金会 2021-11-22 成立,JetBrains 博客《The New Life of PHP》宣布,JetBrains、Automattic、Acquia、Craft CMS、Laravel 等发起,Acquia 开张当天捐 2.5 万美元(出处:JetBrains 博客 2021-11-22、Dries Buytaert 博客 dri.es)
  4. PHP 7.4 于 2022-11-28 停止安全支持,末版 7.4.33;8.0、8.1 也已停更(出处:php.net/supported-versions.php、endoflife.date/php)
  5. W3Techs 2026-10 数据:能查明服务端语言的网站近七成(69.3%)由 PHP 生成页面(出处:w3techs.com;与哲学版素材卡同源)
  6. 7.4/8.0/8.1 仅获精简源码补丁,5.4–7.3 无官方修复,须迁移(用户素材,与官方支持时间表相符)

## 代码与配图

- 经典代码段(PHP 8.x 可运行;请求参数进页面的最小样例,体现「代码内嵌 HTML、世界即请求」):

```php
<?php
$name = $_GET["name"] ?? "访客";
$now  = date("Y-m-d H:i");
?>
<h1>你好，<?= htmlspecialchars($name) ?>，现在是 <?= $now ?></h1>
```

- 配图 1:asset/php搞笑漫画.jpg(「以后禁止 AI 挖洞!」会议室漫画)→「一些论点」AI 段后
- 配图 2:asset/1024.jpg(1024 程序员节贺图)→ 结尾段,呼应发稿日 10-24

## 批判性素材(避免自嗨)

- 对立观点:部署文化与升级债务——「随便一个虚拟主机都能跑」带来铺量,也带来大批停在停维护版本上的站点;「能跑就别动」在内核漏洞面前是负资产
- 反例或边界:临时缓解手段只能缩暴露面不能根除;World Quest 这类老基础设施无路可走;弱类型、参数顺序等老槽点哲学版已写,本期不复用
- 作者表态点:站升级派——跟小版本走的当晚升完重启完事,养祖传 7.4 的早该动身(已入正文)

## 钩子草稿(50–80 字)

- 本版此前无存稿;避开哲学版近两期开场(第 8 期格言、第 11 期哲学版具体问题)→ 用「一个时刻」切入
- 草稿(约 67 字):「10 月 21 日晚,两个内核漏洞的补丁提前落地,全球管理员只分到不到 24 小时。出事的不是某一家公司的应用:能查明服务端语言的网站,近七成跑着同一个东西。」

## 与用户素材的出入记录(工作流第 5 步)

1. CVSS 评分:泄露者曾传 10.0,PHP 官方澄清其评分为 9.2——正文采用官方口径 9.2(The Hacker News)
2. 第二款永久停服游戏:用户素材作《Please Save My Pandemonium!》(僕の魔界を救って!),英文信源多作「Save My Demonic World」,应为同一游戏的不同英译——正文只写《World Quest》,规避歧义
3. 「攻击者 10-16 开始扫描」未能在检索中独立交叉,可交叉的是 Cloudflare「早期利用尝试」——正文未写 10-16 日期
4. 事件成因(第一漏洞 OOM 内存损坏、第二漏洞跨请求 UAF)与 ASLR/ARM64 细节来自用户素材,与厂商技术文方向一致;正文仅采用跨请求 UAF 一项
5. 漏洞发现方「安全公司 Calif + Wiz,模型 GPT-5.6 Sol」:用户素材与聚合报道相符,但未及一手公告——正文以「安全研究员拿 AI 模型审计」间接表述,不写公司与模型名
