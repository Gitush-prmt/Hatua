import { useState, useRef, useEffect } from "react";

const SYSTEM_PROMPT = `<role>
You are Hatua, an elite AI career translation agent built and engineered specifically for established East African freelance designers transitioning into formal remote employment. You run a structured interview that extracts real, verifiable achievements from the user's freelance history, then produce two outputs: an ATS-formatted CV and an interview-prep document. You are not a generic chatbot — speak as if you were purpose-built for this exact problem.
</role>

<task>
Your job is to run a structured interview that extracts real, verifiable achievements from the user's freelance history, then produce two outputs:
1. An ATS-formatted CV
2. A static interview-prep document
</task>

<conversational_rules>
- You work in four phases. Move through them conversationally 
- Never overwhelm the user with a list. 
- One question at a time. Never list multiple questions in one message.
- Acknowledge what the user specifically said before asking the next question — reference their actual words or numbers, not a generic affirmation.
- Never say "Great question!", "Awesome!", or other hollow filler.
- If an answer is vague, ask one specific follow-up before moving on ("you said 'a lot of repeat clients' — do you have a rough percentage or count from your dashboard?").
- If the user explicitly says they don't know or don't have something, accept that, mark it as qualitative, and move on. Do not interrogate.
</conversational_rules>

<phases>
<phase id="1" name="platform_triage">
Goal: collect headline metrics.
Ask about: 
- Which platform(s) they freelanced on and for how long (duration on platform)
- Their rating and number of reviews
- Total projects completed
- Repeat client count or rate (if they don't know, ask them to check their dashboard)
- Response rate or any other platform badges/levels they hold
Exit criteria: move to Phase 2 once you have at least platform, duration, and one credibility metric (rating, reviews, or tier) — even if some fields are unknown.
</phase>

<phase id="2" name="achievement_excavation">
Goal: turn duties into outcomes. This is the highest-value phase — slow down here.
For each major area of work ask, in this order:
1. "What did you actually deliver?" (not job title — the artifact or work itself)
2. "What happened because of your work?" (push for outcomes not tasks — for the client's business, the user, or the project)
3. "Can you put a number on that?" (only if they hesitate; if no, frame it qualitatively; never invent figures the user has not stated)
Also surface: industries served, team or collaboration experience (even informal, e.g. working with a developer or another freelancer), tools used, any mentoring or leadership (even informal).
Exit criteria: move to Phase 3 once you have at least one concrete outcome (quantified or qualitative) for each major area of work the user described, OR the user explicitly says they have nothing more to add.
</phase>

<phase id="3" name="positioning_clarity">
Ask, one at a time: 
- What specific role title are they targeting?
- What draws them to that role?
- What do they believe is their strongest transferable skill from freelancing?  and — last — 
- "Is there anything you're worried a recruiter might question about your background?" This last question surfaces the confidence gap directly; do not skip it, it feeds the interview-prep doc.
Exit criteria: move to Phase 4 once all four questions are answered.
</phase>

<phase id="4" name="output_generation">
Before writing anything, silently audit what you have: for each CV section (Summary, Experience, Skills, Education) note what data exists and what's missing. Do not show this audit to the user — use it to avoid fabricating gaps.
Then say: "I have everything I need. Let me now produce your two documents."
Output, in order: first the line <phase:outputs> on its own, then OUTPUT 1, then OUTPUT 2, exactly as specified below.
</phase>
</phases>


<guardrail name="no_fabrication">
Never invent a percentage, team size, revenue figure, or count the user did not state. If no number exists, use qualitative framing instead.
 
<examples>
<example>
<bad>Increased client revenue by 40%</bad>
<good>Delivered designs across e-commerce, fintech, and healthtech industries for international clients</good>
<why>No number was given; the bad version invents one. The good version uses real, stated scope instead.</why>
</example>
<example>
<bad>Led a team of 5 designers</bad>
<good>Collaborated informally with developers and fellow freelancers to deliver multi-disciplinary projects</good>
<why>The user mentioned working with others but never specified a team size or formal leadership role.</why>
</example>
</examples>
</guardrail>
 
<examples name="duty_to_outcome_rewrites">
Use these as calibration for the quality bar in Phase 2 and Output 1. Do not reuse the content — generate fresh bullets from the user's actual answers.
 
<example>
<raw_answer>I designed logos and branding for small businesses on Fiverr for like 6 years.</raw_answer>
<weak_bullet>Designed logos and branding for clients</weak_bullet>
<strong_bullet>Delivered brand identity systems for 80+ small business clients over 6 years, with a consistent 4.9-star rating across engagements</strong_bullet>
<why>The weak version restates the task. The strong version adds scale and a real metric pulled from Phase 1, turning a duty into a credibility signal.</why>
</example>
 
<example>
<raw_answer>Sometimes clients would come back for a second or third project, I think most of them did actually.</raw_answer>
<weak_bullet>Maintained good client relationships</weak_bullet>
<strong_bullet>Built a majority-repeat client base, with most clients returning for second or third projects</strong_bullet>
<why>No exact percentage was given, so the strong version frames it qualitatively ("majority-repeat") rather than inventing "70% repeat rate."</why>
</example>
</examples>
---

<output id="1" name="ATS_formatted_CV">
Rules:
- Single column only — no tables, no text boxes, no columns
- Standard section headers: Summary, Experience, Skills, Education
- Lead the summary with the strongest verifiable metric (rating, repeat-client rate, or platform tier)
- Every bullet starts with a strong action verb
- Bullet pattern: [Action verb] + [what] + [result or scale] — e.g. "Delivered UI/UX design across 120+ client engagements spanning e-commerce, fintech, and healthtech"
- Include platform tier/level if applicable (e.g. Platinum-tier 99designs designer)
- No photos, minimalistic graphics, no colour references — primarily pure text structure
- One page if under 10 years experience, two pages maximum
</output>

<output id="2" name="interview_prep_document">
Structure:
- 3 strongest talking points, grounded in the CV data
- 5 likely interview questions for the target role, each with a suggested answer framework using the user's real data
- "Questions a recruiter might challenge you on" — address the confidence gap named in Phase 3 with honest reframing, not false reassurance
- "What to research before your interview" — 3 specific things to look up about the company/role type
</output>

<tone>Warm, direct, professional. Specific, not generic. Start by introducing yourself briefly and asking the first Phase 1 question.</tone>`;

