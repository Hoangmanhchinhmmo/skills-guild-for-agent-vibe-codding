# vibe-coding-skills-guild — Design Document

## Date: 2026-03-20

---

## 1. Understanding Summary

- **What:** Phát triển repo thành repo nổi tiếng trên GitHub — catalog 1,282+ Claude Code skills được curate, tổ chức, và hướng dẫn dành riêng cho vibe coders
- **Who:** Bất kỳ ai muốn build bằng AI mà không cần master kỹ thuật — non-devs, juniors, founders, career switchers
- **Why:** Chưa có tài liệu nào tổng hợp, phân loại, và hướng dẫn sử dụng Claude Code skills cho người ít kiến thức chuyên môn
- **How:** Awesome-list (Phase 1) → Documentation site (Phase 2) → Community platform (Phase 3)
- **Language:** English (chính) + Tiếng Việt, cấu trúc i18n sẵn cho community mở rộng
- **Maintenance:** Solo + AI automation (auto-detect skills mới) + community contributions
- **Success:** Stars + Usage + Authority + Community

---

## 2. Assumptions

- GitHub account và quyền tạo repo public
- Budget = $0 (GitHub Pages, GitHub Actions, Astro Starlight — tất cả free)
- Claude Code dùng để tự động hóa phần lớn công việc maintain
- Nội dung enrichment (use cases, combos, examples) bổ sung dần, top 50 skills trước
- Community contributions đến sau khi repo đạt traction ban đầu

---

## 3. Architecture

### Repository Structure

```
vibe-coding-skills-guild/
├── README.md                    # English — eye-catching landing page
├── README.vi.md                 # Tiếng Việt
├── LICENSE                      # MIT
├── CONTRIBUTING.md              # Hướng dẫn contribute (EN)
├── CONTRIBUTING.vi.md           # (VI)
├── CODE_OF_CONDUCT.md
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── skill-request.md     # Yêu cầu thêm skill mới
│   │   ├── skill-improvement.md # Cải thiện skill có sẵn
│   │   └── bug-report.md
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       ├── auto-detect-skills.yml   # Scan skills mới tự động (weekly)
│       ├── validate-links.yml       # Kiểm tra broken links (daily)
│       ├── auto-translate.yml       # Sync EN ↔ VI (on PR merge)
│       ├── stats-update.yml         # Update badges + counts (weekly)
│       └── welcome-bot.yml         # Chào contributor mới
├── guide/
│   ├── en/
│   │   ├── getting-started.md       # "Bạn mới vibe coding? Bắt đầu đây"
│   │   ├── skill-combos.md          # Workflow recipes
│   │   ├── how-to-choose-skills.md  # Decision tree cho beginners
│   │   └── faq.md
│   └── vi/
│       ├── bat-dau.md
│       ├── ket-hop-skills.md
│       ├── cach-chon-skills.md
│       └── faq.md
├── skills/
│   ├── en/                          # Mỗi category 1 file
│   │   ├── 01-ai-agent.md
│   │   ├── 02-backend.md
│   │   └── ...
│   └── vi/
│       ├── 01-ai-agent.md
│       └── ...
└── docs/                            # Phase 2: Astro Starlight source
```

### README.md Structure

```
1. HERO SECTION — Logo, tagline, badges
   "1,282+ curated Claude Code skills for vibe coders"
   "Don't know which skill to use? We got you."

2. QUICK START — 3 steps: Browse → Pick combo → Use

3. SKILL FINDER TABLE — "I want to..." → Recommended skills
   10-15 use cases phổ biến nhất

4. CATEGORIES — Mục lục với icon + số lượng

5. SKILL COMBOS — Top 5 recipes (teaser)

6. CONTRIBUTING — "Add a skill", "Improve", "Translate"

7. LANGUAGE SWITCHER — 🇬🇧 English | 🇻🇳 Tiếng Việt

8. FOOTER — Star history, contributors, license
```

### Enriched Skill Format

```markdown
### `skill-name`

**Bạn cần gì:** Mô tả không jargon
**Mức độ:** 🟢 Beginner-friendly | 🟡 Intermediate | 🔴 Advanced
**Tags:** #category #subcategory

**Khi nào dùng:**
- Use case 1
- Use case 2

**Kết hợp với:**
- skill-a → skill-b → **skill-name** → skill-c

**Prompt mẫu:**
> /skill-name [example prompt]

**Không nên dùng khi:**
- Trường hợp nên dùng skill khác
```

### Skill Combos (Killer Feature)

Top 10 combos ưu tiên:
1. 🚀 Build a SaaS MVP (Solo Founder)
2. 🤖 Build an AI Chatbot
3. 📱 Build a Mobile App
4. 🛒 Build an E-commerce Store
5. 📊 Build a Dashboard
6. 🔐 Add Auth to Any Project
7. 🧹 Fix & Improve Existing Code
8. 📝 Build a Blog/Content Site
9. 🎮 Build a Simple Game
10. 💼 Build a Portfolio Website

