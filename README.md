# Awesome-Mobile-Visual-Regression-Testing

# Awesome Mobile Visual Regression Testing

> A curated list of top Mobile Visual Regression Testing platforms — both SaaS/Hosted commercial solutions and open-source alternatives for catching unintended UI changes in native Android and iOS applications.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Applitools Eyes](#applitools-eyes)
  - [BrowserStack Percy](#browserstack-percy)
  - [Sauce Labs Visual Testing](#sauce-labs-visual-testing)
  - [LambdaTest SmartUI](#lambdatest-smartui)
- [Open-Source Software](#-open-source-software)
  - [Visual Regression Tracker](#visual-regression-tracker)
  - [Argos](#argos)
  - [reg-suit](#reg-suit)
  - [dánwò](#dánwò)
  - [Yewo](#yewo)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Mobile Visual Regression Testing platforms. These are not open-source but are included as reference points for feature comparison.

### Applitools Eyes
**Type:** AI-powered visual validation across web and mobile
Applitools is widely recognized as the most capable visual testing tool, with its **Visual AI** engine that understands page structure and ignores rendering noise like anti-aliasing and font rendering, resulting in the fewest false positives among commercial platforms [citation:5]. For mobile, Applitools supports native Android and iOS apps, but it **requires Appium underneath** — meaning you inherit Appium's selector fragility alongside the per-checkpoint cost [citation:5]. Pricing starts at **$399/month for 1,000 validations**, with enterprise contracts running $10K–$30K+ annually [citation:5].
**Best for:** Enterprises needing the most accurate visual AI with the fewest false positives, accepting Appium dependency for mobile and premium checkpoint-based pricing.

### BrowserStack Percy
**Type:** Managed visual testing with native mobile support
Percy (BrowserStack) provides managed visual review across CI and native mobile, with BrowserStack documenting support for native mobile applications alongside desktop and real-mobile browsers [citation:11]. It uses DOM snapshot rendering for web (more stable than raw pixel capture) and integrates with Playwright, Cypress, Selenium, and Storybook [citation:5]. The free tier includes **5,000 screenshots/month with unlimited users**, with paid plans charging per screenshot ($0.01 desktop, $0.02 desktop plus mobile web) — pricing that is more predictable than Applitools' checkpoint model [citation:5].
**Best for:** Teams wanting managed visual review across web and native mobile with transparent per-screenshot pricing and strong CI/CD integration.

### Sauce Labs Visual Testing
**Type:** Visual testing within Sauce Labs device cloud
Sauce Labs provides visual testing integrated into its virtual and real device cloud, with snapshot allowances on entry tiers and smart hybrid diff capabilities. It is positioned for teams already using Sauce Labs for cross-browser and mobile testing who want visual regression in the same platform.

### LambdaTest SmartUI
**Type:** Visual regression with Figma and Storybook support
SmartUI by LambdaTest captures screenshots, compares against approved baselines, and uses Visual AI to filter pixel noise. It works with Playwright, Selenium, and Cypress, and can test Figma designs and Storybook screenshots directly. Positioned for teams wanting visual testing alongside LambdaTest's cross-browser cloud.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Mobile Visual Regression Testing tools. The open-source ecosystem spans **full self-hosted visual testing platforms**, **CLI-based snapshot testing**, **AI-native test frameworks**, and **vision-model test agents**.

### Visual Regression Tracker
**Stack:** Node.js / TypeScript / PostgreSQL / Docker | **License:** MIT
Visual Regression Tracker is the most established open-source, self-hosted solution for visual testing and managing results [citation:3][citation:4]. Its critical feature for mobile is **platform independence**: it works with web, mobile, and desktop — "as long as you could make a screenshot" [citation:3][citation:4]. This means you can capture screenshots from Appium, Espresso, or XCUITest and feed them into the tracker for pixel-by-pixel comparison against accepted baselines. Key features include:
- **Automation framework independent**: integrate with any existing tool
- **Baseline history**: track how baseline images changed over time
- **Ignore regions**: improve stability by ignoring unimportant or uncontrollable parts of images
- **Language support**: JS, Java, Python, .NET, or any other via REST API
- **Multiple comparison providers**: Pixelmatch (default), Looks-Same (perceptual), Odiff (layout detection), and **VLM (Vision Language Model)** for AI-powered human-noticeability analysis
- **Docker deployment**: everything inside Docker images, with a quick setup script for Linux/macOS/WSL

**Critical configuration note:** The `JWT_SECRET` in `.env` must be set to a random value, or the API will not start [citation:3][citation:4].
**Best for:** Teams wanting a proven, self-hosted visual testing platform that accepts screenshots from any mobile automation framework, with multiple comparison algorithms including AI-based noticeability analysis.

### Argos
**Stack:** TypeScript / Node.js | **License:** MIT
Argos is an open-source visual testing platform explicitly positioned for **teams and AI agents**, with the tagline "Review the product, not just the code" [citation:1][citation:7]. It is a direct alternative to Percy, with GitHub topics including `percy-alternative`, `visual-regression`, and `visual-testing` [citation:1]. The platform is MIT-licensed and under active development (last updated August 2026) [citation:13]. For mobile, Argos can accept screenshots from any source, including Appium or native test frameworks, and diff them against baselines with a review workflow.
**Best for:** Teams wanting an MIT-licensed, actively maintained Percy alternative with a focus on review workflows and AI agent integration, accepting that it is a general visual testing platform rather than mobile-specific.

### reg-suit
**Stack:** Node.js / CLI | **License:** MIT
reg-suit is a command-line visual regression testing tool inspired by snapshot testing, with a plugin architecture for integration [citation:2][citation:8]. It compares current images against previous images, creates an HTML report of differences, and stores snapshots in external cloud storage (AWS S3, Google Cloud Storage) [citation:2]. Plugins include Git-hash-based key generation, S3/GCS publishing, and notifications to GitHub, GitLab, Slack, and Chatwork [citation:2][citation:8]. For mobile, reg-suit is **framework-agnostic** — you provide the screenshot images from any source, and it handles the comparison and reporting.
**Best for:** Teams wanting a lightweight, plugin-driven CLI for visual regression that integrates into any CI pipeline, accepting that screenshot capture must be handled separately.

### dánwò
**Stack:** Node.js / TypeScript | **License:** Open Source
dánwò is an open-source end-to-end testing framework for web and mobile apps that includes **screenshot comparison** as a built-in feature [citation:6]. It runs on Android emulators and iOS Simulators (plus native SwiftUI, Jetpack Compose, and Flutter apps), with plain-English agent steps that replay without model calls after the first run [citation:6]. The screenshot assertion (`await expect(screen).toHaveScreenshot(...)`) provides visual regression capability within the test flow, eliminating the need for a separate visual testing tool. It also includes a backend layer with emulated providers (Stripe, Clerk, Resend) and fault injection for testing payment and email flows [citation:6].
**Best for:** Teams wanting an integrated E2E testing framework with built-in mobile screenshot comparison and AI-assisted test authoring, accepting a newer, comprehensive framework.

### Yewo
**Stack:** Python / Appium | **License:** Open Source (alpha)
Yewo is an AI testing agent for Android and iOS apps that uses **visual models to identify controls and locate where to tap**, eliminating dependence on accessibility IDs, test IDs, or other app-specific selectors [citation:12]. It runs plain-language goals against Android and iOS builds, discovers the journey, generates evidence-grounded test scenarios, and executes them with independent auditing [citation:12]. While primarily an AI test agent rather than a pure visual regression tool, its vision-based approach inherently detects visual anomalies. **Important status:** Yewo is explicitly **alpha software** — expect breaking changes while its public interface is established [citation:12].
**Best for:** Teams wanting to explore AI-agent-driven mobile testing that operates on visual screenshots without selectors, accepting alpha-stage maturity.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Mobile Support | Comparison Method | Self-Hosted | Best For |
|----------|---------|-------|----------------|-------------------|-------------|----------|
| **Applitools Eyes** | Proprietary | Cloud | ✅ Via Appium | Visual AI | ❌ | Fewest false positives |
| **BrowserStack Percy** | Proprietary | Cloud | ✅ Native | DOM snapshot + pixel | ❌ | Managed web + mobile |
| **Sauce Labs Visual** | Proprietary | Cloud | ✅ Device cloud | Smart hybrid diff | ❌ | Sauce Labs users |
| **Visual Regression Tracker** | MIT | Node.js/Postgres | ✅ Any screenshot | Pixelmatch/Looks-Same/Odiff/VLM | ✅ | Self-hosted + any framework |
| **Argos** | MIT | TypeScript/Node | (Screenshot input) | Visual diff | ✅ | Percy alternative + AI agents |
| **reg-suit** | MIT | Node.js/CLI | (Screenshot input) | Pixel diff | ✅ (CLI) | Lightweight CI integration |
| **dánwò** | Open Source | Node.js/TS | ✅ Emulator/Simulator | Built-in screenshot | ✅ | Integrated E2E + visual |
| **Yewo** | Open Source (alpha) | Python/Appium | ✅ Android/iOS | Vision model | ✅ | AI agent without selectors |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Mobile Visual Regression Testing tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

**Note on the open-source ecosystem:** Mobile visual regression testing is a **gap in the open-source landscape** compared to web testing. The commercial tools (Applitools, Percy) dominate, but both have mobile caveats: Applitools requires Appium underneath, inheriting selector fragility [citation:5], and Percy's mobile support, while documented, is an extension of its web-focused DOM snapshot model [citation:11]. On the open-source side, **Visual Regression Tracker** is the most complete self-hosted option, explicitly designed to be **platform independent** — it accepts screenshots from any mobile framework (Appium, Espresso, XCUITest) and offers multiple comparison algorithms including a Vision Language Model for human-noticeability analysis [citation:3][citation:4]. **Argos** is the strongest MIT-licensed Percy alternative with active development and AI agent integration [citation:1][citation:13]. **reg-suit** provides a lightweight CLI approach for teams already comfortable with screenshot capture pipelines [citation:2]. **dánwò** represents a newer integrated approach, bundling screenshot comparison directly into an E2E framework that runs on emulators and simulators [citation:6]. No open-source project fully replicates Applitools' Visual AI accuracy for mobile, but Visual Regression Tracker covers the core self-hosted workflow comprehensively.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
