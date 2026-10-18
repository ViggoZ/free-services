# 🚀 Dịch vụ miễn phí cho lập trình viên

> **Xây dựng và đưa ứng dụng lên môi trường thật với chi phí $0 — đồng thời biết chính xác khi nào bạn sẽ phải trả tiền.**

[English README](README.md) · [Trang web tương tác](https://dereknguyen269.github.io/free-services/) · [Đóng góp](CONTRIBUTING.md)

Đây không chỉ là danh sách các đường link. Repository này tập trung vào:

- Các **stack $0 có thể dùng ngay** cho từng loại dự án.
- **Giới hạn thực tế** của từng dịch vụ, không chỉ một nhãn “free”.
- **Điểm chạm giới hạn**: điều gì sẽ hết trước và khi đó gói tiếp theo có thể tốn bao nhiêu.

> ⚠️ Các gói miễn phí thay đổi thường xuyên. Những dòng có ký hiệu ⏳ chưa được kiểm tra lại gần đây. Hãy luôn xem trang giá chính thức trước khi dùng dịch vụ cho production.

> Bản dữ liệu đầy đủ và có thể tìm kiếm nằm trên [trang web tương tác](https://dereknguyen269.github.io/free-services/). Nguồn dữ liệu là [`data/services.yaml`](data/services.yaml).

---

## 🧭 Chọn nhanh theo loại dự án

| Bạn đang xây dựng gì? | Bắt đầu từ đây |
| --------------------- | -------------- |
| SaaS / MVP startup | [Stack SaaS $0](#-stack-saas-0) |
| Ứng dụng AI | [Stack AI $0](#-stack-ai-0) |
| Website tĩnh / tài liệu | [Stack website tĩnh $0](#-stack-website-tĩnh-0) |
| API / backend | [Stack API $0](#-stack-api-0) |
| Ứng dụng mobile | [Stack mobile $0](#-stack-mobile-0) |
| Dự án cá nhân | [Stack side project $0](#-stack-side-project-0) |
| Dự án mã nguồn mở | [Stack open source $0](#-stack-open-source-0) |

Danh mục đầy đủ: [Hosting](README.md#-hosting) · [Cơ sở dữ liệu](README.md#-databases) · [Xác thực](README.md#-authentication) · [Lưu trữ](README.md#-storage) · [Email](README.md#-email) · [AI](README.md#-ai--llm) · [Analytics](README.md#-analytics) · [Monitoring](README.md#-monitoring--error-tracking) · [Search](README.md#-search) · [Cache & Queue](README.md#-cache--queues) · [Domain & DNS](README.md#-domains-dns--cdn) · [Thanh toán](README.md#-payments) · [Công cụ phát triển](README.md#-developer-tools) · [Tự host](README.md#-self-host-only-free-software-not-free-hosting)

---

## 🏷️ Chú giải

| Ký hiệu | Ý nghĩa |
| ------- | ------- |
| 🟢 | Miễn phí vĩnh viễn, không hết hạn |
| 🔵 | Có credit miễn phí, sẽ dùng hết |
| 🟡 | Dùng thử miễn phí, có thời hạn |
| 💳 | Bắt buộc thêm thẻ thanh toán |
| 😴 | Ngủ / tạm dừng khi không hoạt động |
| ⚡ | Có giới hạn sử dụng hoặc tốc độ |
| 🏠 | Có thể tự host |
| 💰 | Có phí trên mỗi giao dịch |
| ⏳ | Chưa được kiểm tra lại gần đây |

**“Miễn phí” không đồng nghĩa với “phần mềm miễn phí”.** Gói hosted miễn phí không tính tiền trực tiếp; dự án có thể self-host thì miễn phí để tải về nhưng bạn vẫn phải trả tiền máy chủ.

---

# 🏆 Các stack $0

Các stack dưới đây là điểm bắt đầu. Chi phí thực tế còn phụ thuộc vào traffic, dung lượng lưu trữ, compute và số lần gọi API.

## 🚀 Stack SaaS $0

```text
Frontend       → Cloudflare Pages (hoặc Vercel cho Next.js, chỉ phi thương mại)
Backend        → Cloudflare Workers
Database       → Neon hoặc Supabase (Postgres)
Auth           → Better Auth hoặc Supabase Auth
Storage        → Cloudflare R2
Email          → Resend
Analytics      → PostHog
Monitoring     → Sentry
Payments       → Stripe
DNS / CDN      → Cloudflare
Code + CI      → GitHub + GitHub Actions
```

**Điểm sẽ chạm giới hạn:** Workers kết nối Postgres cần Hyperdrive hoặc connection pool; dự án Supabase miễn phí có thể tạm dừng sau thời gian không hoạt động; Vercel Hobby không dành cho SaaS thương mại; email reset mật khẩu có thể nhanh chóng chạm giới hạn gửi hằng ngày.

## 🤖 Stack AI $0

```text
Frontend       → Cloudflare Pages
Backend        → Cloudflare Workers
LLM            → Gemini / Groq / Cerebras
Embeddings     → Cloudflare Workers AI hoặc Gemini
Vector DB      → Supabase pgvector hoặc Cloudflare Vectorize
Database       → Supabase / Neon
Email          → Resend
Analytics      → PostHog
Monitoring     → Sentry
```

Các gói LLM miễn phí thường giới hạn request/phút và request/ngày. Một số nhà cung cấp có thể dùng dữ liệu ở tier miễn phí để cải thiện mô hình. Không gửi dữ liệu nhạy cảm; nên chuẩn bị fallback như Groq → Gemini → OpenRouter trước khi phát hành.

## 🌐 Stack website tĩnh $0

```text
Hosting        → Cloudflare Pages / GitHub Pages
DNS            → Cloudflare
Analytics      → Cloudflare Web Analytics / Umami Cloud
Forms          → Tally / Formspree
```

Với website nhỏ, giới hạn build thường là vấn đề đầu tiên bạn gặp; hosting và bandwidth thường đủ dùng.

## 🔌 Stack API $0

```text
Runtime        → Cloudflare Workers / Render / Koyeb
Database       → Neon / Supabase
Cache          → Upstash Redis
Monitoring     → Sentry + UptimeRobot
Email          → Resend
```

Render có thể “ngủ” khi không có traffic và cold start khá lâu. Workers có giới hạn CPU trên mỗi request. Cả hai phù hợp cho prototype hơn là API production nhạy với độ trễ.

## 📱 Stack mobile $0

```text
App            → Expo (React Native) hoặc Flutter
Backend + DB   → Supabase hoặc Firebase
Auth           → Supabase Auth / Firebase Auth
Push           → Firebase Cloud Messaging
Storage        → Supabase Storage / Cloudflare R2
Crash reports  → Sentry / Firebase Crashlytics
```

Chi phí khó tránh nhất là phí đưa app lên store: Apple Developer khoảng $99/năm và Google Play khoảng $25 một lần.

## 🧑‍💻 Stack side project $0

```text
Hosting        → Cloudflare Pages + Workers
Database       → Turso (SQLite) hoặc Neon
Auth           → Better Auth
Analytics      → Umami Cloud / Cloudflare Web Analytics
Uptime         → UptimeRobot
```

Stack này ưu tiên ít công sức cài đặt và không phải lưu thẻ thanh toán, để dự án bỏ quên không gây ra hóa đơn bất ngờ.

## 🐙 Stack open source $0

```text
Code + Issues  → GitHub
CI/CD          → GitHub Actions
Docs           → GitHub Pages / Cloudflare Pages
Packages       → npm / GitHub Packages / GHCR
Security       → GitHub code scanning + Dependabot
Dev env        → GitHub Codespaces
Community      → GitHub Discussions
```

Nhiều dịch vụ trả phí có chương trình miễn phí cho dự án mã nguồn mở. Hãy kiểm tra chương trình open-source của từng nhà cung cấp trước khi thanh toán.

---

# 📚 Danh mục nổi bật

Danh sách đầy đủ, giới hạn mới nhất và ngày xác minh được duy trì trong [README tiếng Anh](README.md) và [file dữ liệu YAML](data/services.yaml). Một số nhóm dịch vụ chính:

- **Hosting:** Cloudflare Pages, Cloudflare Workers, Vercel, Netlify, Render, Koyeb, GitHub Pages, Deno Deploy, Google Cloud Run.
- **Database:** Supabase, Neon, Prisma Postgres, Aiven, CockroachDB, Nile, Turso, MongoDB Atlas, Firebase.
- **Authentication:** Supabase Auth, Firebase Authentication, Clerk, Auth0, Better Auth, Auth.js.
- **Storage:** Cloudflare R2, Supabase Storage, Backblaze B2, Cloudinary.
- **Email:** Resend, Brevo, Mailgun, Amazon SES, Loops.
- **AI & LLM:** Gemini, Groq, Cerebras, Mistral AI, OpenRouter, Hugging Face, GitHub Models, Workers AI.
- **Analytics:** PostHog, Umami Cloud, Google Analytics, Cloudflare Web Analytics.
- **Monitoring:** Sentry, Better Stack, UptimeRobot, Grafana Cloud, Telemetry Tracker, SolidPing.
- **Search / cache / queue:** Algolia, Tavily, Upstash Redis, Upstash QStash, Cloudflare KV, Cloudflare Queues.
- **Công cụ phát triển:** GitHub, GitLab, Bitbucket, GitHub Actions, npm, Docker Hub, Codespaces, StackBlitz, CodeSandbox.
- **Mobile và design:** Expo, React Native, Flutter, Firebase, Supabase, Figma, Canva, Excalidraw, Lucide.

Các dự án như Meilisearch, Typesense, OpenSearch, GlitchTip, SigNoz, Plausible, Umami, RabbitMQ, Valkey, n8n và Appwrite được liệt kê ở nhóm **self-host** khi phiên bản hosted không có gói miễn phí lâu dài. Self-host không có nghĩa là miễn phí máy chủ.

---

# 🆚 Một số lựa chọn thay thế miễn phí

| Dịch vụ phổ biến | Lựa chọn thay thế |
| ---------------- | ----------------- |
| Vercel | Cloudflare Pages, Netlify |
| Supabase | Neon, Firebase, Appwrite (self-host) |
| Firebase | Supabase, Appwrite |
| Redis | Upstash, Valkey (self-host) |
| Sentry | GlitchTip, SigNoz (self-host) |
| Algolia | Meilisearch, Typesense (self-host) |
| AWS | Cloudflare, Render, Koyeb |
| Stripe | Lemon Squeezy, Paddle, Creem |
| OpenAI API | Gemini, Groq, Cerebras, Mistral |
| Google Analytics | PostHog, Umami, Cloudflare Web Analytics |

---

# 💰 Checklist startup $0

```text
☐ Domain (khoảng $10/năm, không miễn phí)
☐ DNS / CDN
☐ Frontend
☐ Backend
☐ Database
☐ Authentication
☐ Lưu trữ file
☐ Email
☐ Analytics
☐ Theo dõi lỗi
☐ Theo dõi uptime
☐ Thanh toán
☐ CI/CD
☐ AI (nếu cần)
```

Hãy bắt đầu bằng các gói miễn phí và chỉ nâng cấp khi một giới hạn thực sự chặn dự án.

## ⚠️ Miễn phí không có nghĩa là không giới hạn

Trước khi chọn dịch vụ, hãy kiểm tra:

- Giới hạn request, CPU và bộ nhớ.
- Dung lượng lưu trữ, bandwidth và kích thước database.
- Số kết nối đồng thời, đặc biệt khi dùng serverless + Postgres.
- Build minutes và giới hạn tốc độ API.
- Cơ chế sleep và cold start.
- Lưu giữ dữ liệu và backup.
- Có bắt buộc thẻ thanh toán hay không.
- Giới hạn sử dụng thương mại, ví dụ Vercel Hobby.
- Khu vực địa lý được hỗ trợ và thời hạn của free tier.

Một dịch vụ có thể miễn phí nhưng vẫn là lựa chọn không phù hợp cho production.

---

# 🤝 Đóng góp

Mỗi dịch vụ được đánh dấu bằng cột **Verified**:

- ⏳ nghĩa là chưa được kiểm tra lại; hãy xem giới hạn là gần đúng.
- Một ngày cụ thể nghĩa là trang giá đã được kiểm tra vào ngày đó.

Muốn thêm hoặc cập nhật dịch vụ? Dịch vụ nên có free tier thực sự hữu ích, giá và giới hạn được công khai, gói miễn phí đang hoạt động và có điểm khác biệt so với các mục hiện có. Hãy kèm URL, giới hạn, yêu cầu thẻ, loại gói, quyền sử dụng thương mại, hành vi sleep/expiry và ngày xác minh. Xem [CONTRIBUTING.md](CONTRIBUTING.md) để biết mẫu đầy đủ.

Phát hiện thông tin đã lỗi thời? [Mở issue](https://github.com/dereknguyen269/free-services/issues) hoặc gửi pull request.

---

## 📄 Giấy phép

Xem [LICENSE](LICENSE) để biết chi tiết.

<p align="center"><strong>Xây dựng nhiều hơn. Trả ít hơn. Phát hành nhanh hơn. 🚀</strong></p>
