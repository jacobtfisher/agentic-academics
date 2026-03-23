---
title: "Patterns and Anti-Patterns"
---

# Patterns and Anti-Patterns

Lessons from daily use of agentic AI tools in academic research. These are not universal rules. They are patterns that have proven useful and anti-patterns that have caused problems. Take what's relevant, discard what isn't.

## Patterns (What Works)

### Give Context Before Asking for Output

The single highest-leverage thing you can do in any Claude Code session is front-load context. Before asking for analysis, a draft, or a recommendation, make sure Claude Code has read the relevant files, understands the project status, and knows what you're trying to accomplish. A well-maintained CLAUDE.md handles much of this automatically, but for session-specific tasks, a few sentences of framing make an outsized difference.

**The pattern:** "I'm working on [project]. The current status is [X]. I need to [goal]. Before you start, read [these files]."

**Why it works:** Language models are context machines. The quality of the output is directly proportional to the quality of the input context. Five seconds of framing can save five minutes of correcting misunderstandings.

### Negative Instructions Are More Valuable Than Positive Ones

In CLAUDE.md files, skills, and prompts, telling Claude Code what *not* to do is often more informative than telling it what to do. This is because the space of reasonable positive actions is large (and Claude Code is generally good at navigating it), but the space of mistakes you've already encountered is specific and predictable.

**The pattern:** "Do NOT modify files in data/raw/. Do NOT fabricate citations. Do NOT create task checkboxes unless I explicitly ask for them."

**Why it works:** Negative instructions encode your hard-won knowledge of failure modes. They're the scar tissue of previous sessions turned into preventive measures. Every negative instruction in your CLAUDE.md is a mistake you'll never make twice.

### Build Skills From Repeated Explanations

If you've explained the same process to Claude Code more than twice, that's a signal to write a skill. The threshold for "worth encoding" is lower than you think. Even a five-line instruction set saves time over re-explaining, and the act of writing the skill often clarifies your own thinking about the workflow.

**The pattern:** Notice yourself saying "like I described last time..." or re-typing a set of instructions. Stop. Write the skill now, while the process is fresh.

**Why it works:** Skills compound. Each one raises the baseline quality of your sessions and frees conversational bandwidth for the novel parts of your work.

### Use the "Explain, Then Do" Sequence

When asking Claude Code to perform a complex task (an analysis, a restructuring, a multi-file edit), ask it to explain its plan before executing. This catches misunderstandings before they propagate through your files and gives you an opportunity to redirect.

**The pattern:** "Before you make any changes, tell me what you're planning to do and why. Then wait for my approval."

**Why it works:** The cost of a bad plan caught early is a few seconds of reading. The cost of a bad plan executed is debugging, reverting, and lost trust in the output.

### Have a Filesystem Fallback for MCP Tools

MCP integrations (Zotero, Obsidian, Notion) are powerful but imperfect. Connections time out, path resolution fails, APIs return unexpected results. If your workflow depends on an MCP tool, have a backup plan that uses direct file access.

**The pattern:** If the Obsidian MCP can't find a note, try reading it directly from the file system. If Zotero search fails, check whether the item exists by searching your local Zotero data directory. Don't tell yourself a file doesn't exist until you've tried at least two approaches.

**Why it works:** MCP servers add a layer of abstraction that can introduce its own failure modes. The underlying data is still on your machine; you just need a different path to reach it.

### Automate the Scan, Keep the Decision

For recurring maintenance tasks (deadline checks, status sweeps, note generation), automate the information gathering but keep yourself in the decision loop. The scheduled task produces a report; you decide what to do about it.

**The pattern:** Scheduled task outputs a status summary. You read it during your morning review and choose which items to act on. The task never creates tasks, sends messages, or takes action on your behalf.

**Why it works:** The bottleneck in research management is usually information gathering, not decision-making. Automating the former while preserving the latter keeps you in control without drowning in maintenance overhead.

---

## Anti-Patterns (What Doesn't Work)

### Letting AI Generate Tasks Without Your Input

