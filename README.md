<h1 align="center">mirunamu</h1>

<p align="center">
  Software Engineer · Frontend lead<br/>
  <sub>Real-time visualization and web architecture — and the native and infrastructure layers underneath.</sub>
</p>

<p align="center">
  <a href="https://www.npmjs.com/org/mirunamu"><img src="https://img.shields.io/badge/npm-mirunamu-007acc?style=flat-square&logo=npm&logoColor=white" alt="npm" /></a>
  <a href="https://www.npmjs.com/~mirunamu"><img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fnpm-dl-badge.vercel.app%2Fapi%2Fdownloads&style=flat-square" alt="npm downloads" /></a>
  <a href="https://docs.mirunamu.info"><img src="https://img.shields.io/badge/blog-docs.mirunamu.info-007acc?style=flat-square&logo=readthedocs&logoColor=white" alt="blog" /></a>
  <a href="https://www.twolinecloud.com"><img src="https://img.shields.io/badge/company-Twolinecloud-007acc?style=flat-square&logo=googlechrome&logoColor=white" alt="company" /></a>
  <img src="https://komarev.com/ghpvc/?username=mirunamu00&color=007acc&style=flat-square&label=Profile+views" alt="views" />
</p>

---

### 👋 About

I lead the frontend of a real-time power-equipment monitoring platform: sensor streams from many kinds of diagnostic devices, rendered live. I care about finding the bottleneck with a profiler before touching code, and about the groundwork that keeps a codebase healthy — tests, monorepos, CI/CD, and the Kubernetes it all runs on.

I studied satellite systems, remote sensing, and GIS. When a field needs something I haven't used at work, I build a real, usable project with it.

I work with AI coding agents every day, under design docs, review gates, and tests that I define.

---

### 🚀 What I'm building

