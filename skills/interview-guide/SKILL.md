---
name: interview-guide
description: >
  Use this skill when the user asks to "create an interview guide",
  "prepare user interview questions", "plan user interviews",
  "write an interview script", "prepare for customer discovery",
  or needs help structuring conversations with users to validate
  a product hypothesis.
version: 2.0.0
---

# Interview Guide

Generate a customized user interview script using the Trail Guide framework (Warm-up → Build → Peak). Produces questions that surface real behavior and concrete past experiences — not opinions, compliments, or hypotheticals.

## When to Use

After the manager briefing, when the PM has hypotheses about user value and needs to validate through direct conversations. Also useful anytime a PM needs to run discovery interviews.

## Core Interviewing Principles

These principles must shape every question in the guide. They are non-negotiable.

### 1. Talk About Their Life, Not Your Idea

The interview is about the user's reality. The PM should never pitch, explain, or describe what they're building. Every question should explore the user's world, problems, and behavior — not test whether they like the PM's idea.

### 2. Ask About Specifics in the Past, Not Generics About the Future

Past behavior is the only reliable predictor. Generic claims ("I usually..."), future promises ("I would definitely..."), and hypothetical maybes ("I could see myself...") are unreliable. Always anchor to concrete, specific events that already happened.

### 3. Talk Less, Listen More

If the PM is talking more than the interviewee, something is wrong. The PM's job is to ask a question and then shut up. Silence is productive — it gives space for the interviewee to think and share more.

## The Trail Guide Framework

An interview is a guided hike, not a Q&A checklist. Three phases:

1. **Warm-up** (~5-10 min) — Build rapport, set expectations
2. **Build** (~10 min) — Go from broad context to specific domain
3. **Peak** (~25-30 min) — Deep dive into the problem, alternatives, severity

## Process

### Step 1: Gather Context

Ask the PM for:
- **Product/company**: What is the product?
- **Target user**: Who are you interviewing? (demographics/firmographics + product behaviors)
- **Problem hypothesis**: What problem do you believe these users have?
- **Top 3 learning goals**: The 3 most important things you want to learn from these interviews. Every conversation must address these 3 questions. At least one should be a question that could *disprove* your hypothesis.
- **Interview logistics**: Duration (default: 45 min)
- **Output format**: What format for the final document? (docx, md, or pdf). Default: docx.

If a manager briefing document exists in the workspace, offer to pull context from it.

**Challenge the PM**: If none of the 3 learning goals could potentially destroy their currently imagined product direction, push back. The scariest questions are usually the most important ones. Ask: "What would have to be true about this problem for your product to fail?" — that should be one of the 3.

### Step 2: Define Audience Strategy

Help the PM think through:
- **Primary audience**: Who exactly to talk to (specific attributes)
- **How the project audience differs from general users**: Expanding to new segment? Focusing on subset?
- **Diversity attributes**: 1-2 attributes that vary within the audience and might change behavior
- **Sample size**: ~6 interviews per audience segment as baseline. Keep talking to people until you stop hearing new information. If after 10+ conversations feedback is still all over the map, the segment is probably too broad — help the PM narrow it.

**Segment check**: If the PM's target audience is vaguely defined (e.g., "small businesses", "students", "managers"), flag this. Vague segments produce contradictory data. Help them get specific enough that they can describe where to physically *find* these people and what existing behaviors they share.

### Step 3: Generate the Interview Script

**WARM-UP (5-10 min)**

Purpose: Make the interviewee comfortable. Frame as a learning conversation, NOT as an "interview."

Include:
- Self-introduction template (who you are, who else is on the call)
- Research framing: "We're exploring [topic area] to understand how people like you experience [domain]. There are no right or wrong answers — we're just trying to learn from your real experience."
- Permission to record
- Contextual icebreaker question related to their world

**Framing guidance**: Never say "Can I interview you?" or "Thanks for agreeing to this interview" — this sets the wrong tone and makes people guarded. Frame it as a conversation about a topic you're learning about. Keep it casual and human.

**BUILD (10 min)**

