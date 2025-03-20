# 一、使用链接示例
```
https://cdn.jsdelivr.net/gh/ClearMind1/staticAsset@main/image/1726390457934.png
```

# 二、GitHub使用指南
> 来自 https://www.jsdelivr.com/documentation#id-github 介绍
我们推荐在支持npm的项目中使用npm以获得更好的用户体验 - npm包在我们的网站上可搜索，并且包页面会显示其他有用信息，例如描述和主页链接。

## 永久存储保障
我们使用永久S3存储来确保所有文件在以下情况下仍可访问：
- GitHub服务中断
- 仓库被作者删除
- 版本发布被删除

文件仅在首次请求时或S3故障时直接从GitHub获取。

## 路径格式示例
```shell
/gh/user/repo@version/file
```


### 精确版本加载
```shell
/gh/jquery/jquery@3.1.0/dist/jquery.min.js
/gh/jquery/jquery@32b00373b3f42e5cdcb709df53f3b08b7184a944/dist/jquery.min.js
```


### 版本范围加载
（仅支持有效语义化版本）
```shell
/gh/jquery/jquery@3/dist/jquery.min.js
/gh/jquery/jquery@3.1/dist/jquery.min.js
```


> 注意：使用版本范围时，如果请求的文件在新版本中不可用，我们的版本回退功能将保持链接有效，持续从旧版本提供文件而非返回404错误。

### 最新版本加载
（不推荐生产环境使用，若无tag版本则回退到master分支）
```shell
/gh/jquery/jquery@latest/dist/jquery.min.js
/gh/jquery/jquery/dist/jquery.min.js
```


> 重要提示：请求最新版本（相对于"最新主版本"或"最新次版本"）存在风险，因为主版本通常包含破坏性变更。仅在明确知晓后果时使用。

### 自动压缩文件
为任意JS/CSS/SVG文件添加`.min`后缀获取压缩版本（若不存在将自动生成），所有生成文件均包含源映射，适合开发使用：
```shell
/gh/jquery/jquery@3.2.1/src/core.min.js
```


> 注意：大型文件的压缩可能需要数秒，但所有生成文件都会存入永久存储，因此延迟仅出现在前几次请求。

### 目录列表查看
```shell
/gh/jquery/jquery@3.1.0/
/gh/jquery/jquery@3.1.0/dist/
```