- **Dark Vessel Watch** &nbsp;·&nbsp; Maritime surveillance on real Sentinel-1 SAR imagery: a **C++17 + GDAL** engine detects ships (calibration, land mask, CA-CFAR), detections are matched against AIS to surface vessels sailing without AIS, and analysts review them on a **CesiumJS** 3D globe. Jobs run on a lease-based queue that survives worker crashes, with one OpenTelemetry trace per job. Decisions are recorded as ADRs and every performance change ships with before/after numbers (detection 3.6–4.8× faster after profiling). &nbsp;·&nbsp; _in active development_
- **KubeLantern** &nbsp;·&nbsp; A keyboard-driven desktop client that keeps up to 32 Kubernetes clusters connected in one window. Logs from up to 30 containers are merged into one timeline by a native Rust engine, and secrets are compared inside the backend so no value ever reaches the UI. Local-only — no account, no telemetry. Built with **Tauri 2 (Rust) + React**. &nbsp;·&nbsp; _first release coming soon at kubelantern.com_
- **[Pigment](https://github.com/mirunamu00/pigment)** &nbsp;·&nbsp; _Give your agent a palette, not a prompt._ A gallery of versioned, agent-ready design systems: pick one, hand your coding agent (Claude Code, Codex, Cursor, any MCP client) a version-pinned prompt, and every screen it builds follows the same measured tokens and rules — served as `agent.md`, `tokens.css/json`, an HTTP API, and an MCP server. Each system comes out of a reproducible harness that captures a reference site, has an agent apply it to six apps (four base apps plus a landing page and a docs site), and gates it on builds, smoke tests, accessibility, and an independent critic review before publishing. Built with **Next.js + TypeScript (MCP)** &nbsp;→&nbsp; [pigmentui.com](https://pigmentui.com) · [npm](https://www.npmjs.com/package/pigment-mcp)
- **[@mirunamu/next-redis-cache](https://github.com/mirunamu00/next-redis-cache)** &nbsp;·&nbsp; When Next.js runs as several pods on Kubernetes, each pod keeps its own cache: `revalidateTag` only reaches the pod that served the request, and new pods start cold. No Redis handler supported both of Next.js 16's cache interfaces at the time, so I built one — ISR `cacheHandler` and `"use cache"` `cacheHandlers` with shared tag invalidation. 2.0 reproduced 15 defects as failing tests first, keeps serving build output through Redis outages (timeouts, circuit breaker), and cut Redis memory per build by 88%. Runs in production on my homelab &nbsp;→&nbsp; [npm](https://www.npmjs.com/package/@mirunamu/next-redis-cache)
- **[usefy](https://github.com/mirunamu00/usefy)** &nbsp;·&nbsp; 80+ independently published React hooks and UI packages under the `@usefy` npm org — including a QR encoder/decoder with Reed–Solomon, a linear-space Myers diff viewer, and a virtualized JSON viewer &nbsp;→&nbsp; [usefy-web.vercel.app](https://usefy-web.vercel.app)
- **k3s homelab** &nbsp;·&nbsp; A self-hosted Kubernetes cluster driven entirely by GitOps (ArgoCD, Helm, cert-manager, Longhorn, Prometheus/Grafana). Once traced intermittent probe timeouts through four wrong diagnoses to a router firmware bug dropping VXLAN packets.

---

### 💼 Experience

Software Engineer at **[Twolinecloud](https://www.twolinecloud.com)** · 2022 – present

- **Real-time power-equipment monitoring platform** · _frontend lead, 2024 – present_ — Main developer and architecture owner of a platform that streams sensor data from 8+ kinds of diagnostic equipment.
  - Profiled the live diagnostics screen and redesigned its data path instead of swapping the chart library: **+42% fps** (35.1 → 49.8), 69% fewer frames over 50 ms.
  - Rendered a 15,000-cell heatmap as a single bitmap (**44.8 → 2.84 ms** per tick) and built a shared frame scheduler that took 3D chart updates from about 5 to 21–46 per second at 56–59 fps.
  - Designed the WebSocket layer: one socket per URL, reference-counted subscriptions, ZSTD decompression, frame-batched updates.
  - Led a no-code editor (ReactFlow) where operators build monitoring screens, plus the renderer that binds them to live data.
  - Merged five frontend repos into one monorepo with full history, packaged a shared UI library, and rebuilt CI/CD on GitOps.
  - Built an MCP server that lets AI agents author those screens safely (35 tools, every write approved by a person first).
  &nbsp;`React` `TypeScript` `ReactFlow` `ECharts / WebGL` `WebSocket`
- **Power-equipment diagnostics system for a client delivery** · _sole frontend developer_ — Ten screens covering risk matrices, reliability charts, and a large editable grid, with 1,288 unit tests and 176 Playwright scenarios. Delivered into the client's air-gapped network. &nbsp;`React` `TypeScript` `Playwright`
- **Cloud & MLOps infrastructure platform** — Cluster monitoring, MLOps model management, and the admin console for a multi-cloud Kubernetes platform. &nbsp;`Angular` `Vue` `TypeScript`
- **Collaborative Event Storming tool** — A real-time domain-modeling whiteboard where GPT output streams into the diagram as it is generated. &nbsp;`TypeScript` `WebSocket` `OpenAI`
- **Data analytics & ML platform** · _first project_ — Maintenance and feature work on a no-code platform for data preprocessing and machine-learning pipelines, built around a GoJS workflow editor. &nbsp;`Vue` `TypeScript` `GoJS`

---

### 🎓 Education

- **Kyungpook National University** — B.S., Aerospace and Satellite Systems (융복합시스템공학부 항공위성시스템전공) · remote sensing, satellite image processing, 3D GIS, WebGIS

---

### 📜 Certifications

![Microsoft Certified: Azure Administrator Associate (AZ-104)](https://img.shields.io/badge/Microsoft_Certified-Azure_Administrator_Associate_(AZ--104)-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

---

### 🛠 Tech

**Frontend & Visualization**

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-149ECA?style=flat-square&logo=react&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)
![Vue](https://img.shields.io/badge/Vue-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white)
![ReactFlow](https://img.shields.io/badge/React_Flow-FF4154?style=flat-square&logo=reactflow&logoColor=white)
![ECharts](https://img.shields.io/badge/ECharts-AA344D?style=flat-square&logo=apacheecharts&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-990000?style=flat-square&logo=webgl&logoColor=white)
![Cesium](https://img.shields.io/badge/CesiumJS-6CADDF?style=flat-square&logo=cesium&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)

**Native, Geo & Backend**

![C++](https://img.shields.io/badge/C++17-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![GDAL](https://img.shields.io/badge/GDAL-5CAE58?style=flat-square&logo=osgeo&logoColor=white)
![PostGIS](https://img.shields.io/badge/PostGIS-336791?style=flat-square&logo=postgresql&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)
![Tauri](https://img.shields.io/badge/Tauri-24C8DB?style=flat-square&logo=tauri&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-5FA04E?style=flat-square&logo=nodedotjs&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)
![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=flat-square&logo=socketdotio&logoColor=white)

**Infra & DevOps**

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![k3s](https://img.shields.io/badge/k3s-FFC61C?style=flat-square&logo=k3s&logoColor=black)
![ArgoCD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-000000?style=flat-square&logo=opentelemetry&logoColor=white)
![Ceph](https://img.shields.io/badge/Ceph-EF5C55?style=flat-square&logo=ceph&logoColor=white)

---

<div align="center">
  <img height="165" src="https://github-readme-stats-jade-iota-23.vercel.app/api?username=mirunamu00&show_icons=true&hide_border=true&count_private=true&include_all_commits=true&title_color=007acc&icon_color=007acc&text_color=768390&bg_color=00000000" alt="stats" />
  <img height="165" src="https://github-readme-stats-jade-iota-23.vercel.app/api/top-langs/?username=mirunamu00&layout=compact&hide_border=true&langs_count=8&title_color=007acc&text_color=768390&bg_color=00000000" alt="top langs" />
</div>

<div align="center">
  <img src="https://streak-stats.demolab.com?user=mirunamu00&hide_border=true&background=00000000&ring=007acc&fire=007acc&currStreakLabel=007acc&sideLabels=768390&dates=768390&currStreakNum=768390&sideNums=768390" alt="streak" />
</div>

<p align="center">
  <sub>📍 Seoul, Republic of Korea &nbsp;·&nbsp; Building at <a href="https://www.twolinecloud.com">Twolinecloud</a></sub>
</p>