Purpose: Understand the person's world before introducing the hypothesis. Confirm the big picture matters before zooming into details.

Questions from broad → specific:
1. **Life/work context** — General context related to the product domain
2. **Domain behavior** — How they currently handle the relevant area (without mentioning your product). Ask about specific recent instances, not general habits.
3. **Product-specific** — Their experience with this product category (open-ended)

Critical: Do NOT lead the interviewee toward the hypothesis. Let them surface pain points organically. If they don't mention the problem, that IS data.

**PEAK (25-30 min)**

Purpose: Deep exploration of the problem using concrete past behavior.

Four blocks:

1. **Problem validation** — Open questions about their experience with the hypothesized problem. Always ask for a specific recent story: "Walk me through the last time that happened." or "Tell me about the last time you dealt with [area]."

2. **Alternatives & workarounds** — What they do today, what they've tried before, how well it works, where it fails. Key questions to include:
   - "How are you dealing with this now?"
   - "What else have you tried?"
   - "What happened when you tried that?"

3. **Severity & motivation** — Impact on their life/work, why they bother dealing with it, consequences of not solving. Key questions:
   - "Why do you bother with this?" / "What makes this worth solving?"
   - "What are the implications of not solving it?"
   - "Talk me through what happens when this goes wrong."

4. **Underlying goals** — What they're really trying to achieve beneath the surface problem. Dig one level deeper than the first answer:
   - "Why do you want that?" (when they mention a desired outcome)
   - "What would that let you do?" (when they describe a solution they wish existed)
   - "How are you coping without it?" (when they describe something missing)

Include 2-3 "side trail" prompts for following unexpected but valuable threads.

**Closing question**: Always end with "Is there anything else I should have asked?" or "What should I have asked you that I didn't?" — this often surfaces the most important insight of the whole conversation.

**Referral question**: "Who else do you know that deals with this?" or "Who else should I talk to about this?" — every interviewee is a potential source of warm introductions to the next interviewee.

### Step 4: Add Conversation Quality Guardrails

Embed these throughout the script as practical reminders for the interviewer:

**Deflecting compliments**
If the interviewee says something positive about the PM's idea or company ("That sounds really cool!"), the PM should deflect and redirect: "Thanks — but tell me more about how you handle [topic] today." Compliments feel good but teach nothing.

**Anchoring vague claims**
When the interviewee gives a generic answer ("I usually...", "I always...", "That would be great..."), anchor it to reality:
- "When was the last time that happened?"
- "Can you walk me through a specific example?"
- "What did you actually do about it?"

**Digging beneath feature requests**
If the interviewee suggests a specific solution or feature they want, don't take it at face value. Dig into the motivation:
- "Why do you want that?"
- "What would that let you do that you can't do today?"
- "How are you managing without it?"

**Catching emotional signals**
When the interviewee shows emotion (frustration, excitement, embarrassment), that's a signal to dig deeper, not move on:
- "Tell me more about that."
- "What makes it so [frustrating/exciting/annoying]?"
- "Why haven't you been able to fix this already?"

**Avoiding the approval trap**
The PM must NOT expose their ego or stake in the hypothesis. Phrases like "We're building X, what do you think?" or "I've been working on this for months" trigger protective lies — people will tell you what you want to hear. Keep the conversation about them, not about you.

**Cutting off accidental pitches**
If the PM catches themselves explaining or defending their idea, they should stop, acknowledge it ("Sorry, I got carried away — I'm here to learn from you"), and redirect back to the interviewee's experience.

### Step 5: Add Pre-Interview Prep Checklist

