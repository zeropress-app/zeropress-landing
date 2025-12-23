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

## 🛠 Enhancement Policy

ZeroPress pages may include optional enhancements — but these must **never regenerate content** or depend on runtime data for core HTML. They exist solely as client-side decorations or interactive helpers. (See ADR-0006)

### Allowed
- Syntax highlighting
- Image lightbox enhancements
- Copy code buttons
- Theme toggles

### Not Allowed
- Client-side content rendering
- SPA navigation
- Re-fetching or rehydrating core content

> User pages must remain readable as documents, not applications.

(See `ADR-0005`)

---

## 🔍 Search

ZeroPress supports **AI-powered search powered by Cloudflare AutoRAG**.  
R2 files are periodically crawled and indexed,  
but **search is a non-critical enhancement only** — it does not affect availability of static pages. (See ADR-0004)

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
- ADR-0001: Static Publish for User Pages  
- ADR-0002: Not a Headless CMS  
- ADR-0003: R2 File Layout  
- ADR-0004: AutoRAG Search Architecture  
- ADR-0005: Client-side Hydration Boundary  
- ADR-0006: Content Enhancement Policy

---

## 📜 License

ZeroPress is licensed under the **Apache License 2.0**.
Apache 2.0 ensures that both individuals and organizations can adopt,
modify, and sustain ZeroPress without legal barriers — aligning with our
commitment to long-lived, framework-independent publishing.

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
