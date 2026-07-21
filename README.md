# AI Product Manager Portfolio Case Study

---

## Introduction

**Project name: Hatua**
An AI agent that helps East African digital freelancers turn real platform proof-of-work and metrics into CVs potential employers trust. Made for freelancers who are looking to transition from freelance informal employment to formal roles - remote or in-person.

**Role:** Solo AI Product Manager / Designer / Builder
**Timeline:** June – August 2026 (10 weeks)
**Status:** 🟡 In Progress / 🟢 Shipped *(update as you go)*

**Live demo link:** *(add when ready)*

**GitHub repo:** Hatua Github repo

*(Hero image: a clean before/after CV screenshot works well here once you have one)*

---

## 1. The Problem

### The specific pain

In sub-Saharan Africa, entry level employment continues to remain a real problem. The International Labour Organization projects youth (ages 15–24) unemployment at approximately **10%** regionally, with significant country-by-country variation. Over **10 million** young people enter the African labour market annually, yet formal job creation only accommodates a fraction of these entrants. This forces many educated youth to start off their careers as online freelancers as placeholder jobs before gaining formal employment. 

However, most youth still prefer formal employment as the digital gig economy does not offer stability and career growth. The freelancers who are looking for an opportunity to transition from the informal gig economy to formal employment find the transition challenging mainly because:

- **Skills gap anxiety** - Experienced, skilled, freelancers in design, with strong informal track record lack confidence that their real freelancing achievements are enough, even if visible, resulting in a confidence gap.
- Interview fluency - Many freelances lack real-life interview experience and this limits their readiness to join the formal employment world.
- Poorly framed CVs -  Freelancer CVs tend to be poorly framed and ATS-incompatible. Freelancers lack the framework to translate platform metrics (ratings, repeat-client rate, response time, volume) into CV/interview language that formal remote employers recognize and trust making them invisible to potential employers. 
**

### Market context

- Sub-Saharan Africa now holds ~17.5 million freelancers driving a rapidly expanding digital gig economy.
- Why now: Freelance market competition has been growing throughout the last 10 years. This is due to an ever growing number of freelancers in Sub-Saharan Africa, lack of adequate employment opportunities, exploitative platform practices and an explosion of AI-driven options, pushing freelancers toward more formal and long-term remote roles.

**No existing market report isolates this specific sub-problem (CV/credibility translation). Market demand was assessed through freelance community discussions and primary research, specifically interviews, not secondary stats.* 

---

## 2. The User

The user is the established, highly skilled Sub-Saharan Africa freelance designer, 5+ years experience with a strong but unquantified track record in UI/UX, brand identity, graphic design, and 3D animation. This user segment is picked from personal proximity + real network access, not picked for size of market.

### Real User Evidence

**Case 1 — James**

- 12 years freelancing, Platinum-tier 99designs, 120+ clients worldwide, 47% repeat-client rate. Actively upskilling to AI design services.
- Tools: Canva, Claude, Figma, Adobe Illustrator.
- Pushed toward formal roles by: contracting freelance market, platform fee changes, competition from AI in design and desire for income predictability.
- Application outcome before Hatua: constant job application rejections and lack of responses from companies.
- Has never had anyone frame his transferable design skills for him — classic Hatua user
- **Actual CV reviewed** with findings:
    - Strong metric (4.96★) buried as second-to-last bullet, not headline
    - No repeat-client number, no project count stated as outcome
    - Two-column layout = real ATS parsing risk
    - Unclear positioning (4 job titles in headline + unrelated CPA/IBA credentials)

**Case 2 — Anne** 

- 10 years freelancing on Upwork as a digital marketer. Actively upskilling to AI automation services
- Platform metrics: 4.4★ (47 reviews), 267 completed projects, 16.7% repeat client rate.
- Pushed toward formal roles by: client attrition, AI-driven competition (clients turning to AI for marketing needs), income unpredictability
- Tools: Canva, Zapier, Google Analytics, ChatGPT
- Application outcome before Hatua: applied to remote mid-level digital marketing roles; reached interview stage twice; rejected at offer stage due to low skills outlined ("Skills gap" concern is a confidence gap, not a real gap). CV *is* clearing initial screening (reached interview twice) — problem is positioning, not ATS survival.
- Lack of proper CV language framing. (Delegating work + reviewing output before client delivery = contractor/vendor management; 267 projects = stakeholder management at scale)
- Has never had anyone name her transferable skills for her — classic Hatua user

### Research finding — pivot-narrative pattern (v1.5)

Anne's case surfaced a second distinct user pattern during week 1 validation: the **pivot-narrative user** — a freelancer not just formalizing existing skills but actively transitioning into a new service area (AI automation, in her case). This user needs a bridge narrative ("here's where I've been and here's the clear line to where I'm going"), not just translation of existing metrics.

