# Cloudbypass OpenClaw Skill

穿云API（Cloudbypass API）的OpenClaw技能实现，用于绕过Cloudflare 5秒盾、JavaScript质询、Turnstile验证等反爬虫保护。

## 安装

### 通过 ClawHub 安装（推荐）

```bash
npx clawhub install cloudbypass
```

### 手动安装

```bash
git clone https://github.com/cloudbypass/cloudbypass-skill.git
cd cloudbypass-skill
```

## 配置

### 方式1：环境变量（推荐）

如果配置了环境变量，则无需在OpenClaw中配置：

```bash
# 必填：API密钥（从控制台 https://console.cloudbypass.com/#/ 获取）
export CLOUDBYPASS_APIKEY=your_api_key

# V2模式必填：代理地址
export CLOUDBYPASS_PROXY=http://proxy:port

# 可选：会话分区标识
export CLOUDBYPASS_PART=0

# 可选：Turnstile sitekey
export CLOUDBYPASS_SITEKEY=your_sitekey
```

### 方式2：OpenClaw配置

如果未配置环境变量，可在OpenClaw中配置以下参数：

```json
{
  "apiKey": "your_api_key_here",
  "proxy": "http://proxy:port",  // V2模式需要
  "mode": "v1",  // 或 "v2"
  "timeout": 65000
}
```

## 使用

### 在OpenClaw中使用

```
使用穿云访问 https://etherscan.io/accounts/label/lido，并解析数据为json。
```

## 功能特性

- ✅ **V1模式**：适用于简单请求，自动处理基础验证
- ✅ **V2模式**：支持JS质询和Turnstile验证，需要代理支持
- ✅ **V2 Stream模式**：用于文件下载，支持流式传输，节省内存
- ✅ **零依赖实现**：使用Node.js原生模块，无需安装额外依赖

## 使用场景

- 程序请求返回403，但浏览器能正常打开
- 遇到Cloudflare 5秒盾
- 需要处理JavaScript质询或Turnstile验证
- 需要下载受保护的文件

## 获取API密钥

1. 访问 [穿云控制台](https://console.cloudbypass.com/#/)
2. 注册/登录账号
3. 在控制台中获取API密钥

## 参考资源

- **官网**: https://www.cloudbypass.com/
- **API文档**: https://docs.cloudbypass.com/api-quick-reference.md
- **控制台**: https://console.cloudbypass.com/#/
- **使用教程**: https://www.cloudbypass.com/help/
