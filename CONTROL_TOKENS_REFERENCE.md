# HITL Swarm Control Tokens Reference

Quick guide to directing swarm thinking without re-prompting.

---

## The Six Tokens

| Token | Action | When to Use |
|-------|--------|------------|
| `▶ PROCEED` | Approve synthesis, continue | Checkpoint reasoning looks good |
| `✏ CORRECT: [text]` | Override wrong assumption | System got something factually wrong |
| `⏸ HOLD` | Stop immediately | You need to think or need more time |
| `🔍 EXPAND` | Go deeper on current path | Summary is too brief |
| `🧭 REFRAME` | Look from different angle | Current framing is incomplete or wrong |
| `⚠ FLAG` | Surface specific risks | You sense danger in current reasoning |

---

## Token Syntax

**Single token:**
```
▶ PROCEED
```

**Token with instruction:**
```
✏ CORRECT: The budget is $50K not $100K
```

**Token with context:**
```
🧭 REFRAME: Look at this from the end-user's perspective, not the company's
```

**Multiple tokens (one per line):**
```
🧭 REFRAME: Consider regulatory constraints we haven't mentioned yet
Then 🔍 EXPAND on that path
Then ▶ PROCEED
```

---

## Common Patterns

### When Reasoning Looks Good
```
▶ PROCEED
```
Simple. Approve synthesis.

### When Something's Wrong
```
✏ CORRECT: Our market size assumption is off by 50%
Then 🔍 EXPAND on how that changes the paths
Then ▶ PROCEED
```
Fix the fact, explore impact, approve.

### When You Need Different Perspective
```
🧭 REFRAME: Look at this from the customer's perspective
Then 🔍 EXPAND on that path
```
Change lens, go deeper.

### When You Sense Risk
```
⚠ FLAG: Regulatory risk in Path A
Then 🔍 EXPAND on compliance requirements
Then 🧭 REFRAME to address regulations
Then ▶ PROCEED
```
Surface danger, expand on it, reframe, approve.

### When Paths Are Unclear
```
🔍 EXPAND: Summarize each path in one paragraph with key tradeoff
```
Get clarity without restarting.

### When You're Not Ready
```
⏸ HOLD
[Think about something]
Then 🧭 REFRAME: Include X consideration
Then ▶ PROCEED
```
Pause, add information, continue.

---

## What NOT to Do

**Don't:** Re-state the whole problem
```
❌ This doesn't work well:
"Let me ask about the market analysis..."
```

**Do:** Use control tokens
```
✅ This works:
🔍 EXPAND: On market analysis specifically
```

**Don't:** Ask vague questions
```
❌ Vague:
"Is Path A good?"
```

**Do:** Be specific
```
✅ Specific:
✏ CORRECT: Path A assumes we have internal expertise, we don't
Then 🔍 EXPAND on Path B
```

**Don't:** Use multiple tokens at once in confusing ways
```
❌ Confusing:
▶ PROCEED 🧭 REFRAME ✏ CORRECT: also ⚠ FLAG
```

**Do:** Use one token per message, or combine clearly on separate lines
```
✅ Clear:
✏ CORRECT: [specific correction]
Then 🔍 EXPAND
Then ▶ PROCEED
```

---

## Practical Examples

### Example 1: Financial Analysis
```
User: "Analyze investment options"
[Swarm generates paths]
[Checkpoint]

User: ✏ CORRECT: Interest rates will be 5%, not 3%
Then 🔍 EXPAND on impact to ROI calculations
Then ▶ PROCEED
```

### Example 2: Strategic Decision
```
User: "Should we pivot to new market?"
[Swarm generates paths]
[Checkpoint]

User: 🧭 REFRAME: What if we're looking at this from investor perspective instead of founder perspective?
Then 🔍 EXPAND on that angle
Then ▶ PROCEED
```

### Example 3: Risk Assessment
```
User: "Design new system architecture"
[Swarm generates paths]
[Checkpoint]

User: ⚠ FLAG: Security vulnerabilities in Path A
Then 🔍 EXPAND: What are specific attack vectors?
Then 🧭 REFRAME: How does Path B address these?
Then ▶ PROCEED
```

### Example 4: Incomplete Information
```
User: "Recommend hiring strategy"
[Swarm generates paths]
[Checkpoint]

User: 🔍 EXPAND: On recruitment timeline constraints
Then ✏ CORRECT: Budget is $500K not $750K
Then 🧭 REFRAME: Given these constraints
Then ▶ PROCEED
```

---

## Pro Tips

**Tip 1: Use EXPAND before PROCEED**
Usually want to understand reasoning before approving.

**Tip 2: Combine CORRECT with EXPAND**
When you fix a fact, explore impact.

**Tip 3: Use REFRAME when stuck**
Different angle often unlocks new insights.

**Tip 4: FLAG specific risks**
More useful than general concern.

**Tip 5: Let system reach checkpoint**
Don't interrupt mid-reasoning. Let it pause first.

**Tip 6: One control token per message works well**
Multiple tokens on separate lines okay if chained clearly.

---

## When Each Token Shines

**▶ PROCEED**
- Checkpoint looks complete
- You've asked your questions
- You're ready for synthesis
- You approve the direction

**✏ CORRECT**
- Factual error (date, number, constraint)
- Wrong assumption revealed
- Missing constraint added
- Use when you know the fix

**⏸ HOLD**
- You need to think
- You want external input
- You need to check something
- Buying time to process

**🔍 EXPAND**
- Reasoning is too brief
- You need specifics
- Impact unclear
- Want to understand depth

**🧭 REFRAME**
- Current angle is limited
- Need different perspective
- Missing stakeholder view
- Need to challenge framing

**⚠ FLAG**
- You sense a problem
- Risk isn't surfaced
- Vulnerability exists
- Red flag in reasoning

---

## Remember

**You're directing the thinking, not responding to it.**

The system pauses at checkpoints. You guide what happens next.

Use control tokens to:
- Correct facts
- Change perspective
- Go deeper
- Surface risks
- Approve synthesis

**Short, specific, clear.**

That's all the system needs from you.