**Deliberate decision:** This pattern was identified before building began and consciously deferred to v1.5 rather than expanding v1 scope. Reasoning: 

(a) Rests on one user at time of discovery — thin validation for a new conversation branch from v1; 

(b) Adding a second flow inside a 10-week solo build risks doing both shallowly; 

**Transition for v1.5 scope when ready:** Revise prompt flow to accommodate wider conversation branching; Pivot Hatua to bridge between past freelance identity and target future roles.

### Competitive landscape

| Tool | Strength | Gap for this user |
| --- | --- | --- |
| Rezi | 88%+ ATS parse rate, single-column templates | No concept of freelance-platform metrics as input; AI bullet generator fabricates numbers |
| Teal | Job-search CRM + keyword matching | Built for traditional W-2 history, not platform-based proof-of-work |
| Qwyse | Coaches users to quantify vague achievements | Generic — no freelance-platform awareness, no Africa/Kenya context, paid US-market SaaS |

### **The real gap**

- No tool translates *real* freelance-platform metrics and proof of work (ratings, repeat-client %, response time) into employer-trusted language. Most of the available tools expect the user to come up with the metrics and proof of work and fit them into a CV for them to review and develop better versions with the data already supplied.
- No tool translates *real* freelance-platform metrics and proof of work (ratings, repeat-client %, response time) without fabricating data.
- No non-generic tools are built for the East African (and African) freelance-to-formal transition specifically. Most are built for generic CV generation and review.

---

## 3. The Decision Process

### Ideas considered and rejected

1. **Idea A — "Daktari Triage": AI symptom-and-resource navigator for informal settlement clinics.** A WhatsApp-based agent that helps community health volunteers (CHVs) in places like Kibera or Mathare triage patients before they reach an overstretched clinic — asking structured questions, flagging red-flag symptoms, and directing people to the right level of care (self-care, clinic, hospital) plus the nearest facility that actually has capacity/stock that day.
    
    **Reason for rejection:** Sensitivity of medical information and lack of enough experience and knowledge in the medical sector
    
2. **Idea B — "Soko Scout": AI agent for informal traders (mama mboga / jua kali) to manage credit, pricing, and supplier negotiation.** An agent that helps small informal traders track who owes them what (replacing the notebook ledger), suggests pricing based on local market data, and even drafts/sends payment reminders via SMS/WhatsApp — built for low-literacy, low-smartphone-capability users.
    
    **Reason for rejection:** Lack of enough knowledge and experience in the sector. 
    
3. **Idea C — "Hatua": AI agent that helps Kenyan job seekers translate informal/hustle experience into formal CVs and interview readiness for remote/global roles.** An agent that interviews a user conversationally about their actual work history (including informal or gig work), structures it into a credible CV and LinkedIn profile, and preps them for remote-job interview formats — essentially solving the "I have real skills but no formal paper trail" problem that blocks East Africans from remote work platforms.
    
    **Reason for choosing:** Personal proximity + network access of freelancers for real validation. 
    

### Scope decisions — what got cut, and why

- *Considered:* All three disciplines - design, writing, dev - from day one → **Decided:** Design-only for v1 → **Reasoning:** Can’t credibly judge writing/code quality with same authority as 10 years of design judgment.
- *Considered:* Both established and emerging freelancers → **Decided:** Established only → **Reasoning:** Different products, not different intensities — emerging freelancers need more in terms of gap-coaching, not just translation.
- *Considered:* Cover letter + LinkedIn rewrite in v1 → **Decided:** Cut to v1.5 → **Reasoning:** Same extraction engine, but doesn’t showcase the core differentiator any further than the CV already does; Also protects the Aug 31 deadline
- *Considered:* Custom-coded backend app → **Decided:** Claude API + lightweight front-end → **Reasoning:** Matches actual skillset (prompt engineering, not backend engineering); protects time for the harder problem (extraction logic) over infrastructure

---

## 4. The Product

### What Hatua does (v1)

- Conversational intake: Hatua interviews users about freelance work history, platform accomplishments and metrics, career goals.
- Extraction: structures real (not invented) achievement data into consumable information
- Output 1: ATS-formatted CV (simple, single-column, standard fonts, no graphics/tables)
- Output 2: Static interview-prep document — likely questions + talking points grounded in actual CV content obtained from the interview

### Hatua non-goals (explicit)

- **Not for writers/devs and emerging freelancers (for v1.5):** Also not for the broader informal economy
- **Not a job-matching app: D**oes not also include application tracking and job-platform integrations
- **No dedicated mobile apps:** This will be fully web-native and responsive. Not building an Android or iOS application.
- **Not multi-language**
- **No native user auth system:** You are **not** building a custom signup, login, or password recovery system
- **No custom database backend:** Everything runs in-session (volatile local state). If the user refreshes, they start over.
- Does not draw up cover letters/LinkedIn (for v1.5),
- Does not converse with the user on other CV sections - Education. Focus is on experience and real achievements framing