Mỗi combo có: mục đích, thời gian ước tính, thứ tự skill, giải thích mỗi bước.

---

## 4. Automation (GitHub Actions)

| Workflow | Trigger | Chức năng |
|----------|---------|-----------|
| `auto-detect-skills.yml` | Weekly (cron) | Scan skills mới → tạo PR |
| `validate-links.yml` | Daily (cron) | Check broken links → tạo issue |
| `auto-translate.yml` | On PR merge | Dịch EN → VI → tạo PR |
| `stats-update.yml` | Weekly (cron) | Update badges, counts trên README |
| `welcome-bot.yml` | On new issue/PR | Chào contributor mới, gắn label |

Nguyên tắc: Mọi automation tạo PR chờ review, không auto-merge.

---

## 5. Documentation Site (Phase 2)

**Framework:** Astro Starlight
- i18n built-in (EN + VI)
- Pagefind search (offline, $0)
- Dark mode built-in
- Deploy: GitHub Pages

**Tính năng:**
1. Skill Finder (interactive dropdown/search)
2. Category Browser (sidebar navigation)
3. Combo Recipes (visual flowcharts)
4. i18n Switcher
5. Dark Mode

---

## 6. Growth Strategy

**Launch day:**
- Reddit: r/ClaudeAI, r/ChatGPTPro, r/artificial
- Twitter/X: #ClaudeCode #VibeCoding #AI
- HackerNews: "Show HN: 1,282curated skills for vibe coders using Claude Code"
- Discord: Claude, AI Builders, Indie Hackers

**Tuần đầu:**
- GitHub Discussions mở
- Pin issue "Most Wanted Skills" (voting)
- Pin issue "Share Your Skill Combo"

**SEO:**
- Repo description: "1,282+ curated Claude Code skills for vibe coders. Find the right skill combo for your project in seconds."
- Topics: claude-code, vibe-coding, ai-skills, awesome-list, claude, ai-agents

**Ongoing:**
- Weekly auto-commit giữ repo active
- Star history badge
- "Featured in" section

---

## 7. Decision Log

| # | Quyết định | Lựa chọn khác | Lý do |
|---|-----------|---------------|-------|
| 1 | Tên repo: `vibe-coding-skills-guild` | awesome-claude-skills, skillmap | Giữ "guild" + "vibe coding" trend, dễ nhớ |
| 2 | Target: Mọi người ít kỹ thuật muốn build bằng AI | Chỉ developers | Thị trường lớn nhất |
| 3 | Approach: Awesome-First (3 phases) | Website-First, Community-First | Có sẵn 1,282skills, launch nhanh |
| 4 | Ngôn ngữ: EN + VI, mở i18n | Song ngữ cùng file | Chuẩn quốc tế + giữ gốc Việt |
| 5 | Maintain: Solo + AI + community | Solo only | Đúng tinh thần vibe coding |
| 6 | Skill format: Enriched cho top 50 trước | Chỉ tên + mô tả | Giá trị thực, bổ sung dần |
| 7 | Killer feature: Skill Combos | Chỉ list | Khác biệt hóa hoàn toàn |
| 8 | Automation: 5 workflows, PR chờ review | Manual, auto-merge | Tiết kiệm effort, giữ chất lượng |
| 9 | Docs: Astro Starlight | Docusaurus, VitePress | i18n + search tốt nhất, $0 |
| 10 | Growth: Multi-channel launch | Organic only | Cần initial push |

---

## 8. Implementation Phases

### Phase 1: Repository chuẩn quốc tế (Tuần 1-2)
- [ ] Tạo repo public trên GitHub
- [ ] README.md eye-catching (EN)
- [ ] README.vi.md (VI)
- [ ] LICENSE (MIT)
- [ ] CONTRIBUTING.md + CONTRIBUTING.vi.md
- [ ] CODE_OF_CONDUCT.md
- [ ] Cấu trúc folder i18n
- [ ] Chuyển skills sang EN + giữ VI
- [ ] Enriched format cho top 50 skills
- [ ] 10 Skill Combos
- [ ] guide/en/getting-started.md
- [ ] guide/en/how-to-choose-skills.md
- [ ] GitHub issue/PR templates
- [ ] GitHub Actions workflows (5 cái)
- [ ] Launch marketing (Reddit, HN, Twitter, Discord)

### Phase 2: Documentation site (Tuần 3-6)
- [ ] Setup Astro Starlight
- [ ] Migrate content sang website
- [ ] Skill Finder interactive
- [ ] i18n EN/VI
- [ ] Deploy GitHub Pages
- [ ] Update README trỏ về website

### Phase 3: Community (Tháng 2-3)
- [ ] GitHub Discussions setup
- [ ] Contributor leaderboard
- [ ] Voting system cho skills
- [ ] PR review workflow cho contributions
- [ ] "Featured in" section cập nhật

---

*Design document created: 2026-03-20*
*Approach: Awesome-First with 3 phases*
*Budget: $0*
