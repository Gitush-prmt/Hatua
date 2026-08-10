# Hatua
### AI career translation agent for East African freelance designers

**Built by:** Gituru Mwai — UX/UI Designer / AI UX Product Manager / Conversational AI PM

**Timeline:** 10 weeks (June – August 2026)

**Stack:** Claude API · React · EnhanceCV (ATS validation)

**Live demo:** *https://hatuacv.vercel.app/*

**Full case study:** *https://app.notion.com/p/Hatua-386248c7214780feaa7dc027881dfdaa?source=copy_link*

---

## The Problem

Established East African freelance designers have real, verifiable track records — platform ratings, repeat-client rates, project volume — but no framework to translate that proof-of-work into language a formal remote employer trusts. The result: strong designers with 10+ years of experience receiving only silence or automated rejections, not because their skills are lacking, but because their CVs speak a different language than the recruiters and ATS systems screening them.

---

## What Hatua does

Hatua interviews a user conversationally about their freelance history and produces two outputs in a single session:

**1. ATS-formatted CV** — single-column, keyword-mapped to the user's target role, with every bullet following a strict action verb + what + outcome structure. Skills section split into Core Competencies (ATS keyword block) and Tools & Platforms (software list).

**2. Interview-prep document** — likely questions for the target role with answer frameworks built from the user's real data, a section addressing the specific confidence gap the user named, and a "what to research before your interview" guide.

**Core differentiator:** No fabrication. Competing tools (Rezi, Teal, Qwyse) generate plausible-sounding metrics the user never provided. Hatua uses only data the user can actually defend in an interview. If a number isn't there, it frames the achievement qualitatively instead.

---

## Results — 6 real users

| User | ATS before | ATS after | Improvement |
|---|---|---|---|
| Gits | 69% | 87% | +18 pts |
| Mwai | 78% | 87% | +9 pts |
| Anne *(anonymized)* | 64% | 89% | +25 pts |
| Yusuf | 56% | 84% | +28 pts |
| Shari | 68% | 85% | +17 pts |
| Sunny | 72% | 89% | +17 pts |
| **Average** | **67.8%** | **86.8%** | **+19 pts** |

Every user confirmed every bullet was accurate — nothing they couldn't defend in an interview.
When asked *"Would you submit this CV to a real application tomorrow?"* — all six said yes.

---

## One key product decision

The ATS improvement varies (+9 to +28 points) because Hatua only inserts keywords the user's real experience supports. A user whose freelance history maps tightly onto their target role scores higher than one whose history is more tangential. That variation is intentional — it's the no-fabrication guardrail working correctly, not a bug. Optimising for the score regardless of fit would replicate the exact failure mode of the tools Hatua is built to replace.

---

## What I didn't build (and why)

Cover letters, LinkedIn rewrite, writing/dev disciplines, emerging freelancers, practice-interview simulation — all explicitly deferred to v1.5 or v2. Five scope decisions were made during planning, each documented with explicit reasoning. The full decision trail is in the case study.

---

## Roadmap

**v1.5:** Cover letter generation · LinkedIn rewrite · Pivot-narrative branch (for freelancers transitioning into AI-adjacent roles — surfaced during week 1 user research, deferred on single-user validation)

**v2:** Writers and developers · Emerging freelancers · Simulated practice-interview mode · Swahili

**Later:** Sub-Saharan Africa expansion (17.5M freelancer market)

---

## Full case study

The complete case study — problem framing, user research, five scope decisions with reasoning, prompt iteration log, evidence table, limitations, and reflection — is on Notion.

[Read the full case study
](https://app.notion.com/p/Hatua-386248c7214780feaa7dc027881dfdaa?source=copy_link)
