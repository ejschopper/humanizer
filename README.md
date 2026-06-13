# Humanizer

A Claude Code and OpenCode skill for turning AI-sounding text into plain, specific, human writing.

Humanizer does two jobs:

1. Removes common AI-writing tells.
2. Rebuilds the draft using plain English rules: active voice, concrete language, observed detail, brevity, and common punctuation.

The default style is direct, practical, and clear. The final output avoids em dashes and en dashes. It prefers common punctuation: `.`, `,`, `:`, `;`, and `-`.

## Installation

### Claude Code

Clone directly into Claude Code's skills directory:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/ejschopper/humanizer.git ~/.claude/skills/humanizer
```

Or copy the skill file manually if you already have this repo cloned:

```bash
mkdir -p ~/.claude/skills/humanizer
cp SKILL.md ~/.claude/skills/humanizer/
```

### OpenCode

Clone directly into OpenCode's skills directory:

```bash
mkdir -p ~/.config/opencode/skills
git clone https://github.com/ejschopper/humanizer.git ~/.config/opencode/skills/humanizer
```

Or copy the skill file manually if you already have this repo cloned:

```bash
mkdir -p ~/.config/opencode/skills/humanizer
cp SKILL.md ~/.config/opencode/skills/humanizer/
```

> Note: OpenCode also scans `~/.claude/skills/` for compatibility, so if you use both tools, a single clone into `~/.claude/skills/humanizer/` is enough.

## Usage

### Claude Code

```text
/humanizer

[paste your text here]
```

### OpenCode

```text
/humanizer

[paste your text here]
```

Or ask the model to humanize text directly:

```text
Please humanize this text: [your text]
```

## Voice calibration

To match a personal writing style, provide a sample:

```text
/humanizer

Here is a sample of my writing for voice matching:
[paste 2-3 paragraphs]

Now humanize this text:
[paste AI text]
```

The skill will analyze sentence rhythm, word choice, paragraph habits, and punctuation. It will still apply the default punctuation policy unless you explicitly ask otherwise.

## What changed in v3

Version 3 shifts Humanizer from an AI-detector cleanup prompt into a plain English editing skill.

It now includes:

- A strict no em dash and no en dash final audit.
- A common-punctuation policy: `.`, `,`, `:`, `;`, and `-`.
- Active voice rules.
- Positive-form rules.
- Concrete-language rules.
- Omit-needless-words rules.
- Observation-before-interpretation rules.
- Specific-detail-over-abstraction rules.
- Theatrical punctuation and fake-candid opener detection.
- Practical writing defaults for emails, documentation, technical notes, incident reviews, PRDs, and architecture reviews.

## Pattern categories

### AI writing tells

- Significance inflation.
- Promotional language.
- Superficial `-ing` analysis.
- Vague attribution.
- Formulaic challenges and future outlook.
- AI vocabulary clusters.
- Copula avoidance.
- Rule of three overuse.
- Synonym cycling.
- False ranges.
- Chatbot artifacts.
- Sycophantic tone.
- Generic conclusions.

### Style and cadence tells

- Em dashes and en dashes.
- Decorative punctuation.
- Boldface overuse.
- Inline-header lists.
- Title Case headings.
- Emojis.
- Curly quotes.
- Hyphenated word pair overuse.
- Persuasive authority tropes.
- Signposting announcements.
- Fragmented headers.
- Diff-anchored writing.
- Manufactured punchlines.
- Aphorism formulas.
- Conversational rhetorical openers.
- Theatrical punctuation.

### Plain English rewrite rules

- Use active voice when the actor matters.
- Put statements in positive form.
- Use definite, specific, concrete language.
- Omit needless words.
- Keep related words together.
- Put emphasis at the end when useful.
- Write with nouns and verbs.
- Do not overwrite.
- Do not overstate.
- Avoid empty qualifiers.
- Be clear.

### Observation-first rules

- Say what happened before explaining what it means.
- Prefer examples over conclusions.
- Prefer specific detail over abstract commentary.
- Prefer evidence over adjectives.
- Do not perform intelligence. Make the sentence useful.

## Full example

Before:

> Great question. AI-assisted coding serves as a pivotal moment in the rapidly evolving software development landscape, showcasing how teams can unlock creativity, enhance collaboration, and drive innovation. It is not just about autocomplete. It is about transforming the way developers work. The future looks bright.

After:

> AI coding assistants can speed up repetitive work: config files, test scaffolds, boilerplate, and small refactors. They are less reliable for architecture and debugging. The risk is that a suggestion can look right, pass lint, and still miss the point. Treat the tool like autocomplete, review every line, and keep tests in place.

## References

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup)
- Strunk and White, `The Elements of Style`
- Anne Lamott, `Bird by Bird`

## Version history

- **3.0.0** - Added plain English rewrite rules, observation-first rules, strict common-punctuation policy, no em/en dash final audit, theatrical punctuation detection, and practical writing defaults inspired by Strunk and White and Anne Lamott.
- **2.8.0** - Added style/cadence patterns for manufactured punchlines, aphorism formulas, and conversational rhetorical openers.
- **2.7.0** - Added diff-anchored writing and stricter em/en dash handling.
- **2.6.0** - Consolidated workflow sections and condensed the worked example.
- **2.5.1** - Added passive voice and subjectless fragment rule.
- **2.5.0** - Added persuasive framing, signposting, fragmented headers, and tighter filler rules.
- **2.4.0** - Added voice calibration.
- **2.3.0** - Added hyphenated word pair overuse.
- **2.2.0** - Added final AI audit and second-pass rewrite prompt.
- **2.1.0** - Added before/after examples.
- **2.0.0** - Rebuilt around Wikipedia's Signs of AI writing.
- **1.0.0** - Initial release.

## License

MIT