**Before each conversation, the PM should know:**
- Their current top 3 learning goals (and which ones this specific person might help answer)
- What commitment or next step they want to push for at the end (if applicable)
- Basic background on this person (a quick look at their profile/role — don't waste interview time on questions you could have answered with 5 minutes of desk research)
- Best guesses about what this person cares about (you'll probably be wrong, but having a hypothesis makes it easier to notice surprises)

### Step 6: Generate the Document

Produce the document in the user's chosen format (default: docx). If docx, use the docx skill. If pdf, use the pdf skill. If md, write as markdown. Use the following structure:

```
# Interview Guide: [Project/Feature Name]
Date: [date]
Target audience: [who — be specific]
Duration: [X] min
Problem hypothesis: [1-2 sentences]

## Top 3 Learning Goals
1. [most important thing to learn]
2. [second most important]
3. [the scary question that could disprove the hypothesis]

## Pre-Interview Checklist
- [ ] Recording tool ready
- [ ] Note-taker assigned (ideal: 2 people — one talks, one writes)
- [ ] Interviewee confirmed as matching target profile
- [ ] Quiet environment confirmed
- [ ] Reviewed interviewee background (no dumb questions)
- [ ] Know what commitment/next step to push for

## Warm-up (5-10 min)
[introduction script + framing as learning conversation + icebreaker]

## Build (10 min)
### Life/Work Context
[questions — broad]
### Domain Behavior
[questions — specific recent instances]
### Product-Specific
[questions — open-ended, no leading]

## Peak (25-30 min)
### Problem Exploration
[questions — anchored to past behavior, specific stories]
### Alternatives & Workarounds
[questions — what they do today, what they've tried]
### Severity & Motivation
[questions — why it matters, consequences, urgency]
### Underlying Goals
[questions — what they're really trying to achieve]

## Conversation Guardrails
- If they give a compliment → deflect and redirect to their experience
- If they give a vague/generic answer → anchor: "When was the last time?"
- If they suggest a feature → dig into motivation: "Why do you want that?"
- If they show emotion → go deeper: "Tell me more about that"
- If you catch yourself pitching → stop, apologize, redirect
- If something unexpected comes up → follow it for 2-3 min before redirecting

## Closing
- "Is there anything else I should have asked?"
- "Who else should I talk to about this?"

## Side Trail Prompts
[follow-up questions for unexpected directions]

## Post-Interview (within 30 min)
- Write up notes with exact quotes where possible
- Tag observations: problem, workaround, goal, emotion, feature request
- Debrief with team: key learnings, surprises, what to adjust
- Update the 3 learning goals if needed
- Assess: adjust questions for next interview?
```

## Common Mistakes to Avoid

1. **Leading questions**: "Don't you think checkout is confusing?" → Instead: "Walk me through your last purchase."
2. **Discussing solutions**: The interview is about the PROBLEM. Solutions come later.
3. **Script as checklist**: If something interesting emerges, follow it. The script is a safety net, not a railroad.
4. **Skipping warm-up**: Without rapport, you get polite answers, not honest ones.
5. **Wrong people**: Validate the interviewee matches the target profile before diving in.
6. **Fishing for compliments**: "Do you think this is a good idea?" guarantees useless data. The interviewee will always say yes.
7. **Accepting fluff as data**: "I would totally use that!" is not data. "I spent 3 hours last week doing this manually" is data.
8. **Not asking scary questions**: If no question in the interview could potentially disprove the hypothesis, the interview is theater.
9. **Talking too much**: If the PM is talking more than 30% of the time, they're doing it wrong.
10. **Over-formalizing**: Treating every conversation as a formal 60-minute affair. Early conversations can be 5-10 minutes. Keep it casual.

## Question Quality Reference

**Questions that produce real data:**
- "Talk me through the last time that happened."
- "Why do you bother with [task]?"
- "What are the implications when it goes wrong?"
- "What else have you tried?"
- "How are you dealing with it now?"
- "Why do you want that?" / "What would that let you do?"
- "Who else should I talk to?"
- "Is there anything else I should have asked?"

**Questions that produce bad data (never include these):**
- "Do you think it's a good idea?"
- "Would you use a product that does X?"
- "How much would you pay for X?"
- "Do you ever [thing you hope they do]?"
- "Would you ever [thing you hope they'd do]?"
- "On a scale of 1-5, how much do you..."

## Key Principle

A great interview feels like a conversation, not an interrogation. The PM's job is to understand reality — even if reality contradicts the hypothesis. Bad news is solid learning. Lukewarm responses are data. The only useless responses are compliments and hypotheticals.