### Key design and prompt engineering decisions

- Extraction prompt handled thin/messy data well without fabricating metrics. The tone was displayed as instructed in the prompt. ✅
- Original prompt build in the Hatua.jsx file had to be engineered and elevated by moving away from raw text blocks and adopting structured XML-tag architectures. This better prompt structure eliminates ambiguity by explicitly separating instructions and context **✅**
- **Token Space**:  `max_tokens` set at `1000` for initial conversations, but scaled up to `4000` right before triggering Phase 4 so the generated CV text doesn't hit a sudden hard cut-off limit.
- Added download capabilities and button. The system prompt now instructs the model to emit two explicit separators (`--- ATS-FORMATTED CV ---` and `--- INTERVIEW-PREP DOCUMENT ---`) as outputs. The `parseOutputs()` function slices on those markers, so each document is cleanly isolated before being handed to the downloader.
- **Token Exhaustion before achieving results.**  Three separate issues were causing this:
    - The output-trigger was unreliable:  If a user answers tersely and reaches Phase 4 before message 14, that turn only gets 1,000 tokens — not enough for a full CV + interview-prep doc, so response cuts off mid-document. ***Fix:*** have the model signal phase transitions explicitly (e.g. emit `<phase:2>`, `<phase:3>`,  tags at the start of each reply), and set `maxTokens` based on the *actual* phase tag from the previous response, not message count or string-matching.
    - One call was being used to produce two full documents at once: 4,000 tokens had to cover the model's chat, the entire CV, *and* the interview-prep doc. ***Fix:*** split Phase 4 into two sequential API calls — one that returns only the CV, another that returns only the interview-prep doc. Gave each its own 3,000–4,000 token budget. This also means a truncation only costs one document, not both.
    - The full system prompt + full transcript was resent on every single turn: The system prompt is long and `messages` grows every turn. ***Fix:*** instead of appending every raw turn to `messages`, maintain a compact JSON "extracted answers" object client-side (name, platform, metrics, achievements, target role, confidence gap) and send *that* plus just the latest exchange, rather than the full transcript. Update it after each assistant reply.
- **Phase 2 (Achievement excavation) has no hard cap:**  3 sub-questions per area or work achievement is open-ended — a user with 4 service lines could hit 12+ questions before Phase 3 even starts. ***Fix:*** cap it explicitly, e.g. "cover no more than the 2–3 highest-impact work areas; if the user names more, ask which 2–3 matter most for their target role." This keeps the interview in line and on topic.
- Added two new `<guardrail>` blocks to the system prompt (inside the `SYSTEM_PROMPT` template literal), inserted right after the existing `no_fabrication` guardrail, before the `duty_to_outcome_rewrites` examples:
    - **`no_fabrication_cv_output`** — fires right before the CV is written in response to `GENERATE_CV_ONLY`. Makes the model re-check every bullet against the transcript *at generation time*, not just back in Phase 4.
    - **`no_fabrication_interview_prep_output`** — fires right before the interview-prep doc is written in response to `GENERATE_PREP_ONLY`. This one didn't exist at all before. It covers the different risk profile for that document (invented story outcomes, conflicts, or opinions rather than invented numbers), tells the model how to handle gaps (flag rather than invent), and ends with the same trace-back-to-transcript check.

---

## 5. Evidence & Results

### Results checkpoint

| Date | Task | Status | Remedy |
| --- | --- | --- | --- |
| 29/06/26 | Conversational intake: Working end-to-end flow | ✅ | - |
|  | Extraction: Turn data into consumable information | ❌ | Engineer prompt to translate freelance language into formal role language throughout |
|  | Output 1: ATS-formatted CV | ❌ | Engineer more effective prompts |
|  | Output 2: Static interview-prep document | ❌ | Increase output token limits |
| 2/07/26 | Conversational intake: Working end-to-end flow | ❌ | Limit questions to important queries and ask two questions at a time instead of one at a time to guard against token limit being exceeded. |
|  | Extraction: Turn data into consumable information | ✅ | - |
|  | Output 1: ATS-formatted CV | ❌ | Engineer more effective prompts |
|  | Output 2: Static interview-prep document | ✅ | - |
| 5/07/26 | Conversational intake: Working end-to-end flow | ❌ | Added capped phase-detection with an explicit phase tag so that conversation doesn’t cut off before outputs |
|  | Extraction: Turn data into consumable information | ✅ | - |
|  | Output 1: ATS-formatted CV | ✅ | - |
|  | Output 2: Static interview-prep document | ✅ | - |
| 8/07/26 | Conversational intake: Working end-to-end flow | ❌ | Tightened the prompt's tagging instructions to remove a wait step and unnecessary user action at the final phase |
|  | Extraction: Turn data into consumable information | ✅ | - |
|  | Output 1: ATS-formatted CV | ✅ | - |
|  | Output 2: Static interview-prep document | ✅ | - |
| 10/07/26 | Conversational intake: Working end-to-end flow | ✅ | - |
|  | Extraction: Turn data into consumable information | ✅ | - |
|  | Output 1: ATS-formatted CV | ✅ | - |
|  | Output 2: Static interview-prep document | ✅ | - |
| 13/07/2026 | Conversational intake: Working end-to-end flow | ✅ | - |
|  | Extraction: Turn data into consumable information | ✅ | - |
|  | Output 1: ATS-formatted CV | ✅ | - |
|  | Output 2: Static interview-prep document | ✅ | - |

