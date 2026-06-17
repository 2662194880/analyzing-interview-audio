---
name: analyzing-interview-audio
description: Use when analyzing interview audio or call recordings, especially to transcribe business/HR interviews, distinguish interviewer and candidate voices, summarize questions and answers, diagnose interview weaknesses, and prepare next-round interview strategy.
---

# Analyzing Interview Audio

## Overview

Analyze interview recordings as evidence, not vibes. Produce a practical interview debrief: who asked what, how the candidate answered, what signals the interviewer cared about, where the candidate lost points, and what to improve next.

## Workflow

1. **Locate and preserve source audio**
   - Confirm the exact audio file and duration.
   - Do not overwrite or trim the original unless explicitly asked.
   - If a clipped version is needed, create a new file with a descriptive suffix.

2. **Transcribe locally when possible**
   - Check for local ASR tools first: `faster_whisper`, `whisper`, `vosk`, `ffmpeg`.
   - If a model/tool must be installed or downloaded, request approval before network access.
   - Prefer local transcription for privacy. Do not upload interview audio to public services unless the user explicitly asks and approves.
   - If available, use `scripts/transcribe_interview.py`.

3. **Separate speakers cautiously**
   - Label speakers by conversational role, usually `面试官` and `候选人`.
   - Use turn-taking, question/answer structure, self-introductions, and content cues.
   - State uncertainty when diarization is approximate. Do not pretend speaker separation is perfect if the tool only provides text segments.

4. **Build the interview map**
   - List the main interviewer questions in order.
   - Summarize the candidate's answer to each question.
   - Identify interviewer signals: repeated questions, long explanations, pushback, concerns, and explicit role information.
   - Extract next-round intelligence: department, role focus, work location, rotation/training, stability expectations, and culture/pressure signals.

5. **Diagnose candidate performance**
   - Lead with the highest-impact issues, not generic advice.
   - Separate content problems from delivery problems:
     - Content: unclear career logic, weak role fit, lack of examples, no metrics, wrong emphasis.
     - Delivery: long answers, filler words, evasive openings, low confidence, over-explaining.
   - Tie every critique to specific interview moments when possible.

6. **Give next-round preparation**
   - Convert weaknesses into answer templates the user can rehearse.
   - Prepare likely HRBP/business follow-up questions.
   - Include concise replacement wording for risky phrases.
   - End with the 3-5 points the candidate must remember before the next interview.

## Output Format

Use this structure unless the user asks otherwise:

1. **整体判断**
   - Pass/fail signal estimate if supported by evidence.
   - The interviewer's biggest concerns.

2. **面试信息点**
   - Department and role facts.
   - Training/rotation/location/stability signals.
   - What this means for next round.

3. **问题复盘**
   - Interviewer question -> candidate answer summary -> evaluation.

4. **不足与风险**
   - Rank by severity.
   - Include examples such as "回答太绕", "长期意愿不够坚定", "岗位理解偏泛".

5. **下次怎么说**
   - Provide polished, oral Chinese answer templates.
   - Keep answers realistic and aligned with the user's real experience.

## Interview-Specific Heuristics

- For JD Logistics / logistics operations interviews, watch for these signals:
  - Whether the role is warehouse, transport, capacity platform, middle office, or lean improvement.
  - Whether the interviewer stresses frontline rotation, hardship, stability, 2-3 year location commitment, or conversion.
  - Whether the candidate overuses "学习" instead of "贡献".
  - Whether transportation background is clearly connected to logistics operations.

- For HRBP rounds, prioritize:
  - Stability and long-term industry intent.
  - City acceptance and family support.
  - Frontline hardship acceptance.
  - Career plan clarity.
  - Values, communication style, and self-awareness.

## Common Mistakes

- Do not summarize only the transcript. The user needs diagnosis and next-step tactics.
- Do not overclaim speaker diarization accuracy when only ASR text is available.
- Do not invent experience. Reframe real experience toward the target role instead.
- Do not bury the most important concern. If the interviewer repeatedly probes stability, say so clearly.
- Do not give generic STAR advice without rewriting the user's actual answer.

## Privacy

Interview audio can include personal information and company details. Keep processing local by default, request approval for network/model downloads, and mention privacy limitations when using any external service.
