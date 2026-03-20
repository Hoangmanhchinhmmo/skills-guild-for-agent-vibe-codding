# DANH SACH SKILLS & HUONG DAN SU DUNG DANH CHO AI AGENT
## Claude Code Skills Directory — Agent Reference Guide
### Tong so: 961 Skills | Cap nhat: 2026-03-20

---

## MUC LUC

1. [Cach su dung Skills](#1-cach-su-dung-skills)
2. [AI & Agent Development](#2-ai--agent-development)
3. [Backend Development](#3-backend-development)
4. [Frontend Development](#4-frontend-development)
5. [Mobile Development](#5-mobile-development)
6. [Database & Data Engineering](#6-database--data-engineering)
7. [DevOps & Cloud Infrastructure](#7-devops--cloud-infrastructure)
8. [Testing & QA](#8-testing--qa)
9. [Security & Penetration Testing](#9-security--penetration-testing)
10. [API Design & Documentation](#10-api-design--documentation)
11. [Architecture & Design Patterns](#11-architecture--design-patterns)
12. [Programming Languages](#12-programming-languages)
13. [Git & Version Control](#13-git--version-control)
14. [CI/CD & Automation](#14-cicd--automation)
15. [Monitoring & Observability](#15-monitoring--observability)
16. [SEO & Marketing](#16-seo--marketing)
17. [CRM & Business Automation](#17-crm--business-automation)
18. [Document & Office Tools](#18-document--office-tools)
19. [Azure SDK Collection](#19-azure-sdk-collection)
20. [Game Development](#20-game-development)
21. [Blockchain & Web3](#21-blockchain--web3)
22. [Content & Writing](#22-content--writing)
23. [Research & Analysis](#23-research--analysis)
24. [Workflow & Project Management](#24-workflow--project-management)
25. [Specialized Industry Skills](#25-specialized-industry-skills)

---

## 1. CACH SU DUNG SKILLS

### Cú phap goi Skill:
```
/ten-skill                    # Goi truc tiep
/ten-skill [tham-so]          # Goi voi tham so
```

### Nguyen tac cho Agent AI:
1. **Chon skill phu hop voi nhiem vu** — Khong goi skill khong lien quan
2. **Doc mo ta skill truoc khi goi** — Hieu ro pham vi hoat dong
3. **Ket hop nhieu skills** — Mot so skill bo sung cho nhau (vd: `brainstorming` → `writing-plans` → `executing-plans`)
4. **Uu tien skill chuyen biet** hon skill tong quat (vd: `fastapi-pro` thay vi `python-pro` khi lam FastAPI)
5. **Skill automation** yeu cau Composio MCP server — Kiem tra truoc khi goi
6. **Luon xac nhan ket qua** giua cac buoc trong chuoi skill — Khong chay mu

### Phan loai muc do:
- **[CORE]** — Skills co ban, dung thuong xuyen
- **[SPEC]** — Skills chuyen sau cho domain cu the
- **[AUTO]** — Skills tu dong hoa qua MCP/Composio
- **[SEC]** — Skills bao mat — **YEU CAU QUYEN RO RANG** (pentest engagement, CTF, security research)

### Xu ly loi khi goi Skill:

```
Neu skill THAT BAI:
  1. Doc thong bao loi — xac dinh nguyen nhan (skill khong ton tai? thieu dependency? timeout?)
  2. Thu lai 1 lan voi tham so khac
  3. Neu van that bai → Tim skill thay the cung domain (xem bang "Skill tuong tu" ben duoi)
  4. Neu khong co skill thay the → Thuc hien thu cong (khong phu thuoc skill)
  5. Bao cao loi cho user

Neu skill TRA VE KET QUA KHONG HOP LE:
  1. Xac nhan ket qua truoc khi truyen sang buoc tiep
  2. Neu ket qua sai → Chay lai voi prompt cu the hon
  3. Neu van sai → Bypass skill, lam thu cong
```

### Phan biet cac skill tuong tu (Disambiguation):

| Nhom | Skill | Khi nao dung |
|------|-------|-------------|
| **Prompt** | `prompt-engineer` | Toi uu 1 prompt cu the |
| | `prompt-engineering` | Hoc ky thuat prompt tong quat |
| | `prompt-engineering-patterns` | Ap dung pattern nang cao |
| | `prompt-library` | Tim prompt mau co san |
| **Code Review** | `code-reviewer` | Review code chuyen sau |
| | `code-review-checklist` | Checklist nhanh |
| | `code-review-ai-ai-review` | Review tu dong bang AI |
| | `code-review-excellence` | Hoc cach review tot hon |
| **Refactoring** | `code-refactoring-refactor-clean` | Refactor code hien tai |
| | `codebase-cleanup-refactor-clean` | Cleanup toan bo codebase |
| | `code-refactoring-tech-debt` | Quan ly tech debt |
| | `legacy-modernizer` | Modernize legacy system |
| **Agent** | `ai-agent-development` | Xay dung agent tu dau |
| | `ai-agents-architect` | Thiet ke kien truc agent |
| | `autonomous-agents` | Tim hieu ve autonomous agents |
| | `autonomous-agent-patterns` | Ap dung design patterns |
| **Debug** | `debugger` | Debug loi cu the |
| | `systematic-debugging` | Debug theo quy trinh he thong |
| | `error-detective` | Tim pattern loi trong logs |
| | `debugging-strategies` | Chon chien luoc debug phu hop |
| **Testing** | `testing-qa` | QA tong quat |
| | `test-driven-development` | TDD workflow |
| | `tdd-orchestrator` | Dieu phoi TDD red-green-refactor |
| | `test-automator` | Tu dong hoa testing |

### Luu y ve Composio MCP Server:

Composio (Rube MCP) la nen tang tu dong hoa ket noi voi 80+ dich vu ben ngoai
(CRM, email, cloud storage, social media...).

**Kiem tra truoc khi goi skill Composio:**
1. Xac nhan MCP server dang chay (kiem tra trong Claude Code settings)
2. Xac nhan tai khoan dich vu da duoc ket noi (vd: Slack token, GitHub token)
3. Neu MCP khong kha dung → Khong the dung skill [AUTO], phai thao tac thu cong

### CANH BAO BAO MAT:

**Cac skill [SEC] chi duoc su dung khi:**
- Co van ban uy quyen pentest (engagement letter)
- Trong moi truong CTF/lab
- Phuc vu nghien cuu bao mat hoc thuat
- Defensive security (bao ve he thong cua minh)

**TUYET DOI KHONG:**
- Tan cong he thong khong co quyen
- Scan/recon muc tieu khong duoc uy quyen
- Su dung de tron tranh phat hien (evasion)
- Tan cong tu choi dich vu (DoS)

**Cac skill nguy hiem cao:** `metasploit-framework`, `sqlmap-database-pentesting`,
`privilege-escalation-methods`, `active-directory-attacks`, `red-team-tools`,
`shodan-reconnaissance`, `wireshark-analysis`, `burp-suite-testing`

---

## 2. AI & AGENT DEVELOPMENT

### Agent Architecture & Patterns
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `ai-agent-development` | Xay dung autonomous AI agent | 🔵 |
| `ai-agents-architect` | Thiet ke kien truc agent system | 🔵 |
| `ai-engineer` | LLM apps, RAG, production AI systems | 🔵 |
| `ai-ml` | AI/ML workflow tong quat | 🔵 |
| `ai-product` | AI product development | 🟢 |
| `ai-wrapper-product` | Xay dung san pham boc API AI | 🟢 |
| `autonomous-agent-patterns` | Design patterns cho autonomous agents | 🟢 |
| `autonomous-agents` | He thong AI tu dong | 🟢 |
| `agent-evaluation` | Testing & benchmarking LLM agents | 🟢 |
| `agent-tool-builder` | Xay dung tools cho AI agents | 🟢 |
| `agent-memory-mcp` | Hybrid memory system cho agents | 🟢 |
| `agent-memory-systems` | Thiet ke he thong nho cho agents | 🟢 |
| `agent-manager-skill` | Quan ly nhieu agents qua tmux | 🟢 |
| `agent-orchestration-improve-agent` | Cai thien agent hien co | 🟢 |
| `agent-orchestration-multi-agent-optimize` | Toi uu multi-agent systems | 🟢 |
| `agentfolio` | Tim kiem va nghien cuu AI agents | 🟢 |
| `computer-use-agents` | Agents tuong tac voi may tinh | 🟢 |
| `multi-agent-brainstorming` | Brainstorming co cau truc multi-agent | 🟢 |
| `multi-agent-patterns` | Orchestrator, peer-to-peer, hierarchical | 🟢 |
| `parallel-agents` | Multi-agent orchestration dong thoi | 🟢 |
| `dispatching-parallel-agents` | Chia task doc lap cho nhieu agents | 🟢 |

### LLM & Prompt Engineering
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `prompt-engineer` | Toi uu prompts | 🔵 |
| `prompt-engineering` | Huong dan prompt engineering | 🔵 |
| `prompt-engineering-patterns` | Ky thuat prompt nang cao | 🟢 |
| `prompt-library` | Bo suu tap prompts chat luong | 🟢 |
| `prompt-caching` | Chien luoc caching cho LLM prompts | 🟢 |
| `llm-app-patterns` | Production patterns cho LLM apps | 🟢 |
| `llm-evaluation` | Danh gia LLM applications | 🟢 |
| `llm-application-dev-ai-assistant` | Phat trien AI assistant | 🟢 |
| `llm-application-dev-langchain-agent` | LangChain agent development | 🟢 |
| `llm-application-dev-prompt-optimize` | Toi uu prompt chuyen sau | 🟢 |

### Context Engineering
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `context-fundamentals` | Co ban ve context cho LLM | 🔵 |
| `context-manager` | Quan ly context dong | 🟢 |
| `context-compression` | Nen context cho long conversations | 🟢 |
| `context-degradation` | Nhan biet context failures | 🟢 |
| `context-optimization` | Compaction, masking, caching | 🟢 |
| `context-window-management` | Quan ly context window | 🟢 |
| `context-driven-development` | Phat trien theo context | 🟢 |

### RAG & Search
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `rag-engineer` | Xay dung RAG systems | 🔵 |
| `rag-implementation` | Trien khai RAG | 🟢 |
| `embedding-strategies` | Chon va toi uu embeddings | 🟢 |
| `vector-database-engineer` | Vector DB chuyen sau | 🟢 |
| `vector-index-tuning` | Toi uu vector index | 🟢 |
| `similarity-search-patterns` | Tim kiem tuong tu | 🟢 |
| `hybrid-search-implementation` | Ket hop vector + keyword search | 🟢 |

### Agent Frameworks
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `langchain-architecture` | Thiet ke apps voi LangChain | 🟢 |
| `langgraph` | LangGraph production-grade agents | 🟢 |
| `langfuse` | LLM observability voi Langfuse | 🟢 |
| `crewai` | CrewAI multi-agent framework | 🟢 |
| `claude-api` | Anthropic Claude API/SDK | 🔵 |
| `claude-code-guide` | Huong dan Claude Code CLI | 🔵 |
| `gemini-api-dev` | Google Gemini API | 🟢 |
| `copilot-sdk` | GitHub Copilot SDK | 🟢 |

### Memory & Persistence
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `memory-systems` | Short-term, long-term, graph memory | 🟢 |
| `conversation-memory` | Persistent memory cho LLM | 🟢 |
| `hierarchical-agent-memory` | CLAUDE.md memory system | 🟢 |
| `data-structure-protocol` | Structural memory cho codebase | 🟢 |

---

## 3. BACKEND DEVELOPMENT

### Architecture & Patterns
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `backend-architect` | Backend architecture chuyen sau | 🔵 |
| `backend-dev-guidelines` | Node.js backend standards | 🔵 |
| `backend-development-feature-development` | Feature development E2E | 🟢 |
| `backend-security-coder` | Secure backend coding | 🔴 |
| `architecture-patterns` | Event-driven, CQRS, microservices | 🟢 |
| `microservices-patterns` | Service boundaries, communication | 🟢 |
| `cqrs-implementation` | CQRS pattern | 🟢 |
| `event-sourcing-architect` | Event sourcing + CQRS | 🟢 |
| `event-store-design` | Thiet ke event stores | 🟢 |
| `saga-orchestration` | Distributed transactions | 🟢 |
| `projection-patterns` | Read models tu event streams | 🟢 |

### Node.js / JavaScript Backend
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `nodejs-backend-patterns` | Express/Fastify production patterns | 🔵 |
| `nodejs-best-practices` | Node.js development principles | 🔵 |
| `nestjs-expert` | NestJS framework | 🟢 |
| `bullmq-specialist` | Redis-backed job queues | 🟢 |
| `bun-development` | Bun runtime | 🟢 |

### Python Backend
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `fastapi-pro` | FastAPI async APIs | 🔵 |
| `fastapi-router-py` | FastAPI routers + CRUD | 🟢 |
| `fastapi-templates` | FastAPI project templates | 🟢 |
| `python-fastapi-development` | Python FastAPI tong quat | 🟢 |
| `django-pro` | Django 5.x + DRF + Celery | 🟢 |

### .NET Backend
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `dotnet-architect` | .NET architecture | 🟢 |
| `dotnet-backend` | ASP.NET Core 8+ | 🟢 |
| `dotnet-backend-patterns` | C#/.NET patterns | 🟢 |

### PHP / Laravel
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `laravel-expert` | Laravel production-grade | 🟢 |
| `laravel-security-audit` | Laravel security | 🔴 |
| `php-pro` | PHP nang cao | 🟢 |

### Go Backend
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `golang-pro` | Go 1.21+ modern patterns | 🟢 |
| `go-concurrency-patterns` | Goroutines, channels, sync | 🟢 |
| `grpc-golang` | gRPC services in Go | 🟢 |

### Serverless & Edge
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `aws-serverless` | AWS Lambda production | 🟢 |
| `azure-functions` | Azure Functions | 🟢 |
| `gcp-cloud-run` | Google Cloud Run | 🟢 |
| `cloudflare-workers-expert` | Cloudflare Workers | 🟢 |
| `inngest` | Serverless background jobs | 🟢 |
| `trigger-dev` | Background jobs + AI workflows | 🟢 |

### Auth & Payment
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `auth-implementation-patterns` | Auth patterns | 🔵 |
| `clerk-auth` | Clerk authentication | 🟢 |
| `payment-integration` | Stripe, PayPal | 🟢 |
| `stripe-integration` | Stripe chuyen sau | 🟢 |
| `paypal-integration` | PayPal integration | 🟢 |
| `billing-automation` | Recurring billing | 🟢 |
| `plaid-fintech` | Plaid API fintech | 🟢 |

### GraphQL & API
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `graphql` | GraphQL co ban | 🔵 |
| `graphql-architect` | Federation, performance | 🟢 |
| `file-uploads` | File uploads + cloud storage | 🟢 |

### Workflow Engines
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `temporal-golang-pro` | Temporal + Go | 🟢 |
| `temporal-python-pro` | Temporal + Python | 🟢 |
| `temporal-python-testing` | Test Temporal workflows | 🟢 |
| `workflow-orchestration-patterns` | Durable workflows | 🟢 |
| `dbos-golang` | DBOS Go SDK | 🟢 |
| `dbos-python` | DBOS Python SDK | 🟢 |
| `dbos-typescript` | DBOS TypeScript SDK | 🟢 |

---

## 4. FRONTEND DEVELOPMENT

### React Ecosystem
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `react-patterns` | Modern React hooks, composition | 🔵 |
| `react-best-practices` | React + Next.js optimization | 🔵 |
| `react-nextjs-development` | React + Next.js 14+ | 🔵 |
| `react-state-management` | Redux Toolkit, Zustand, Signals | 🟢 |
| `react-ui-patterns` | Loading, error, data patterns | 🟢 |
| `react-modernization` | Upgrade React versions | 🟢 |
| `react-native-architecture` | React Native + Expo | 🟢 |
| `react-flow-architect` | ReactFlow interactive graphs | 🟢 |
| `react-flow-node-ts` | ReactFlow node components | 🟢 |
| `zustand-store-ts` | Zustand stores TypeScript | 🟢 |
| `fp-ts-errors` | fp-ts Either + TaskEither | 🟢 |
| `fp-ts-pragmatic` | fp-ts thuc dung | 🟢 |
| `fp-ts-react` | fp-ts + React | 🟢 |

### Next.js
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `nextjs-best-practices` | Next.js App Router | 🔵 |
| `nextjs-app-router-patterns` | Server Components, streaming | 🟢 |
| `nextjs-supabase-auth` | Supabase Auth + Next.js | 🟢 |

### Angular
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `angular` | Angular v20+ | 🟢 |
| `angular-best-practices` | Angular optimization | 🟢 |
| `angular-migration` | AngularJS → Angular | 🟢 |
| `angular-state-management` | Signals, NgRx | 🟢 |
| `angular-ui-patterns` | Angular UI patterns | 🟢 |

### CSS & Design Systems
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `tailwind-patterns` | Tailwind CSS v4 | 🔵 |
| `tailwind-design-system` | Design system voi Tailwind | 🟢 |
| `radix-ui-design-system` | Radix UI primitives | 🟢 |
| `core-components` | Component library patterns | 🟢 |
| `frontend-design` | Production-grade UI | 🟢 |
| `frontend-ui-dark-ts` | Dark-themed React + Tailwind | 🟢 |
| `scroll-experience` | Scroll-driven experiences | 🟢 |

### Frontend Dev Guidelines
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `frontend-dev-guidelines` | Frontend standards | 🔵 |
| `frontend-developer` | React components, layouts | 🔵 |
| `frontend-slides` | HTML presentations | 🟢 |
| `frontend-security-coder` | Frontend security | 🔴 |
| `frontend-mobile-development-component-scaffold` | React component scaffold | 🟢 |
| `frontend-mobile-security-xss-scan` | XSS scanning | 🔴 |

### 3D & Visual
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `3d-web-experience` | Three.js 3D experiences | 🟢 |
| `threejs-skills` | Three.js scenes | 🟢 |
| `shader-programming-glsl` | GLSL shaders | 🟢 |
| `algorithmic-art` | p5.js algorithmic art | 🟢 |
| `claude-d3js-skill` | D3.js data visualizations | 🟢 |
| `remotion-best-practices` | Remotion video in React | 🟢 |
| `canvas-design` | Visual art PNG/PDF | 🟢 |

---

## 5. MOBILE DEVELOPMENT

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `mobile-developer` | React Native, Flutter, native | 🔵 |
| `mobile-design` | Mobile-first design | 🔵 |
| `mobile-security-coder` | Mobile security | 🔴 |
| `flutter-expert` | Flutter + Dart 3 | 🟢 |
| `ios-developer` | Swift/SwiftUI | 🟢 |
| `swiftui-expert-skill` | SwiftUI best practices | 🟢 |
| `android-jetpack-compose-expert` | Jetpack Compose | 🟢 |
| `android_ui_verification` | Android UI testing | 🟢 |
| `react-native-architecture` | React Native + Expo | 🟢 |
| `expo-deployment` | Deploy Expo apps | 🟢 |
| `upgrading-expo` | Upgrade Expo SDK | 🟢 |
| `telegram-mini-app` | Telegram Mini Apps (TWA) | 🟢 |
| `app-store-optimization` | ASO toolkit | 🟢 |

---

## 6. DATABASE & DATA ENGINEERING

### Database Design & Admin
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `database` | Database dev + operations | 🔵 |
| `database-design` | Schema, normalization | 🔵 |
| `database-admin` | Cloud-native DB admin | 🟢 |
| `database-architect` | Data layer design | 🟢 |
| `database-optimizer` | Performance optimization | 🟢 |
| `database-migration` | Cross-ORM migrations | 🟢 |

### PostgreSQL
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `postgresql` | PostgreSQL schema design | 🔵 |
| `postgresql-optimization` | Query tuning | 🟢 |
| `postgres-best-practices` | Postgres optimization | 🟢 |
| `neon-postgres` | Neon serverless Postgres | 🟢 |
| `using-neon` | Neon best practices | 🟢 |

### SQL & NoSQL
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `sql-pro` | Modern SQL cloud-native | 🔵 |
| `sql-optimization-patterns` | Query optimization | 🟢 |
| `nosql-expert` | Cassandra, MongoDB, DynamoDB | 🟢 |
| `cc-skill-clickhouse-io` | ClickHouse analytics | 🟢 |

### ORM & Tools
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `prisma-expert` | Prisma ORM | 🟢 |
| `convex` | Convex reactive backend | 🟢 |
| `firebase` | Firebase full backend | 🟢 |

### Data Engineering
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `data-engineer` | Data pipelines, warehouses | 🔵 |
| `data-engineering-data-pipeline` | Pipeline architecture | 🟢 |
| `data-engineering-data-driven-feature` | Data-driven features | 🟢 |
| `data-quality-frameworks` | Great Expectations validation | 🟢 |
| `data-scientist` | Advanced analytics, ML | 🟢 |
| `data-storytelling` | Data visualization narrative | 🟢 |
| `dbt-transformation-patterns` | dbt analytics engineering | 🟢 |
| `spark-optimization` | Apache Spark optimization | 🟢 |
| `airflow-dag-patterns` | Apache Airflow DAGs | 🟢 |

### Migrations
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `database-migrations-sql-migrations` | SQL zero-downtime migrations | 🟢 |
| `database-migrations-migration-observability` | Migration monitoring + CDC | 🟢 |

---

## 7. DEVOPS & CLOUD INFRASTRUCTURE

### Docker & Containers
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `docker-expert` | Docker containerization | 🔵 |
| `kubernetes-architect` | K8s cloud-native | 🔵 |
| `kubernetes-deployment` | K8s deployment | 🟢 |
| `k8s-manifest-generator` | K8s manifests | 🟢 |
| `k8s-security-policies` | K8s security | 🔴 |
| `helm-chart-scaffolding` | Helm charts | 🟢 |

### Cloud Platforms
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `cloud-architect` | AWS/Azure/GCP multi-cloud | 🔵 |
| `cloud-devops` | Cloud infra + DevOps | 🔵 |
| `aws-skills` | AWS development | 🟢 |
| `aws-serverless` | AWS Lambda | 🟢 |
| `aws-cost-cleanup` | AWS resource cleanup | 🟢 |
| `aws-cost-optimizer` | AWS cost optimization | 🟢 |
| `multi-cloud-architecture` | Multi-cloud design | 🟢 |
| `hybrid-cloud-architect` | Hybrid cloud | 🟢 |
| `hybrid-cloud-networking` | Hybrid connectivity | 🟢 |
| `cost-optimization` | Cloud cost rightsizing | 🟢 |

### Terraform & IaC
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `terraform-skill` | Terraform best practices | 🔵 |
| `terraform-specialist` | Terraform/OpenTofu nang cao | 🟢 |
| `terraform-infrastructure` | Terraform IaC | 🟢 |
| `terraform-aws-modules` | Terraform AWS modules | 🟢 |
| `terraform-module-library` | Reusable Terraform modules | 🟢 |
| `cdk-patterns` | AWS CDK patterns | 🟢 |
| `cloudformation-best-practices` | CloudFormation | 🟢 |

### Service Mesh
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `service-mesh-expert` | Istio, Linkerd, Consul | 🟢 |
| `service-mesh-observability` | Mesh observability | 🟢 |
| `istio-traffic-management` | Istio routing | 🟢 |
| `linkerd-patterns` | Linkerd patterns | 🟢 |
| `mtls-configuration` | mTLS zero-trust | 🔴 |

### Server & Deployment
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `server-management` | Server processes, config | 🔵 |
| `deployment-engineer` | CI/CD deployment | 🟢 |
| `deployment-pipeline-design` | Multi-stage pipelines | 🟢 |
| `deployment-procedures` | Production deployment | 🟢 |
| `vercel-deployment` | Vercel + Next.js | 🟢 |
| `vercel-deploy-claimable` | Vercel deploy skill | 🟢 |
| `appdeploy` | Web app deployment | 🟢 |
| `azd-deployment` | Azure Container Apps | 🟢 |
| `gitops-workflow` | ArgoCD + Flux | 🟢 |

---

## 8. TESTING & QA

### Testing Frameworks
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `testing-qa` | Testing + QA tong quat | 🔵 |
| `testing-patterns` | Jest patterns, mocking | 🔵 |
| `test-automator` | AI-powered test automation | 🔵 |
| `test-driven-development` | TDD workflow | 🔵 |
| `tdd-orchestrator` | TDD red-green-refactor | 🟢 |
| `tdd-workflow` | TDD principles | 🟢 |
| `tdd-workflows-tdd-red` | TDD red phase | 🟢 |
| `tdd-workflows-tdd-green` | TDD green phase | 🟢 |
| `tdd-workflows-tdd-refactor` | TDD refactor phase | 🟢 |
| `tdd-workflows-tdd-cycle` | TDD full cycle | 🟢 |
| `test-fixing` | Fix failing tests | 🟢 |
| `unit-testing-test-generate` | Generate unit tests | 🟢 |

### E2E Testing
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `e2e-testing` | Playwright E2E | 🔵 |
| `e2e-testing-patterns` | Playwright + Cypress | 🟢 |
| `playwright-skill` | Playwright automation | 🟢 |
| `webapp-testing` | Web app testing | 🟢 |
| `browser-automation` | Browser testing + scraping | 🟢 |
| `screenshots` | Marketing screenshots | 🟢 |

### Language-Specific Testing
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `javascript-testing-patterns` | Jest, Vitest | 🟢 |
| `python-testing-patterns` | pytest patterns | 🟢 |
| `bats-testing-patterns` | Bash testing (Bats) | 🟢 |
| `web3-testing` | Smart contract testing | 🟢 |

### Code Review
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `code-reviewer` | Elite code review | 🔵 |
| `code-review-checklist` | Review checklist | 🔵 |
| `code-review-excellence` | Effective review practices | 🟢 |
| `code-review-ai-ai-review` | AI-powered review | 🟢 |
| `codex-review` | Review + CHANGELOG | 🟢 |
| `requesting-code-review` | Request review format | 🟢 |
| `receiving-code-review` | Handle review feedback | 🟢 |
| `fix-review` | Verify fix commits | 🟢 |

---

## 9. SECURITY & PENETRATION TESTING

### Security General
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `security-audit` | Security audit tong quat | 🔴 |
| `security-auditor` | DevSecOps audit | 🔴 |
| `vulnerability-scanner` | OWASP 2025 scanning | 🔴 |
| `security-bluebook-builder` | Security Blue Books | 🔴 |
| `security-compliance-compliance-check` | Compliance checking | 🔴 |
| `security-requirement-extraction` | Security requirements | 🔴 |
| `security-scanning-security-dependencies` | Dependency vulnerabilities | 🔴 |
| `security-scanning-security-hardening` | Multi-layer hardening | 🔴 |
| `security-scanning-security-sast` | SAST scanning | 🔴 |
| `sast-configuration` | SAST config | 🔴 |
| `api-security-best-practices` | API security | 🔴 |
| `api-security-testing` | API security testing | 🔴 |
| `pci-compliance` | PCI DSS compliance | 🔴 |
| `gdpr-data-handling` | GDPR compliance | 🔴 |
| `secrets-management` | CI/CD secrets | 🔴 |

### Penetration Testing
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `pentest-checklist` | Pentest planning | 🔴 |
| `pentest-commands` | Pentest commands | 🔴 |
| `aws-penetration-testing` | AWS pentest | 🔴 |
| `cloud-penetration-testing` | Cloud pentest | 🔴 |
| `web-security-testing` | OWASP Top 10 | 🔴 |
| `sql-injection-testing` | SQL injection | 🔴 |
| `xss-html-injection` | XSS testing | 🔴 |
| `html-injection-testing` | HTML injection | 🔴 |
| `file-path-traversal` | Path traversal | 🔴 |
| `idor-testing` | IDOR testing | 🔴 |
| `broken-authentication` | Auth testing | 🔴 |
| `ssh-penetration-testing` | SSH pentest | 🔴 |
| `smtp-penetration-testing` | SMTP pentest | 🔴 |
| `wordpress-penetration-testing` | WordPress pentest | 🔴 |
| `sqlmap-database-pentesting` | SQLMap auto pentest | 🔴 |

### Offensive Security Tools
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `metasploit-framework` | Metasploit | 🔴 |
| `burp-suite-testing` | Burp Suite | 🔴 |
| `ffuf-claude-skill` | Web fuzzing | 🔴 |
| `scanning-tools` | Security scanning | 🔴 |
| `shodan-reconnaissance` | Shodan recon | 🔴 |
| `wireshark-analysis` | Packet analysis | 🔴 |
| `api-fuzzing-bug-bounty` | API fuzzing | 🔴 |

### Red Team & Attack
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `red-team-tactics` | MITRE ATT&CK tactics | 🔴 |
| `red-team-tools` | Red team tooling | 🔴 |
| `active-directory-attacks` | AD attacks | 🔴 |
| `privilege-escalation-methods` | Priv esc methods | 🔴 |
| `linux-privilege-escalation` | Linux priv esc | 🔴 |
| `windows-privilege-escalation` | Windows priv esc | 🔴 |
| `attack-tree-construction` | Attack trees | 🔴 |
| `ethical-hacking-methodology` | Ethical hacking | 🔴 |
| `top-web-vulnerabilities` | Top web vulns | 🔴 |

### Threat Modeling & Defense
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `threat-modeling-expert` | Threat modeling | 🔴 |
| `stride-analysis-patterns` | STRIDE methodology | 🔴 |
| `threat-mitigation-mapping` | Threat → controls | 🔴 |

### Reverse Engineering
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `reverse-engineer` | Binary analysis | 🔴 |
| `firmware-analyst` | Firmware analysis | 🔴 |
| `binary-analysis-patterns` | Disassembly patterns | 🔴 |
| `anti-reversing-techniques` | Anti-reversing | 🔴 |
| `protocol-reverse-engineering` | Protocol RE | 🔴 |
| `memory-forensics` | Memory forensics | 🔴 |
| `malware-analyst` | Defensive malware analysis | 🔴 |

---

## 10. API DESIGN & DOCUMENTATION

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `api-design-principles` | REST + GraphQL design | 🔵 |
| `api-patterns` | API decision-making | 🔵 |
| `api-documentation` | OpenAPI specs generation | 🔵 |
| `api-documentation-generator` | Auto API docs | 🟢 |
| `api-documenter` | OpenAPI 3.1 | 🟢 |
| `api-testing-observability-api-mock` | API mocking | 🟢 |
| `openapi-spec-generation` | OpenAPI 3.1 specs | 🟢 |

---

## 11. ARCHITECTURE & DESIGN PATTERNS

### Software Architecture
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `architecture` | Architectural decisions | 🔵 |
| `architect-review` | Architecture review | 🔵 |
| `senior-architect` | Comprehensive architecture | 🟢 |
| `software-architecture` | Quality-focused architecture | 🟢 |
| `architecture-decision-records` | ADRs | 🟢 |

### Domain-Driven Design
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `domain-driven-design` | DDD routing/planning | 🟢 |
| `ddd-strategic-design` | Subdomains, contexts | 🟢 |
| `ddd-tactical-patterns` | Entities, value objects | 🟢 |
| `ddd-context-mapping` | Context relationships | 🟢 |

### Clean Code & Refactoring
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `clean-code` | Clean Code principles | 🔵 |
| `code-refactoring-refactor-clean` | Code refactoring | 🟢 |
| `code-refactoring-tech-debt` | Tech debt management | 🟢 |
| `codebase-cleanup-refactor-clean` | Codebase cleanup | 🟢 |
| `codebase-cleanup-tech-debt` | Tech debt cleanup | 🟢 |
| `legacy-modernizer` | Legacy code modernization | 🟢 |

### C4 Architecture Diagrams
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `c4-architecture-c4-architecture` | Full C4 docs | 🟢 |
| `c4-context` | C4 Context level | 🟢 |
| `c4-container` | C4 Container level | 🟢 |
| `c4-component` | C4 Component level | 🟢 |
| `c4-code` | C4 Code level | 🟢 |

---

## 12. PROGRAMMING LANGUAGES

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `python-pro` | Python 3.12+ nang cao | 🔵 |
| `python-patterns` | Python development principles | 🔵 |
| `python-performance-optimization` | Python profiling | 🟢 |
| `python-packaging` | Python packages | 🟢 |
| `async-python-patterns` | Python asyncio | 🟢 |
| `uv-package-manager` | uv package manager | 🟢 |
| `pydantic-models-py` | Pydantic models | 🟢 |
| `javascript-pro` | Modern JavaScript ES6+ | 🔵 |
| `javascript-mastery` | JS 33+ topics | 🔵 |
| `modern-javascript-patterns` | ES6+ features | 🟢 |
| `typescript-pro` | TypeScript nang cao | 🔵 |
| `typescript-expert` | TS + JS expert | 🔵 |
| `typescript-advanced-types` | Generics, utility types | 🟢 |
| `rust-pro` | Rust 1.75+ | 🟢 |
| `rust-async-patterns` | Tokio async Rust | 🟢 |
| `c-pro` | C memory management | 🟢 |
| `cpp-pro` | Modern C++ RAII | 🟢 |
| `csharp-pro` | Modern C# records, LINQ | 🟢 |
| `java-pro` | Java 21+ virtual threads | 🟢 |
| `kotlin-coroutines-expert` | Kotlin Coroutines + Flow | 🟢 |
| `scala-pro` | Enterprise Scala | 🟢 |
| `ruby-pro` | Ruby metaprogramming | 🟢 |
| `elixir-pro` | Elixir OTP | 🟢 |
| `haskell-pro` | Haskell type system | 🟢 |
| `julia-pro` | Julia 1.10+ | 🟢 |
| `golang-pro` | Go 1.21+ | 🟢 |
| `sql-pro` | Modern SQL | 🔵 |

### Shell & Scripting
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `bash-pro` | Defensive Bash | 🔵 |
| `bash-linux` | Bash/Linux patterns | 🔵 |
| `bash-scripting` | Production Bash | 🟢 |
| `bash-defensive-patterns` | Defensive Bash techniques | 🟢 |
| `posix-shell-pro` | POSIX sh strict | 🟢 |
| `powershell-windows` | PowerShell Windows | 🟢 |
| `shellcheck-configuration` | ShellCheck config | 🟢 |
| `linux-shell-scripting` | Linux shell scripts | 🟢 |
| `busybox-on-windows` | BusyBox on Windows | 🟢 |

---

## 13. GIT & VERSION CONTROL

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `commit` | Sentry commit conventions | 🔵 |
| `create-pr` | Sentry PR conventions | 🔵 |
| `git-pushing` | Stage, commit, push | 🔵 |
| `git-advanced-workflows` | Rebasing, cherry-pick | 🟢 |
| `git-pr-workflows-git-workflow` | Full git workflow | 🟢 |
| `git-pr-workflows-pr-enhance` | PR optimization | 🟢 |
| `git-pr-workflows-onboard` | Onboarding specialist | 🟢 |
| `iterate-pr` | Fix PR until CI passes | 🟢 |
| `address-github-comments` | Address PR comments | 🟢 |
| `using-git-worktrees` | Git worktrees isolation | 🟢 |
| `finishing-a-development-branch` | Complete dev branch | 🟢 |
| `changelog-automation` | Auto changelog | 🟢 |

---

## 14. CI/CD & AUTOMATION

### CI/CD Platforms
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `github-actions-templates` | GitHub Actions workflows | 🔵 |
| `github-workflow-automation` | GitHub workflow AI | 🟢 |
| `gitlab-ci-patterns` | GitLab CI/CD | 🟢 |
| `cicd-automation-workflow-automate` | Workflow automation | 🟢 |
| `deployment-pipeline-design` | Multi-stage pipelines | 🟢 |

### Build Tools
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `monorepo-architect` | Monorepo architecture | 🟢 |
| `monorepo-management` | Turborepo, Nx, pnpm | 🟢 |
| `turborepo-caching` | Turborepo caching | 🟢 |
| `nx-workspace-patterns` | Nx workspace | 🟢 |
| `bazel-build-optimization` | Bazel builds | 🟢 |

### Quality & Linting
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `lint-and-validate` | Auto linting + static analysis | 🔵 |
| `find-bugs` | Bug + vulnerability finding | 🔵 |
| `vibe-code-auditor` | Audit AI-generated code | 🟢 |
| `production-code-audit` | Deep codebase scan | 🟢 |
| `simplify` | Review + simplify code | 🟢 |

---

## 15. MONITORING & OBSERVABILITY

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `observability-engineer` | Monitoring, logging, tracing | 🔵 |
| `observability-monitoring-monitor-setup` | Monitor setup | 🟢 |
| `observability-monitoring-slo-implement` | SLO implementation | 🟢 |
| `slo-implementation` | SLI/SLO define | 🟢 |
| `prometheus-configuration` | Prometheus metrics | 🟢 |
| `grafana-dashboards` | Grafana dashboards | 🟢 |
| `distributed-tracing` | Jaeger + Tempo tracing | 🟢 |
| `distributed-debugging-debug-trace` | Debug tracing setup | 🟢 |
| `kpi-dashboard-design` | KPI dashboards | 🟢 |

### Incident Response
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `incident-responder` | SRE incident response | 🔵 |
| `incident-response-incident-response` | Incident workflow | 🟢 |
| `incident-response-smart-fix` | Smart incident fix | 🟢 |
| `incident-runbook-templates` | Runbook templates | 🟢 |
| `on-call-handoff-patterns` | On-call handoffs | 🟢 |
| `postmortem-writing` | Blameless postmortems | 🟢 |
| `devops-troubleshooter` | Rapid incident troubleshooting | 🟢 |

---

## 16. SEO & MARKETING

### SEO
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `seo-fundamentals` | SEO core principles | 🔵 |
| `seo-audit` | SEO audit | 🟢 |
| `seo-content-writer` | SEO-optimized content | 🟢 |
| `seo-content-planner` | Content outlines, clusters | 🟢 |
| `seo-content-auditor` | Content quality E-E-A-T | 🟢 |
| `seo-content-refresher` | Update outdated content | 🟢 |
| `seo-keyword-strategist` | Keyword analysis | 🟢 |
| `seo-meta-optimizer` | Meta titles, descriptions | 🟢 |
| `seo-structure-architect` | Content structure | 🟢 |
| `seo-authority-builder` | E-E-A-T signals | 🟢 |
| `seo-snippet-hunter` | Featured snippets | 🟢 |
| `seo-cannibalization-detector` | Keyword cannibalization | 🟢 |
| `seo-forensic-incident-response` | Traffic drop investigation | 🟢 |
| `geo-fundamentals` | AI search optimization | 🟢 |
| `programmatic-seo` | Programmatic SEO | 🟢 |
| `schema-markup` | Schema.org structured data | 🟢 |
| `local-legal-seo-audit` | Local SEO for law firms | 🟢 |

### Marketing & Growth
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `content-creator` | SEO marketing content | 🟢 |
| `content-marketer` | AI-powered content marketing | 🟢 |
| `marketing-ideas` | Marketing strategies | 🟢 |
| `marketing-psychology` | Behavioral science | 🟢 |
| `copywriting` | Conversion-focused copy | 🟢 |
| `social-content` | Social media content | 🟢 |
| `email-sequence` | Email sequences | 🟢 |
| `paid-ads` | Paid advertising | 🟢 |
| `launch-strategy` | Product launch planning | 🟢 |
| `referral-program` | Referral programs | 🟢 |
| `analytics-tracking` | Analytics systems | 🟢 |

### CRO (Conversion Rate Optimization)
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `page-cro` | Page optimization | 🟢 |
| `form-cro` | Form optimization | 🟢 |
| `popup-cro` | Popup optimization | 🟢 |
| `signup-flow-cro` | Signup flow optimization | 🟢 |
| `onboarding-cro` | Post-signup optimization | 🟢 |
| `paywall-upgrade-cro` | Paywall optimization | 🟢 |
| `ab-test-setup` | A/B test setup | 🟢 |

---

## 17. CRM & BUSINESS AUTOMATION (Composio MCP)

> **Luu y:** Tat ca skills [AUTO] ben duoi yeu cau Rube MCP (Composio) server duoc cau hinh.
> Kiem tra: MCP server chay + tai khoan dich vu da ket noi. Neu khong → KHONG the dung.

### CRM
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `hubspot-automation` | HubSpot CRM | [AUTO] |
| `salesforce-automation` | Salesforce | [AUTO] |
| `pipedrive-automation` | Pipedrive | [AUTO] |
| `close-automation` | Close CRM | [AUTO] |
| `zoho-crm-automation` | Zoho CRM | [AUTO] |

### Project Management
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `jira-automation` | Jira | [AUTO] |
| `linear-automation` | Linear | [AUTO] |
| `asana-automation` | Asana | [AUTO] |
| `clickup-automation` | ClickUp | [AUTO] |
| `monday-automation` | Monday.com | [AUTO] |
| `trello-automation` | Trello | [AUTO] |
| `wrike-automation` | Wrike | [AUTO] |
| `basecamp-automation` | Basecamp | [AUTO] |
| `todoist-automation` | Todoist | [AUTO] |

### Communication
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `slack-automation` | Slack | [AUTO] |
| `discord-automation` | Discord | [AUTO] |
| `microsoft-teams-automation` | MS Teams | [AUTO] |
| `telegram-automation` | Telegram | [AUTO] |
| `intercom-automation` | Intercom | [AUTO] |
| `gmail-automation` | Gmail | [AUTO] |
| `outlook-automation` | Outlook | [AUTO] |
| `outlook-calendar-automation` | Outlook Calendar | [AUTO] |

### Email Marketing
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `mailchimp-automation` | Mailchimp | [AUTO] |
| `sendgrid-automation` | SendGrid | [AUTO] |
| `activecampaign-automation` | ActiveCampaign | [AUTO] |
| `brevo-automation` | Brevo (Sendinblue) | [AUTO] |
| `convertkit-automation` | ConvertKit | [AUTO] |
| `klaviyo-automation` | Klaviyo | [AUTO] |
| `postmark-automation` | Postmark | [AUTO] |

### Cloud Storage
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `google-drive-automation` | Google Drive | [AUTO] |
| `dropbox-automation` | Dropbox | [AUTO] |
| `box-automation` | Box | [AUTO] |
| `one-drive-automation` | OneDrive | [AUTO] |

### Dev Tools Automation
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `github-automation` | GitHub | [AUTO] |
| `gitlab-automation` | GitLab | [AUTO] |
| `bitbucket-automation` | Bitbucket | [AUTO] |
| `circleci-automation` | CircleCI | [AUTO] |
| `vercel-automation` | Vercel | [AUTO] |
| `render-automation` | Render | [AUTO] |
| `sentry-automation` | Sentry | [AUTO] |
| `datadog-automation` | Datadog | [AUTO] |
| `pagerduty-automation` | PagerDuty | [AUTO] |

### Analytics
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `google-analytics-automation` | Google Analytics | [AUTO] |
| `amplitude-automation` | Amplitude | [AUTO] |
| `mixpanel-automation` | Mixpanel | [AUTO] |
| `posthog-automation` | PostHog | [AUTO] |
| `segment-automation` | Segment | [AUTO] |

### Calendar & Scheduling
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `google-calendar-automation` | Google Calendar | [AUTO] |
| `cal-com-automation` | Cal.com | [AUTO] |
| `calendly-automation` | Calendly | [AUTO] |
| `zoom-automation` | Zoom | [AUTO] |

### Productivity & Docs
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `notion-automation` | Notion | [AUTO] |
| `confluence-automation` | Confluence | [AUTO] |
| `coda-automation` | Coda | [AUTO] |
| `googlesheets-automation` | Google Sheets | [AUTO] |
| `airtable-automation` | Airtable | [AUTO] |
| `miro-automation` | Miro | [AUTO] |
| `figma-automation` | Figma | [AUTO] |
| `canva-automation` | Canva | [AUTO] |

### E-commerce & Payment
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `shopify-automation` | Shopify | [AUTO] |
| `stripe-automation` | Stripe | [AUTO] |
| `square-automation` | Square | [AUTO] |
| `webflow-automation` | Webflow | [AUTO] |

### Social Media
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `twitter-automation` | Twitter/X | [AUTO] |
| `linkedin-automation` | LinkedIn | [AUTO] |
| `instagram-automation` | Instagram | [AUTO] |
| `tiktok-automation` | TikTok | [AUTO] |
| `youtube-automation` | YouTube | [AUTO] |
| `reddit-automation` | Reddit | [AUTO] |

### Customer Support
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `freshdesk-automation` | Freshdesk | [AUTO] |
| `freshservice-automation` | Freshservice | [AUTO] |
| `helpdesk-automation` | HelpDesk | [AUTO] |
| `zendesk-automation` | Zendesk | [AUTO] |

### HR & Legal
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `bamboohr-automation` | BambooHR | [AUTO] |
| `docusign-automation` | DocuSign | [AUTO] |

### Workflow Platforms
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `make-automation` | Make (Integromat) | [AUTO] |
| `zapier-make-patterns` | Zapier + Make | [AUTO] |

---

## 18. DOCUMENT & OFFICE TOOLS

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `pdf` / `pdf-official` | PDF manipulation toolkit | 🔵 |
| `docx` / `docx-official` | Word document creation/editing | 🔵 |
| `xlsx` / `xlsx-official` | Spreadsheet creation/editing | 🔵 |
| `pptx` / `pptx-official` | Presentation creation/editing | 🔵 |
| `nanobanana-ppt-skills` | AI-powered PPT generation | 🟢 |
| `office-productivity` | Office workflow | 🟢 |
| `mermaid-expert` | Mermaid diagrams | 🟢 |

---

## 19. AZURE SDK COLLECTION

> **68+ Azure SDK skills** theo ngon ngu: .NET, Java, Python, TypeScript, Rust

### Categories:
- **AI Services:** `azure-ai-projects-*`, `azure-ai-openai-*`, `azure-ai-voicelive-*`, `azure-ai-contentsafety-*`, `azure-ai-vision-*`, `azure-ai-textanalytics-*`, `azure-ai-transcription-*`, `azure-ai-translation-*`, `azure-ai-document-intelligence-*`, `azure-ai-ml-py`
- **Identity/Auth:** `azure-identity-dotnet`, `azure-identity-java`, `azure-identity-py`, `azure-identity-rust`, `azure-identity-ts`
- **Storage:** `azure-storage-blob-*`, `azure-storage-file-*`, `azure-storage-queue-*`
- **Messaging:** `azure-servicebus-*`, `azure-eventhub-*`, `azure-eventgrid-*`, `azure-web-pubsub-*`
- **Databases:** `azure-cosmos-*`, `azure-data-tables-*`, `azure-search-documents-*`
- **Key Vault:** `azure-keyvault-*`, `azure-security-keyvault-*`
- **Monitoring:** `azure-monitor-*`
- **Management:** `azure-mgmt-*`, `azure-resource-manager-*`
- **Communication:** `azure-communication-*`
- **M365 Agents:** `m365-agents-dotnet`, `m365-agents-py`, `m365-agents-ts`

---

## 20. GAME DEVELOPMENT

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `game-development` | Game dev orchestrator | 🔵 |
| `unity-developer` | Unity C# games | 🟢 |
| `unity-ecs-patterns` | Unity ECS + DOTS | 🟢 |
| `unreal-engine-cpp-pro` | Unreal Engine 5.x C++ | 🟢 |
| `godot-gdscript-patterns` | Godot 4 GDScript | 🟢 |
| `godot-4-migration` | Godot 3.x → 4.x | 🟢 |
| `bevy-ecs-expert` | Bevy ECS Rust | 🟢 |
| `minecraft-bukkit-pro` | Minecraft Bukkit plugins | 🟢 |

---

## 21. BLOCKCHAIN & WEB3

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `blockchain-developer` | Web3 apps, smart contracts | 🟢 |
| `solidity-security` | Smart contract security | 🔴 |
| `nft-standards` | ERC-721, ERC-1155 | 🟢 |
| `defi-protocol-templates` | DeFi protocol templates | 🟢 |
| `web3-testing` | Smart contract testing | 🟢 |
| `crypto-bd-agent` | Crypto business development | 🟢 |

---

## 22. CONTENT & WRITING

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `beautiful-prose` | Hard-edged writing style | 🟢 |
| `copy-editing` | Edit + improve writing | 🟢 |
| `copywriting` | Marketing copy | 🟢 |
| `doc-coauthoring` | Co-authoring workflow | 🟢 |
| `kaigai-novel-writer` | Japanese novel writing | 🟢 |
| `kaigai-script-writer` | Japanese YouTube scripts | 🟢 |
| `podcast-generation` | AI podcast audio | 🟢 |
| `audio-transcriber` | Audio → Markdown | 🟢 |
| `youtube-summarizer` | YouTube transcripts | 🟢 |

---

## 23. RESEARCH & ANALYSIS

| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `deep-research` | Multi-step research | 🔵 |
| `search-specialist` | Advanced web search | 🔵 |
| `research-engineer` | Academic research | 🟢 |
| `claude-scientific-skills` | Scientific analysis | 🟢 |
| `infinite-gratitude` | Parallel research execution | 🟢 |
| `last30days` | Last 30 days research | 🟢 |
| `daily-news-report` | Daily news scraping | 🟢 |
| `exa-search` | Semantic search + discovery | 🟢 |
| `tavily-web` | Web search + extraction | 🟢 |
| `firecrawl-scraper` | Deep web scraping | 🟢 |
| `apify-ultimate-scraper` | Universal AI scraper | 🟢 |

### Business Analysis
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `business-analyst` | AI-powered business analysis | 🟢 |
| `startup-analyst` | Startup market analysis | 🟢 |
| `startup-financial-modeling` | Financial modeling | 🟢 |
| `startup-metrics-framework` | Startup metrics | 🟢 |
| `competitive-landscape` | Competitive analysis | 🟢 |
| `market-sizing-analysis` | Market sizing | 🟢 |
| `product-manager-toolkit` | PM toolkit | 🟢 |
| `pricing-strategy` | Pricing design | 🟢 |
| `quant-analyst` | Financial models, backtesting | 🟢 |
| `risk-manager` | Portfolio risk monitoring | 🟢 |
| `risk-metrics-calculation` | VaR, CVaR, Sharpe | 🟢 |
| `backtesting-frameworks` | Trading backtesting | 🟢 |

---

## 24. WORKFLOW & PROJECT MANAGEMENT

### Planning & Execution
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `brainstorming` | Creative brainstorming | 🔵 |
| `plan-writing` | Structured task planning | 🔵 |
| `writing-plans` | Multi-step implementation plans | 🔵 |
| `executing-plans` | Execute from plans | 🔵 |
| `concise-planning` | Quick planning | 🟢 |
| `planning-with-files` | File-based planning | 🟢 |
| `subagent-driven-development` | Execute with sub-agents | 🟢 |

### Conductor System
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `conductor-setup` | Initialize Conductor project | 🟢 |
| `conductor-new-track` | Create new track | 🟢 |
| `conductor-implement` | Execute track tasks | 🟢 |
| `conductor-status` | Project status | 🟢 |
| `conductor-manage` | Track lifecycle | 🟢 |
| `conductor-revert` | Git-aware undo | 🟢 |
| `conductor-validator` | Validate artifacts | 🟢 |
| `track-management` | Track management | 🟢 |
| `workflow-patterns` | Conductor patterns | 🟢 |

### Documentation
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `documentation` | API docs, architecture docs | 🔵 |
| `documentation-generation-doc-generate` | Auto doc generation | 🟢 |
| `documentation-templates` | README, contributing, etc. | 🟢 |
| `docs-architect` | Technical docs from code | 🟢 |
| `readme` | README creation | 🟢 |
| `code-documentation-code-explain` | Code explanation | 🟢 |
| `code-documentation-doc-generate` | Code doc generation | 🟢 |
| `reference-builder` | Technical references | 🟢 |
| `tutorial-engineer` | Step-by-step tutorials | 🟢 |

### Wiki System
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `wiki-architect` | Hierarchical wiki from code | 🟢 |
| `wiki-changelog` | Wiki changelog | 🟢 |
| `wiki-onboarding` | Onboarding guides | 🟢 |
| `wiki-page-writer` | Wiki pages | 🟢 |
| `wiki-qa` | Wiki Q&A | 🟢 |
| `wiki-researcher` | Deep wiki research | 🟢 |
| `wiki-vitepress` | VitePress wiki | 🟢 |

### Debugging
| Skill | Mo ta | Muc do |
|-------|-------|--------|
| `debugger` | Error specialist | 🔵 |
| `systematic-debugging` | Systematic debug workflow | 🔵 |
| `debugging-strategies` | Profiling, tracing | 🟢 |
| `error-handling-patterns` | Error handling patterns | 🟢 |
| `error-detective` | Error pattern search | 🟢 |
| `sharp-edges` | Error-prone API detection | 🟢 |

---

## 25. SPECIALIZED INDUSTRY SKILLS

### Supply Chain & Logistics
| Skill | Mo ta |
|-------|-------|
| `carrier-relationship-management` | Carrier portfolio management |
| `customs-trade-compliance` | Customs & tariff compliance |
| `inventory-demand-planning` | Demand forecasting |
| `logistics-exception-management` | Freight exception handling |
| `production-scheduling` | Job sequencing |
| `quality-nonconformance` | Quality control |
| `returns-reverse-logistics` | Returns management |
| `energy-procurement` | Energy procurement |

### HR & Legal
| Skill | Mo ta |
|-------|-------|
| `hr-pro` | HR hiring, onboarding |
| `legal-advisor` | Privacy policies, ToS |
| `employment-contract-templates` | Employment contracts |

### Design (Apple HIG)
| Skill | Mo ta |
|-------|-------|
| `hig-foundations` | Apple HIG foundations |
| `hig-patterns` | HIG interaction patterns |
| `hig-platforms` | Platform-specific HIG |
| `hig-components-*` | HIG component guides (9 skills) |
| `hig-inputs` | HIG input methods |
| `hig-technologies` | Apple tech integrations |
| `hig-project-context` | Apple design context |

### Bots & Messaging
| Skill | Mo ta |
|-------|-------|
| `discord-bot-architect` | Discord bots |
| `slack-bot-builder` | Slack bots (Bolt) |
| `telegram-bot-builder` | Telegram bots |
| `automate-whatsapp` | WhatsApp automations |
| `observe-whatsapp` | WhatsApp troubleshooting |

### E-commerce
| Skill | Mo ta |
|-------|-------|
| `shopify-development` | Shopify apps/themes |
| `shopify-apps` | Shopify app dev |
| `wordpress` | WordPress full workflow |
| `wordpress-plugin-development` | WP plugins |
| `wordpress-theme-development` | WP themes |
| `wordpress-woocommerce-development` | WooCommerce |

### Browser Extensions
| Skill | Mo ta |
|-------|-------|
| `browser-extension-builder` | Browser extension builder |
| `chrome-extension-developer` | Chrome Manifest V3 |

### UI/UX Design
| Skill | Mo ta |
|-------|-------|
| `ui-ux-designer` | Interface design + wireframes |
| `ui-ux-pro-max` | 67 styles, 96 palettes |
| `ui-skills` | Agent UI constraints |
| `ui-visual-validator` | Visual UI testing |
| `web-design-guidelines` | Web interface guidelines |
| `stitch-ui-design` | Google Stitch prompts |
| `design-orchestration` | Design workflow routing |
| `interactive-portfolio` | Portfolio builder |

### Miscellaneous
| Skill | Mo ta |
|-------|-------|
| `claude-ally-health` | Health assistant |
| `claude-win11-speckit-update-skill` | Windows 11 management |
| `skill-creator` | Create new skills |
| `skill-developer` | Manage Claude skills |
| `skill-seekers` | Convert docs to skills |
| `writing-skills` | Create/improve agent skills |
| `personal-tool-builder` | Build custom tools |
| `micro-saas-launcher` | Launch micro-SaaS |
| `viral-generator-builder` | Shareable generator tools |
| `customer-support` | AI customer support |
| `sales-automator` | Cold emails, proposals |
| `kaizen` | Continuous improvement |
| `file-organizer` | File organization |
| `loki-mode` | Multi-agent startup system |
| `voice-agents` | Voice AI agents |
| `voice-ai-development` | Voice AI apps |
| `voice-ai-engine-development` | Voice AI engine |
| `data-storytelling` | Data narratives |

---

## HUONG DAN SU DUNG CHO AGENT AI

### 1. Quy trinh chon Skill (Chi tiet)

```
Buoc 1: Xac dinh LOAI nhiem vu
  ├── Viet code moi
  │   ├── Backend API → fastapi-pro, nestjs-expert, django-pro, laravel-expert, golang-pro
  │   ├── Frontend UI → react-patterns, angular, flutter-expert, nextjs-best-practices
  │   ├── Database → postgresql, prisma-expert, database-design
  │   ├── Mobile → ios-developer, android-jetpack-compose-expert, react-native-architecture
  │   ├── DevOps → docker-expert, kubernetes-architect, terraform-skill
  │   ├── AI/ML → ai-engineer, rag-engineer, langchain-architecture
  │   └── Game → unity-developer, godot-gdscript-patterns, bevy-ecs-expert
  │
  ├── Fix bug / Debug
  │   ├── Loi cu the, co stack trace → debugger
  │   ├── Loi phuc tap, can he thong → systematic-debugging
  │   ├── Tim pattern loi trong logs → error-detective
  │   ├── Loi performance → performance-engineer
  │   └── Test fail → test-fixing
  │
  ├── Review / Audit
  │   ├── Review code → code-reviewer
  │   ├── Review nhanh (checklist) → code-review-checklist
  │   ├── Review PR → comprehensive-review-pr-enhance
  │   ├── Audit security → security-audit
  │   └── Audit code quality → production-code-audit, vibe-code-auditor
  │
  ├── Testing
  │   ├── Unit test → unit-testing-test-generate
  │   ├── TDD → test-driven-development
  │   ├── E2E → e2e-testing, playwright-skill
  │   ├── API testing → api-testing-observability-api-mock
  │   └── Security testing → web-security-testing, api-security-testing
  │
  ├── Deploy / Infra
  │   ├── Docker → docker-expert
  │   ├── Kubernetes → kubernetes-architect
  │   ├── CI/CD → github-actions-templates, gitlab-ci-patterns
  │   ├── Cloud → aws-serverless, azure-functions, gcp-cloud-run
  │   └── Vercel/Render → vercel-deployment, render-automation
  │
  ├── Security [YEU CAU QUYEN]
  │   ├── Pentest web → web-security-testing, burp-suite-testing
  │   ├── Pentest API → api-fuzzing-bug-bounty, api-security-testing
  │   ├── Pentest cloud → aws-penetration-testing, cloud-penetration-testing
  │   ├── Threat modeling → threat-modeling-expert, stride-analysis-patterns
  │   └── Reverse engineering → reverse-engineer, firmware-analyst
  │
  ├── Documentation
  │   ├── API docs → api-documentation, openapi-spec-generation
  │   ├── Project docs → documentation, docs-architect
  │   ├── README → readme
  │   └── Wiki → wiki-architect, wiki-page-writer
  │
  ├── Research / Tim kiem
  │   ├── Research web → deep-research, search-specialist
  │   ├── Scraping → firecrawl-scraper, apify-ultimate-scraper
  │   ├── Business analysis → business-analyst, startup-analyst
  │   └── Competitive → competitive-landscape
  │
  └── Marketing / SEO
      ├── SEO → seo-fundamentals, seo-audit
      ├── Content → content-creator, copywriting
      ├── CRO → page-cro, signup-flow-cro
      └── Email → email-sequence

Buoc 2: Uu tien chuyen biet > tong quat
  VD: fastapi-pro > python-pro > backend-architect
  VD: nextjs-app-router-patterns > react-patterns > frontend-developer

Buoc 3: Ket hop skills khi can (xac nhan ket qua giua cac buoc)
  VD: brainstorming → [xac nhan] → writing-plans → [xac nhan] → executing-plans

Buoc 4: Neu task da-domain (vd: "optimize Django DB on K8s")
  → Chon 1 skill chinh (django-pro) + 1-2 skill ho tro (postgresql-optimization, kubernetes-architect)
  → Khong goi qua 3 skills cung luc — giam hieu qua
```

### 2. Cac chuoi Skill thuong dung

**Luu y:** Giua moi buoc, PHAI xac nhan ket qua truoc khi chuyen sang buoc tiep.
Neu buoc nao that bai → dung lai, khong tiep tuc chuoi.

#### Phat trien feature moi:
```
brainstorming → [xac nhan y tuong]
→ writing-plans → [xac nhan plan]
→ test-driven-development → executing-plans
→ code-reviewer → [xac nhan code OK]
→ verification-before-completion → commit → create-pr
```

#### Fix bug:
```
systematic-debugging → [xac dinh nguyen nhan]
→ debugger → [viet fix]
→ test-fixing → [xac nhan tests pass]
→ fix-review → commit
```

#### Security audit:
```
security-audit → [liet ke findings]
→ vulnerability-scanner → [xac nhan vulns]
→ security-scanning-security-sast → security-scanning-security-dependencies
→ security-bluebook-builder
```

#### Setup project moi:
```
architecture → [xac nhan kien truc]
→ database-design → [xac nhan schema]
→ docker-expert → github-actions-templates → terraform-skill
```

#### SEO campaign:
```
seo-fundamentals → seo-audit → [danh gia hien trang]
→ seo-keyword-strategist → seo-content-planner
→ seo-content-writer → seo-meta-optimizer → schema-markup
```

### 3. Luu y quan trong cho Agent

1. **Khong goi skill khong co tren may** — Chi su dung skills trong thu muc `~/.claude/skills/`
2. **Composio/MCP skills** — Kiem tra MCP server dang chay va tai khoan da ket noi truoc khi goi
3. **Security skills [SEC]** — YEU CAU van ban uy quyen hoac moi truong CTF/lab
4. **Azure SDK skills** — Can Azure credentials va `azure-identity-*` duoc cau hinh
5. **Ket hop parallel agents** khi co nhieu tasks doc lap (nhung khong qua 3 dong thoi)
6. **Doc ky mo ta skill** truoc khi goi — Xem bang "Phan biet skill tuong tu" o Section 1
7. **Luon xac nhan ket qua** giua cac buoc trong chuoi skill
8. **Khong retry vo han** — Thu lai toi da 1 lan, sau do tim skill thay the hoac lam thu cong
9. **Resource contention** — Tren Windows, tranh chay nhieu skills cung truy cap 1 file/port

### 4. Skill theo vai tro Agent

| Vai tro Agent | Skills cu the |
|---------------|--------------|
| **Coder** | `python-pro`, `javascript-pro`, `typescript-pro`, `golang-pro`, `rust-pro`, `java-pro`, `csharp-pro`, `clean-code` |
| **Backend Dev** | `fastapi-pro`, `nestjs-expert`, `django-pro`, `laravel-expert`, `dotnet-backend`, `nodejs-backend-patterns` |
| **Frontend Dev** | `react-patterns`, `nextjs-best-practices`, `angular`, `tailwind-patterns`, `frontend-developer` |
| **Reviewer** | `code-reviewer`, `code-review-checklist`, `code-review-ai-ai-review`, `lint-and-validate`, `codex-review` |
| **Tester** | `testing-qa`, `test-driven-development`, `e2e-testing`, `playwright-skill`, `test-automator`, `unit-testing-test-generate` |
| **Architect** | `architecture`, `senior-architect`, `software-architecture`, `ddd-strategic-design`, `c4-architecture-c4-architecture` |
| **DevOps** | `docker-expert`, `kubernetes-architect`, `terraform-specialist`, `cloud-architect`, `github-actions-templates` |
| **Security** | `security-audit`, `vulnerability-scanner`, `pentest-checklist`, `web-security-testing`, `threat-modeling-expert` |
| **Researcher** | `deep-research`, `search-specialist`, `firecrawl-scraper`, `exa-search`, `tavily-web` |
| **Writer** | `documentation`, `docs-architect`, `readme`, `tutorial-engineer`, `wiki-page-writer`, `reference-builder` |
| **PM** | `product-manager-toolkit`, `brainstorming`, `plan-writing`, `writing-plans`, `concise-planning` |
| **Marketer** | `seo-fundamentals`, `seo-audit`, `content-creator`, `copywriting`, `marketing-ideas`, `page-cro` |
| **Data Engineer** | `data-engineer`, `dbt-transformation-patterns`, `airflow-dag-patterns`, `spark-optimization`, `data-quality-frameworks` |
| **AI Engineer** | `ai-engineer`, `rag-engineer`, `langchain-architecture`, `langgraph`, `prompt-engineer`, `agent-tool-builder` |

---

---

## DECISION LOG (Multi-Agent Brainstorming)

### Qua trinh review:
- **Primary Designer**: Tao ban dau 961 skills, phan loai 25 sections
- **Skeptic Agent**: 10 objections — focus overlap, YAGNI, error handling, security
- **Constraint Guardian**: 8 concerns — count mismatch, phantom skills, schema inconsistency
- **User Advocate**: 8 concerns — cognitive load, disambiguation, Composio explanation

### Quyet dinh:

| # | Van de | Quyet dinh | Ly do |
|---|--------|-----------|-------|
| 1 | Khong co error handling | **ACCEPTED** — Da them section "Xu ly loi khi goi Skill" | Critical cho agent autonomy |
| 2 | Security warnings yeu | **ACCEPTED** — Da them "CANH BAO BAO MAT" chi tiet + danh sach skills nguy hiem | Phap ly + an toan |
| 3 | Skill selection qua nong | **ACCEPTED** — Da mo rong thanh cay quyet dinh 2 cap voi skills cu the | Agent can huong dan ro rang |
| 4 | Table schema khong nhat quan | **ACCEPTED** — Da them cot "Muc do" cho Section 17 | Consistency |
| 5 | Composio khong giai thich | **ACCEPTED** — Da them section "Luu y ve Composio MCP Server" | Agent can biet cach kiem tra |
| 6 | Wildcard patterns | **ACCEPTED** — Da thay bang ten skill cu the trong "Skill theo vai tro" | Agent khong the resolve wildcards |
| 7 | Skills tuong tu khong phan biet | **ACCEPTED** — Da them bang "Phan biet cac skill tuong tu" | Giam nham lan |
| 8 | Validation giua cac buoc chuoi | **ACCEPTED** — Da them [xac nhan] markers trong chuoi skill | Ngan loi lan truyen |
| 9 | 961 skills la YAGNI | **REJECTED** — Day la catalog tham khao, khong phai recommendation | Catalog can day du |
| 10 | Can JSON/YAML format | **DEFERRED** — Ngoai pham vi deliverable hien tai | Co the lam sau |
| 11 | Vietnamese diacritics | **REJECTED** — He thong chay tren non-VN locale | Encoding issues |
| 12 | Can metrics/pruning | **DEFERRED** — Can runtime infrastructure | Ngoai pham vi |

### Arbiter verdict: **APPROVED**
- Tat ca reviewer da duoc goi
- Tat ca objections da duoc xu ly hoac tu choi co ly do
- Decision Log day du
- Thiet ke du an toan de su dung

---

*Tai lieu duoc tao boi Multi-Agent Brainstorming Process (5 agents).*
*Tong so skills tren may: 961 | Cap nhat: 2026-03-20*
*Review: Skeptic (10 objections) | Constraint Guardian (8 concerns) | User Advocate (8 concerns)*
*8/12 objections accepted and fixed | 2 rejected | 2 deferred*