### Before/after Hatua extracted CVs

| Case | ATS score before | ATS score after | Tool used to measure |
| --- | --- | --- | --- |
| Mwai | 78 | 87 | https://enhancv.com/resources/resume-checker/ |
| Anne | 64 | 89 | https://enhancv.com/resources/resume-checker/ |
| Hareem | 69 | 87 | https://enhancv.com/resources/resume-checker/ |
| Yusuf | 56 | 84 | https://enhancv.com/resources/resume-checker/ |
| Shari | 68 | 85 | https://enhancv.com/resources/resume-checker/ |
| Sunny | 72 | 89 | https://enhancv.com/resources/resume-checker/ |

### Qualitative feedback

- Mwai’s reaction to the output: “There was a small but noticeable incidence of fabrication on the Interview Prep document”
    - *What I changed in response:*  Added two new `<guardrail>` blocks to the system prompt (inside the `SYSTEM_PROMPT` template literal), inserted right after the existing `no_fabrication` guardrail, before the `duty_to_outcome_rewrites` examples. 
    Hatua already had a *pre*-generation check for the CV
- Anne’s reaction to the output: “Too many question asked by Hatua. It seemed like the questions were never-ending”
    - *What I changed in response:* Added a soft ceiling of ~10 questions in every phase, with instructions to move on and use qualitative framing for anything still missing.
- Sunny’s reaction to the output: “The ‘What to Research Before Your Interview’ was an unexpected and pleasant addition to the Interview Prep document. This really helped in my preparation for my interview”
    - *What I changed in response:* Maintained the file as is. No change required. Additional features were maintained.
- Shari’s reaction to the output: “The summary section of the CV is doing its job, but the Skills section has mixed the tools with some role keywords. This, I suspect, is blocking ATS keyword parsing”
    - *What I changed in response:* Split the Skills section into two explicit subsections — role competencies first, tools second (the software list). Core Competencies comes first — this is the ATS keyword block, mapped directly to the user's target role, listing capabilities not tools. Tools & Platforms comes second — the actual software list. ATS parsers weight the competencies block heavily because it matches the keyword clusters recruiters build into their filters. Separating them means neither dilutes the other.

### Security Considerations

To keep Hatua as simple, safe and fast as possible, I used **Vercel Serverless Functions**. Vercel allows a user to drop a single backend file into a project folder alongside the`index.html`, and it handles the server setup.

I created a secure serverless backend that sits between the HTML page and Anthropic's servers. When the frontend needs to connect to the AI, it will fetch from `/api/chat` instead of calling Anthropic directly. This keeps the `ANTHROPIC_API_KEY` hidden on Vercel's secure servers, prevents users from stealing your key to run up bills, and cleanly proxies all conversational requests. `callClaude()` now fetches `/api/chat` — key removed from browser entirely.

### Honest limitations

- The sample size (6) is good enough to provide directional and product need Suevidence, but too small to be proof at scale
- The cost of token usage on my Claude tier made it expensive to run the web app the whole day or a continuous period of usage.
- Everything runs in-session (volatile local state). If the user refreshes, they start over. This was intentional so as to security overhead entirely.

---

## 6. Outcome & Reflection

- Did you hit the Aug 31 deadline? What shipped vs. what got cut?
- What would you build next (v1.5 → v2 roadmap): cover letter, LinkedIn rewrite, writers/devs, emerging freelancers, practice-interview simulation, Swahili
- What this project taught you about AI product management specifically — not generic “I learned a lot,” but a real decision you’d make differently next time

---

## 7. Appendix

- Link to full system prompts / extraction logic
- GitHub repo - https://github.com/Gitush-prmt/Hatua
- Link to raw interview notes (Mwai, Mutile) — anonymized if shared publicly
- Idea Probe Protocol transcript or summary (optional — shows your thinking process in full, which is rare and valuable)
