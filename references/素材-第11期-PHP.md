# 素材卡 · 第 11 期 PHP

(工作流第 2 步产物,按 `references/素材收集模板.md` 填写;查不到的条目写「暂缺」,不编造。)

## 基本信息

- 期数:第 11 期(用户指定;索引此前最大期数为第 8 期,第 9–10 期待补登)
- 主题语言:PHP
- 哲学面一句话:实用主义——先把问题解决了,优雅可以慢慢补;工具的最高美德是把事办了
- 客串语言及连接点:Perl——PHP 诞生的直接动因就是顶替一摞 Perl CGI 脚本(Rasmus 原本用 Perl 统计简历访客,嫌每次请求都拉起整套环境又慢又吵,才用 C 重写);`$` 开头的变量名也是从 Perl 学来的

## 方向一:梗、绰号与社区声音

- 绰号或梗:「PHP 是世界上最好的语言」——中文技术论坛(贴吧、V2EX、微博等)2010 年代流行,反讽用法居多,常用于引战
- 真实吐槽:①「PHP is a fractal of bad design」——博主 Eevee,博客文章《PHP: a fractal of bad design》,2012-04-09,eev.ee,细数数百条设计矛盾;②经典吐槽点:函数参数顺序不统一,`strpos($haystack, $needle)` 与 `in_array($needle, $haystack)` 方向相反
- 可写进文章的点:分形檄文 + 参数顺序例子(已进正文);中文反讽梗(已进正文)

## 方向二:哲学面与类比

- 哲学面:Rasmus 自述讨厌编程、喜欢解决问题,PHP 是省事的工具,不是艺术品
- 术语及白话解释:①CGI——让网页服务器调用外部程序来生成页面的老规矩;②弱类型——字符串当数字使、数字当字符串使,语言会悄悄替你换算
- 类比候选:牙刷(Rasmus 本人在 SitePoint 访谈中的类比,出自语言自己的世界);地基、发动机(行文少量比喻)

## 方向三:名言与硬细节

- 名言 1:「I actually hate programming, but I love solving problems.」——Rasmus Lerdorf,Siliconrepublic 访谈《Rasmus Lerdorf, father of PHP: Programming is boring》,2016-01-13
- 名言 2:「PHP is about as exciting as your toothbrush. You use it every day, it does the job, it is a simple tool, so what? Who would want to read about toothbrushes?」——Rasmus Lerdorf,SitePoint 访谈《PHP's Creator, Rasmus Lerdorf》(https://www.sitepoint.com/phps-creator-rasmus-lerdorf)
- 名言 3(吐槽):「PHP is a fractal of bad design」——Eevee,eev.ee,2012-04-09(https://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design)
- 硬细节:
  1. 1995-06-08,Rasmus 在 Usenet 新闻组 comp.infosystems.www.authoring.cgi 发帖,宣布 "Personal Home Page Tools (PHP Tools) version 1.0" 开放源码,原话称其为 "a set of small tight cgi binaries written in C"(出处:php.net 手册《History of PHP》、Wikipedia PHP 条目)
  2. 1994 年 Rasmus 为统计个人简历访问量先写了 Perl 脚本,后用 C 重写,最初叫 Personal Home Page Tools(出处:php.net《History of PHP》)
  3. 1997 年 Zeev Suraski 与 Andi Gutmans(以色列 Technion 学生)重写解析器;1998 年发布 PHP 3,更名递归缩写 PHP: Hypertext Preprocessor;两人随后创办 Zend 公司(出处:php.net《History of PHP》)
  4. PHP 6(核心 Unicode 化)约 2010 年放弃;因市面上已有《PHP 6》书籍出版,社区投票跳过版本号 6;2015-12-03 发布 PHP 7,官方口径速度约为 PHP 5 的两倍(出处:wiki.php.net/rfc/php6、ma.ttias.be《PHP 6: The Missing Version Number》、php.net/releases/7)
  5. 2020-11-26 发布 PHP 8.0:`0 == "foo"` 由 true 改为 false(RFC《Saner string to number comparisons》,2019 年通过;出处:wiki.php.net/rfc/string_to_number_comparison)
  6. 2025-11-20 发布 PHP 8.5,引入管道操作符 `|>`(出处:php.net/releases/8.5)
  7. W3Techs 2026-10 数据:PHP 占「已知服务端语言」网站的 69.3%(2021 年约 82%),居第一;WordPress 占全部网站 39.6%(出处:w3techs.com/technologies/details/pl-php、w3techs.com/technologies/details/cm-wordpress)
  8. Facebook 早年整站为 PHP,2014 年才另推 Hack 语言(出处:Wikipedia Hack/HHVM 相关条目)

## 代码与配图

- 经典代码段(PHP 8.5 可运行;教材第一课式访客计数器,体现「HTML 内嵌代码 + 变量内插」):

```php
<?php
$hits = (int) file_get_contents("counter.txt") + 1;
file_put_contents("counter.txt", $hits);
echo "你是第 $hits 位访客";
```

(注:counter.txt 不存在时 file_get_contents 会先报一条警告,计数逻辑不受影响,教材式写法如此。)

- 配图灵感 1:1995 年风格个人主页 + 简陋访客计数器 →「写在前面」
- 配图灵感 2:自相似分形螺旋 →「一些论点」,呼应 Eevee 檄文

## 批判性素材(避免自嗨)

- 对立观点:设计不一致(参数顺序、函数命名规则)、历史上安全口碑差(register_globals / magic quotes 时代)、常被嘲「土」
- 反例或边界:实用主义填坑速度慢于骂声——`0 == "foo"` 将就约 25 年才改;strpos 参数顺序至今未改;既有安装基数太大,无法推倒重排
- 作者表态点:偏爱「先跑起来」的实用主义(写小站会直接新建 .php 文件);受不了 strpos 与 in_array 参数方向相反,每次都得查文档

## 钩子草稿(50–80 字)

- 最近两期开场:第 8 期 Rust 以格言引语开场,第 7 期 Clojure 亦以格言引语开场 → 本期改用「从一个具体问题讲起」
- 草稿(约 76 字):「1994 年,一个程序员有个小烦恼:他想知道几个人看过自己挂在网上的简历。为了数清这个数,他写了个小工具。三十多年后,它还在给互联网上大多数网站打工。」
