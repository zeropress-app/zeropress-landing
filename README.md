# ZeroPress

ZeroPress is a **static-first, file-native CMS** designed for the modern web.  
It focuses on **publishing durable HTML artifacts**, not serving content through runtime APIs.

Built for developers and creators who value performance, reliability, and long-term maintainability — without the operational complexity of legacy CMSs or application-heavy frameworks.

ZeroPress is an alternative to traditional systems like WordPress **and** to API-centric Headless CMSs.

---

## ✨ Key Characteristics

- **Static-first publishing**
  - User-facing pages are generated as **final HTML at publish time**
  - No runtime rendering, no request-time content APIs
- **File-native architecture**
  - Published content lives as files in object storage (Cloudflare R2)
  - HTML, metadata, and sitemap are first-class artifacts
- **Deterministic SEO**
  - Search engines and AI systems consume the same HTML users see
  - No dependency on JavaScript execution
- **Clear system separation**
  - Admin = application
  - User pages = documents
- **Cloudflare-native**
  - Pages for delivery
  - R2 for content storage
  - Workers for interaction (search, comments)
- **AI-assisted workflows**
  - Writing, translation, metadata generation
  - AI is a tool, not a runtime dependency

---

## 🚫 What ZeroPress Is *Not*

To avoid ambiguity:

- ❌ Not a Headless CMS
- ❌ Not an SPA-based publishing system
- ❌ Not request-time SSR
- ❌ Not framework-coupled (Next.js, Nuxt, etc.)

> ZeroPress does not render pages via APIs.  
> ZeroPress **publishes pages as files**.

---

## 🧱 Architecture Overview

```
Admin (Application)
   ↓ publish
R2 (HTML, meta.json, sitemap.xml)
   ↓
Cloudflare Pages (User-facing delivery)
```

- User pages work **without JavaScript**
- APIs and Workers exist only to *support* publishing and interaction
- Content remains accessible even if backend systems fail

---

## 🧠 Why ZeroPress Instead of WordPress?

| Aspect | WordPress | ZeroPress |
|------|-----------|-----------|
| Content storage | Database | Files (HTML + JSON) |
| Rendering | Request-time PHP | Publish-time static HTML |
| Failure mode | White screen / DB errors | HTML still available |
| Plugins | Required for basics | Architecture-level features |
| Security | Continuous patching | Minimal attack surface |
| SEO | Runtime dependent | Deterministic |
| Mental model | Application | Documents |

---

## 🧠 Why ZeroPress Instead of a Headless CMS?

| Aspect | Headless CMS | ZeroPress |
|------|--------------|-----------|
| Content delivery | JSON API | Static HTML files |
| Frontend | Required | Not required |
| SEO | SSR/SSG dependent | Native |
| Runtime dependency | High | None |
| Content survivability | Tied to API | File-based |

---

## 🧩 Client-side JavaScript Policy

ZeroPress enforces a **strict hydration boundary**:

**Allowed**
- Search UI
- Comments
- Theme toggles
- Minor UI enhancements

**Forbidden**
- Client-side rendering of content
- SPA routing
- Re-fetching content for display

> User pages must remain readable as documents, not applications.

(See `ADR-0005`)

---

## 🔍 Search

- Search is implemented via **Cloudflare AutoRAG**
- R2 files are periodically crawled and indexed
- Search runs through Workers
- Search failure never affects page availability

Search is a **feature**, not a dependency.

---

## 🚀 Vision

ZeroPress believes:

> Published content should outlive frameworks, APIs, and runtimes.

Instead of optimizing for developer convenience alone, ZeroPress optimizes for:
- longevity
- debuggability
- operational clarity
- content survivability

---

## 📍 Project Status

ZeroPress is currently in **Alpha**.

- Core architecture is defined
- APIs and tooling are evolving
- Breaking changes may occur

Architectural decisions are documented in:
- `ARCHITECTURE.md`
- `docs/adr/`

---

## 📜 License

ZeroPress is licensed under the **Apache License 2.0**.

This allows:
- Self-hosting
- Commercial use
- Long-term architectural freedom

without forcing SaaS lock-in.

---

## 🌐 Links

- Website: https://zeropress.app  
- Docs: https://docs.zeropress.app  

---

## 🤝 Contributing

ZeroPress welcomes early contributors who value:
- clear architecture
- explicit decisions
- minimal magic

See:
- `CONTRIBUTING.md`
- `GOVERNANCE.md`

---

## 📧 Contact

For collaboration or early access:  
hello@zeropress.org