AI tools are eager to be helpful, and "helpful" often means generating to-do lists, action items, and next steps. The problem is that unsupervised task generation creates clutter. Items appear in your task dashboard that you didn't ask for, don't agree with, or aren't actually important. Over time, the noise erodes trust in the system.

**The anti-pattern:** A skill or scheduled task that automatically creates checkbox tasks (`- [ ] Do this thing`) in your notes.

**The fix:** Have AI *suggest* next steps in prose or in a clearly labeled "auto-generated" section, rather than creating actionable tasks. You promote the ones that matter into real tasks manually. The extra step is worth the signal-to-noise improvement.

### Over-Granular Task Decomposition

When asked to help plan a project or break down a task, AI tends to produce exhaustively detailed checklists, ten steps where three would do. This feels productive but creates the illusion of progress without the substance. A single well-described task ("Revise the methods section: add power analysis, justify sample size, and clarify randomization procedure") is almost always better than five sub-tasks that will all be done in the same sitting.

**The anti-pattern:** "Break this task into subtasks" → a list of 12 items, most of which are steps in a single workflow.

**The fix:** Ask yourself: will these subtasks be done on different days, by different people, or with different dependencies? If not, keep it as one task with the key details in the description.

### Trusting Citations Without Verification

Language models fabricate citations. Studies have found fabrication rates ranging from roughly 14% to over 90% depending on the model and domain. Even when the citation is real, the bibliographic details (volume, page numbers, DOI) may be wrong. A hallucinated citation that survives peer review becomes part of the scientific record.

**The anti-pattern:** Asking Claude Code to "add citations to support this argument" and incorporating the results without checking each one.

**The fix:** Treat every AI-generated citation as a hypothesis. Verify it exists. Verify the details are correct. Verify it actually says what the AI claims it says. If you use a Zotero MCP, ask Claude Code to search your existing library rather than generate citations from its training data. At least then you know the paper exists and you have read it.

### Using AI for Tasks That Build Your Expertise

The line between "efficient delegation" and "counterproductive shortcutting" runs through the question: does doing this task myself build knowledge or skills I need? Data formatting doesn't. Understanding your data *does*. Generating boilerplate doesn't. Crafting an argument *does*. Writing a function to reshape a dataframe doesn't (usually). Understanding why your analysis produces unexpected results *does*.

**The anti-pattern:** Asking Claude Code to run your entire analysis pipeline and report the results, without engaging with the intermediate steps.

**The fix:** Ask Claude Code to walk you through the analysis step by step. Run each step together. Ask why results look the way they do. Use the tool to *accelerate* your understanding, not to bypass it. (See [Teach Me, Don't Do It For Me](../guides/teach-me-mindset.md).)

### Building Workflows Around a Single Tool's Quirks

Agentic AI tools are evolving rapidly. A workflow that depends on a specific Claude Code behavior, a particular MCP's idiosyncrasies, or an exact prompt formulation is fragile. When the tool updates (and it will), the workflow breaks.

**The anti-pattern:** A skill that relies on a specific error message format to detect failures, or a CLAUDE.md instruction that exploits a known model behavior that may not persist across versions.

**The fix:** Design workflows around the *principle* (scan for deadlines, surface connections, generate structured notes) rather than the *implementation detail*. When the tool changes, you update the implementation; the workflow logic survives because it's expressed at a higher level of abstraction.

### Expecting Consistency Across Sessions

Every Claude Code session starts fresh. Even with CLAUDE.md providing persistent context, the model's responses will vary across sessions for the same prompt. This is a feature of how language models work, not a bug, but it can be disorienting if you expect deterministic behavior.

**The anti-pattern:** "Last time I asked this, Claude Code gave me a different answer. Something is broken."

**The fix:** Treat variation as normal. If consistency matters for a specific task, encode the expected behavior in a skill with detailed instructions. The more precisely you specify what you want, the more consistent the output. But some variation is inherent and, in many cases, productive (different phrasings of the same idea can surface different insights).

---

*This list is maintained based on ongoing experience. Contributions welcome via PR.*