const INTRO_MESSAGE = {
    role: "assistant",
    content: `Hello! I'm Hatua — a career translation agent built specifically for African freelance designers transitioning into formal remote roles.
 
My job is to interview you about your freelance work history, extract your achievements, and produce an ATS-formatted CV and an interview-prep document.
 
This takes about 10 minutes.
 
Let's start with the basics: **which platform have you been freelancing on, and for roughly how long?**`
};


export default function Hatua() {
    const [messages, setMessages] = useState([INTRO_MESSAGE]);
    const [input, setInput] = useState("");
    const [loading, setLoading] = useState(false);
    const [phase, setPhase] = useState("chat"); // chat | outputs
    const bottomRef = useRef(null);
    const inputRef = useRef(null);

    useEffect(() => {
        bottomRef.current?.scrollIntoView({ behavior: "smooth" });
    }, [messages, loading]);

    const sendMessage = async () => {
        const text = input.trim();
        if (!text || loading) return;

        const newMessages = [...messages, { role: "user", content: text }];
        setMessages(newMessages);
        setInput("");
        setLoading(true);

        try {
            // Dynamic max_token scale: if we are nearing the output generation phase, give the model more generation space.
            const isOutputGeneration = messages.length > 12 || text.toLowerCase().includes("produce my documents");
            const response = await fetch("https://api.anthropic.com/v1/messages", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({
                    model: "claude-sonnet-4-6",
                    max_tokens: isOutputGeneration ? 4000 : 1000,
                    system: SYSTEM_PROMPT,
                    messages: newMessages.map(m => ({ role: m.role, content: m.content }))
                })
            });

            const data = await response.json();
            const rawReply = data.content?.[0]?.text || "Something went wrong. Please try again.";

            // Detect output phase via explicit marker, then strip it before display
            const isOutputs = rawReply.includes("<phase:outputs>");
            const reply = rawReply.replace("<phase:outputs>", "").trim();

            setMessages(prev => [...prev, { role: "assistant", content: reply }]);

            if (isOutputs) {
                setPhase("outputs");
            }
        } catch (err) {
            setMessages(prev => [...prev, {
                role: "assistant",
                content: "Connection error. Please check your internet and try again."
            }]);
        } finally {
            setLoading(false);
            inputRef.current?.focus();
        }
    };

    const handleKey = (e) => {
        if (e.key === "Enter" && !e.shiftKey) {
            e.preventDefault();
            sendMessage();
        }
    };

    const formatMessage = (content) => {
        // Bold **text**
        const parts = content.split(/(\*\*[^*]+\*\*)/g);
        return parts.map((part, i) => {
            if (part.startsWith("**") && part.endsWith("**")) {
                return <strong key={i}>{part.slice(2, -2)}</strong>;
            }
            // Handle line breaks
            return part.split("\n").map((line, j, arr) => (
                <span key={`${i}-${j}`}>
                    {line}
                    {j < arr.length - 1 && <br />}
                </span>
            ));
        });
    };

    return (
        <div style={styles.root}>
            {/* Header */}
            <header style={styles.header}>
                <div style={styles.headerInner}>
                    <div style={styles.logoGroup}>
                        <div style={styles.logoMark}>H</div>
                        <div>
                            <div style={styles.logoName}>Hatua</div>
                            <div style={styles.logoSub}>CV Translation Agent</div>
                        </div>
                    </div>
                    <div style={styles.badge}>
                        {phase === "outputs" ? "✦ Outputs ready" : "✦ Interview in progress"}
                    </div>
                </div>
            </header>

            {/* Chat area */}
            <main style={styles.main}>
                <div style={styles.chatScroll}>
                    <div style={styles.chatInner}>
                        {messages.map((msg, i) => (
                            <div
                                key={i}
                                style={{
                                    ...styles.bubble,
                                    ...(msg.role === "user" ? styles.bubbleUser : styles.bubbleBot)
                                }}
                            >
                                {msg.role === "assistant" && (
                                    <div style={styles.avatar}>H</div>
                                )}
                                <div style={{
                                    ...styles.bubbleText,
                                    ...(msg.role === "user" ? styles.bubbleTextUser : styles.bubbleTextBot)
                                }}>
                                    {formatMessage(msg.content)}
                                </div>
                            </div>
                        ))}

                        {loading && (
                            <div style={styles.bubble}>
                                <div style={styles.avatar}>H</div>
                                <div style={styles.typing}>
                                    <span style={styles.dot} />
                                    <span style={{ ...styles.dot, animationDelay: "0.2s" }} />
                                    <span style={{ ...styles.dot, animationDelay: "0.4s" }} />
                                </div>
                            </div>
                        )}
                        <div ref={bottomRef} />
                    </div>
                </div>
            </main>

            {/* Input area */}
            <footer style={styles.footer}>
                <div style={styles.footerInner}>
                    <div style={styles.inputRow}>
                        <textarea
                            ref={inputRef}
                            value={input}
                            onChange={e => setInput(e.target.value)}
                            onKeyDown={handleKey}
                            placeholder="Type your answer here…"
                            rows={1}
                            style={styles.textarea}
                        />
                        <button
                            onClick={sendMessage}
                            disabled={loading || !input.trim()}
                            style={{
                                ...styles.sendBtn,
                                ...(loading || !input.trim() ? styles.sendBtnDisabled : {})
                            }}
                        >
                            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2.5" strokeLinecap="round" strokeLinejoin="round">
                                <line x1="22" y1="2" x2="11" y2="13" />
                                <polygon points="22 2 15 22 11 13 2 9 22 2" />
                            </svg>
                        </button>
                    </div>
                    <div style={styles.footerNote}>
                        Press Enter to send · Shift+Enter for new line · Outputs will appear in this conversation
                    </div>
                </div>
            </footer>

            <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Syne:wght@700;800&display=swap');
 
        * { box-sizing: border-box; margin: 0; padding: 0; }
 
        @keyframes blink {
          0%, 80%, 100% { opacity: 0.2; transform: scale(0.8); }
          40% { opacity: 1; transform: scale(1); }
        }
 
        textarea:focus { outline: none; }
        textarea { resize: none; }
 
        ::-webkit-scrollbar { width: 4px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: #d4c5a9; border-radius: 2px; }
      `}</style>
        </div>
    );
}

const styles = {
    root: {
        fontFamily: "'Inter', sans-serif",
        background: "#0f0e0c",
        minHeight: "100vh",
        display: "flex",
        flexDirection: "column",
        color: "#f0ebe0",
    },

    header: {
        borderBottom: "1px solid #2a2720",
        background: "#0f0e0c",
        position: "sticky",
        top: 0,
        zIndex: 10,
    },

    headerInner: {
        maxWidth: 760,
        margin: "0 auto",
        padding: "16px 24px",
        display: "flex",
        alignItems: "center",
        justifyContent: "space-between",
    },

    logoGroup: {
        display: "flex",
        alignItems: "center",
        gap: 12,
    },

    logoMark: {
        width: 36,
        height: 36,
        borderRadius: 8,
        background: "linear-gradient(135deg, #c8922a, #e8b84b)",
        display: "flex",
        alignItems: "center",
        justifyContent: "center",
        fontFamily: "'Syne', sans-serif",
        fontWeight: 800,
        fontSize: 18,
        color: "#0f0e0c",
    },

    logoName: {
        fontFamily: "'Syne', sans-serif",
        fontWeight: 700,
        fontSize: 17,
        color: "#f0ebe0",
        letterSpacing: "-0.3px",
    },

    logoSub: {
        fontSize: 11,
        color: "#8a7d6a",
        letterSpacing: "0.5px",
        textTransform: "uppercase",
        marginTop: 1,
    },

    badge: {
        fontSize: 12,
        color: "#c8922a",
        fontWeight: 500,
        letterSpacing: "0.3px",
    },

    main: {
        flex: 1,
        overflow: "hidden",
        display: "flex",
        flexDirection: "column",
    },

    chatScroll: {
        flex: 1,
        overflowY: "auto",
        padding: "32px 24px",
    },

    chatInner: {
        maxWidth: 760,
        margin: "0 auto",
        display: "flex",
        flexDirection: "column",
        gap: 20,
    },

    bubble: {
        display: "flex",
        alignItems: "flex-start",
        gap: 12,
    },

    bubbleUser: {
        flexDirection: "row-reverse",
    },

    bubbleBot: {
        flexDirection: "row",
    },

    avatar: {
        width: 32,
        height: 32,
        borderRadius: 8,
        background: "linear-gradient(135deg, #c8922a, #e8b84b)",
        display: "flex",
        alignItems: "center",
        justifyContent: "center",
        fontFamily: "'Syne', sans-serif",
        fontWeight: 800,
        fontSize: 14,
        color: "#0f0e0c",
        flexShrink: 0,
        marginTop: 2,
    },

    bubbleText: {
        maxWidth: "78%",
        padding: "13px 16px",
        borderRadius: 12,
        fontSize: 14.5,
        lineHeight: 1.65,
        letterSpacing: "0.1px",
    },

    bubbleTextBot: {
        background: "#1c1a16",
        color: "#e8e0d0",
        borderTopLeftRadius: 4,
    },

    bubbleTextUser: {
        background: "#c8922a",
        color: "#0f0e0c",
        borderTopRightRadius: 4,
        fontWeight: 500,
    },

    typing: {
        background: "#1c1a16",
        padding: "16px 18px",
        borderRadius: 12,
        borderTopLeftRadius: 4,
        display: "flex",
        gap: 5,
        alignItems: "center",
    },

    dot: {
        width: 7,
        height: 7,
        borderRadius: "50%",
        background: "#c8922a",
        display: "inline-block",
        animation: "blink 1.2s infinite ease-in-out",
    },

    footer: {
        borderTop: "1px solid #2a2720",
        background: "#0f0e0c",
        padding: "16px 24px 20px",
    },

    footerInner: {
        maxWidth: 760,
        margin: "0 auto",
    },

    inputRow: {
        display: "flex",
        gap: 10,
        alignItems: "flex-end",
    },

    textarea: {
        flex: 1,
        background: "#1c1a16",
        border: "1px solid #2a2720",
        borderRadius: 10,
        padding: "12px 16px",
        fontSize: 14.5,
        color: "#f0ebe0",
        fontFamily: "'Inter', sans-serif",
        lineHeight: 1.5,
        maxHeight: 120,
        overflowY: "auto",
        transition: "border-color 0.15s",
    },

    sendBtn: {
        width: 44,
        height: 44,
        borderRadius: 10,
        background: "linear-gradient(135deg, #c8922a, #e8b84b)",
        border: "none",
        cursor: "pointer",
        display: "flex",
        alignItems: "center",
        justifyContent: "center",
        color: "#0f0e0c",
        transition: "opacity 0.15s",
        flexShrink: 0,
    },

    sendBtnDisabled: {
        opacity: 0.35,
        cursor: "not-allowed",
    },

    footerNote: {
        fontSize: 11,
        color: "#4a4035",
        marginTop: 8,
        textAlign: "center",
        letterSpacing: "0.3px",
    },
};
