# Unity Git 配置

## 目的

统一 Unity 项目的 Git 版本控制配置。控制忽略文件与换行符转换，支持不同操作系统下的多人协作。

## 环境

- Unity 2022.3.0f1
- Git 2.41.0

## 要求

- Git 区分大小写
- `.gitignore` 与 `.gitattributes` 必须放在 Unity 项目根目录

## .gitignore

重点不在于规则数量多，https://www.toptal.com/developers/gitignore/api/unity 生成的版本忽略了太多文件，容易导致重要的文件被忽略，例如：`*.unitypackage`。

只需要忽略缓存文件即可：

- 操作系统缓存文件
- Unity 工程缓存文件
- IDE 缓存文件

## .gitattributes

通过此文件配置换行符的自动转换，可以无视 Git 安装时指定的换行符转换的用户配置，从而使项目得到统一管理。

`* -text` 禁用 Git 内部的换行符转换，同时保留 `git diff` 文本差异显示。

### 机器生成的文件

`*.meta` Unity *.meta 所有平台下换行符均为 LF

### 人类编写的文件

统一人类编写的文件的换行符，在编辑器修改文件换行符时可以规避 `git blame` 的结果被污染。

`*.cs` C# 代码统一使用 LF 以规避 Unity `inconsistent line endings` 报错：

> There are inconsistent line endings in the ‘someFileName.cs’ script. Some are Mac OS X (UNIX) and some are Windows.
> This might lead to incorrect line numbers in stacktraces and compiler errors. Unitron and other text editors can fix this using Convert Line Endings menu commands.
>
> - [inconsistent line endings - Unity Engine - Unity Discussions](https://discussions.unity.com/t/inconsistent-line-endings/406793)

## Git LFS

不使用 Git LFS 功能，有需要请自行开启。

## 参考

- [Git - gitattributes Documentation](https://git-scm.com/docs/gitattributes)
- [GitHub - FrankNine/RepoConfig](https://github.com/FrankNine/RepoConfig)
- [Git 自动转换文件换行符 - 狂飙](https://networm.me/2022/05/22/git-eol-conversion/)
