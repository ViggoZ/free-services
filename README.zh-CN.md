# 🚀 面向开发者的免费服务

> **用 $0 构建并发布你的下一个应用，同时准确了解何时会开始产生费用。**

[English README](README.md) · [Tiếng Việt](README.vi.md) · [交互式网站](https://dereknguyen269.github.io/free-services/) · [参与贡献](CONTRIBUTING.md)

这不是一个只罗列链接的工具清单，而是帮助开发者选择免费基础设施的实用指南：

- 可直接复制使用的 **$0 技术栈**。
- 每项服务的**真实免费额度和限制**，而不只是一个“免费”标签。
- 明确说明**何时会遇到瓶颈**，以及下一档方案可能需要多少费用。

> ⚠️ 免费套餐会持续变化。带有 ⏳ 的项目近期尚未重新验证。将服务用于生产环境前，请务必查看供应商的官方价格页面。

> 🌐 完整数据和可搜索版本请访问[交互式网站](https://dereknguyen269.github.io/free-services/)。数据源为 [`data/services.yaml`](data/services.yaml)。

---

## 🧭 按项目类型快速开始

| 你正在构建什么？ | 从这里开始 |
| ---------------- | ---------- |
| SaaS / 创业 MVP | [$0 SaaS 技术栈](#-0-saas-技术栈) |
| AI 应用 | [$0 AI 技术栈](#-0-ai-技术栈) |
| 静态网站 / 文档 | [$0 静态网站技术栈](#-0-静态网站技术栈) |
| API / 后端 | [$0 API 技术栈](#-0-api-技术栈) |
| 移动应用 | [$0 移动应用技术栈](#-0-移动应用技术栈) |
| 个人项目 | [$0 个人项目技术栈](#-0-个人项目技术栈) |
| 开源项目 | [$0 开源技术栈](#-0-开源技术栈) |

完整分类：[托管](README.md#-hosting) · [数据库](README.md#-databases) · [身份认证](README.md#-authentication) · [存储](README.md#-storage) · [邮件](README.md#-email) · [AI](README.md#-ai--llm) · [分析](README.md#-analytics) · [监控](README.md#-monitoring--error-tracking) · [搜索](README.md#-search) · [缓存与队列](README.md#-cache--queues) · [域名、DNS 与 CDN](README.md#-domains-dns--cdn) · [支付](README.md#-payments) · [开发工具](README.md#-developer-tools) · [自托管](README.md#-self-host-only-free-software-not-free-hosting)

---

## 🏷️ 图例

| 标记 | 含义 |
| ---- | ---- |
| 🟢 | 永久免费，不会过期 |
| 🔵 | 免费额度，用完后需要付费 |
| 🟡 | 限时免费试用 |
| 💳 | 需要绑定信用卡 |
| 😴 | 不活跃时休眠或暂停 |
| ⚡ | 有用量或速率限制 |
| 🏠 | 支持自托管 |
| 💰 | 按交易收取费用 |
| ⏳ | 尚未重新验证 |

**“免费”不等于“免费软件”。** Hosted 免费套餐通常不收取平台费用；可自托管的软件虽然可以免费下载，但服务器仍然需要成本。

---

# 🏆 $0 技术栈

以下方案是起点。实际成本取决于流量、存储、计算资源和 API 使用量。

## 🚀 $0 SaaS 技术栈

```text
前端           → Cloudflare Pages（Next.js 也可使用 Vercel，但仅限非商业用途）
后端           → Cloudflare Workers
数据库         → Neon 或 Supabase（Postgres）
身份认证       → Better Auth 或 Supabase Auth
文件存储       → Cloudflare R2
邮件           → Resend
产品分析       → PostHog
监控           → Sentry
支付           → Stripe
DNS / CDN      → Cloudflare
代码与 CI      → GitHub + GitHub Actions
```

**常见瓶颈：** Workers 连接 Postgres 时需要 Hyperdrive 或连接池；Supabase 免费项目长期不活跃后可能暂停；Vercel Hobby 不允许商业使用；密码重置邮件的每日额度可能很快耗尽。

## 🤖 $0 AI 技术栈

```text
前端           → Cloudflare Pages
后端           → Cloudflare Workers
LLM            → Gemini / Groq / Cerebras
Embedding      → Cloudflare Workers AI 或 Gemini
向量数据库     → Supabase pgvector 或 Cloudflare Vectorize
数据库         → Supabase / Neon
邮件           → Resend
分析           → PostHog
监控           → Sentry
```

免费 LLM 套餐通常限制每分钟和每天的请求量，部分供应商可能将免费套餐中的数据用于模型改进。不要发送敏感用户数据；正式上线前应准备备用供应商，例如 Groq → Gemini → OpenRouter。

## 🌐 $0 静态网站技术栈

```text
托管           → Cloudflare Pages / GitHub Pages
DNS            → Cloudflare
分析           → Cloudflare Web Analytics / Umami Cloud
表单           → Tally / Formspree
```

对于小型网站，几乎没有明显瓶颈；大型网站最先遇到的通常是构建次数或构建时间限制。

## 🔌 $0 API 技术栈

```text
运行时         → Cloudflare Workers / Render / Koyeb
数据库         → Neon / Supabase
缓存           → Upstash Redis
监控           → Sentry + UptimeRobot
邮件           → Resend
```

Render 的免费 Web 服务在不活跃时会休眠，冷启动可能需要几十秒；Workers 对每次请求的 CPU 时间有限制。两者适合原型，不适合对延迟敏感的生产 API。

## 📱 $0 移动应用技术栈

```text
应用           → Expo（React Native）或 Flutter
后端与数据库   → Supabase 或 Firebase
身份认证       → Supabase Auth / Firebase Auth
推送           → Firebase Cloud Messaging
存储           → Supabase Storage / Cloudflare R2
崩溃监控       → Sentry / Firebase Crashlytics
```

发布到应用商店的费用通常无法避免：Apple Developer 约 $99/年，Google Play 约 $25 一次性费用。

## 🧑‍💻 $0 个人项目技术栈

```text
托管           → Cloudflare Pages + Workers
数据库         → Turso（SQLite）或 Neon
身份认证       → Better Auth
分析           → Umami Cloud / Cloudflare Web Analytics
可用性监控     → UptimeRobot
```

此方案优先考虑低配置成本，并尽量不要求绑定信用卡，避免遗忘的项目产生意外账单。

## 🐙 $0 开源技术栈

```text
代码与 Issue   → GitHub
CI/CD          → GitHub Actions
文档           → GitHub Pages / Cloudflare Pages
软件包         → npm / GitHub Packages / GHCR
安全           → GitHub code scanning + Dependabot
开发环境       → GitHub Codespaces
社区           → GitHub Discussions
```

许多付费工具会为开源项目提供免费计划。付费前请先查看供应商的开源项目计划。

---

# 📚 主要服务分类

完整的服务清单、限制和验证日期请查看[英文 README](README.md)及 [`data/services.yaml`](data/services.yaml)。主要分类包括：

- **托管：** Cloudflare Pages、Cloudflare Workers、Vercel、Netlify、Render、Koyeb、GitHub Pages、Deno Deploy、Google Cloud Run。
- **数据库：** Supabase、Neon、Prisma Postgres、Aiven、CockroachDB、Nile、Turso、MongoDB Atlas、Firebase。
- **身份认证：** Supabase Auth、Firebase Authentication、Clerk、Auth0、Better Auth、Auth.js。
- **存储：** Cloudflare R2、Supabase Storage、Backblaze B2、Cloudinary。
- **邮件：** Resend、Brevo、Mailgun、Amazon SES、Loops。
- **AI 与 LLM：** Gemini、Groq、Cerebras、Mistral AI、OpenRouter、Hugging Face、GitHub Models、Workers AI。
- **分析与监控：** PostHog、Umami Cloud、Google Analytics、Sentry、Better Stack、UptimeRobot、Grafana Cloud、Telemetry Tracker、SolidPing。
- **搜索、缓存与队列：** Algolia、Tavily、Upstash Redis、Upstash QStash、Cloudflare KV、Cloudflare Queues。
- **开发工具：** GitHub、GitLab、Bitbucket、GitHub Actions、npm、Docker Hub、Codespaces、StackBlitz、CodeSandbox。
- **移动与设计：** Expo、React Native、Flutter、Firebase、Supabase、Figma、Canva、Excalidraw、Lucide。

Meilisearch、Typesense、OpenSearch、GlitchTip、SigNoz、Plausible、Umami、RabbitMQ、Valkey、n8n 和 Appwrite 等项目在自托管分类中列出。自托管软件本身可能免费，但服务器并不免费。

---

# 🆚 免费替代方案

| 常用服务 | 免费替代方案 |
| -------- | ------------ |
| Vercel | Cloudflare Pages、Netlify |
| Supabase | Neon、Firebase、Appwrite（自托管） |
| Firebase | Supabase、Appwrite |
| Redis | Upstash、Valkey（自托管） |
| Sentry | GlitchTip、SigNoz（自托管） |
| Algolia | Meilisearch、Typesense（自托管） |
| AWS | Cloudflare、Render、Koyeb |
| Stripe | Lemon Squeezy、Paddle、Creem |
| OpenAI API | Gemini、Groq、Cerebras、Mistral |
| Google Analytics | PostHog、Umami、Cloudflare Web Analytics |

---

# 💰 $0 创业检查清单

```text
☐ 域名（约 $10/年，不免费）
☐ DNS / CDN
☐ 前端
☐ 后端
☐ 数据库
☐ 身份认证
☐ 文件存储
☐ 邮件
☐ 分析
☐ 错误追踪
☐ 可用性监控
☐ 支付
☐ CI/CD
☐ AI（如果需要）
```

先使用免费套餐，只有在实际限制阻碍项目时才升级。

## ⚠️ 免费不代表无限制

选择服务前，请检查：

- 请求、CPU 和内存限制。
- 存储、带宽和数据库大小。
- 并发连接数，尤其是 serverless + Postgres 场景。
- 构建分钟数和 API 速率限制。
- 休眠行为和冷启动时间。
- 数据保留和备份策略。
- 是否需要信用卡。
- 商业使用限制，例如 Vercel Hobby 的限制。
- 地理区域可用性和免费套餐有效期。

一个服务可以免费，但仍然不适合生产环境。

---

# 🤝 参与贡献

每一行服务都有 **Verified** 列：

- ⏳ 表示尚未重新验证，限制仅供参考。
- 具体日期表示价格页面在该日期经过检查。

新增服务时，它应该拥有真正有用的免费套餐、公开记录的价格和限制、当前仍有效的免费计划，并且与已有项目有所区别。请提供服务名称、分类、URL、免费额度、是否需要信用卡、套餐类型、商业使用规则、休眠或过期行为，以及最近验证日期。完整模板请查看 [CONTRIBUTING.md](CONTRIBUTING.md)。

发现免费套餐已过时？请[提交 Issue](https://github.com/dereknguyen269/free-services/issues)或发起 Pull Request。

---

## 📄 许可证

详情请查看 [LICENSE](LICENSE)。

<p align="center"><strong>构建更多，付费更少，发布更快。🚀</strong></p>
