---
name: text-humanizer-safe
description: Rewrite user-provided Chinese, English, or multilingual prose so it reads naturally while preserving facts, meaning, tone, citations, numbers, names, quotations, URLs, and claim strength. Use when the user asks to 去 AI 味、降低 AI 腔、humanize text、make writing sound natural, or revise robotic prose. Do not use for writing unrelated new content from scratch.
---

# Safe Text Humanizer

Rewrite the user's existing text in the model. Do not run scripts, install packages, call external services, or send the text to another API unless the user explicitly requests that separate action.

## Preserve the source

Treat the source's claim set as fixed:

- Keep every name, number, date, quotation, citation, URL, technical term, and code fragment accurate.
- Preserve direction and strength: “may” must not become “will”; correlation must not become causation; a recommendation must not become a requirement.
- Keep caveats, uncertainty, scope, attribution, and exceptions.
- Do not invent anecdotes, personal experience, evidence, sources, examples, or opinions.
- Do not add fake mistakes, slang, filler, or eccentric punctuation to simulate a person.
- Preserve meaningful Markdown structure and leave code blocks, formulas, commands, and data unchanged unless the user specifically asks to edit them.

When elegance conflicts with accuracy, keep the accurate version.

## Match the intended voice

Infer the language, register, audience, and purpose from the source and the user's request. Keep formal material formal and conversational material conversational. If the user provides a writing sample, follow its sentence rhythm, vocabulary level, and degree of directness without copying its facts or distinctive phrases.

For Chinese, prefer concrete verbs, ordinary connective words, and natural paragraph flow. Reduce stacked abstractions, slogan-like wording, repeated “首先／其次／最后”, empty scene-setting, forced parallelism, excessive headings, and automatic conclusions such as “综上所述” when they add nothing.

For English, reduce generic scene-setting, repeated signposting, inflated significance, synonym cycling, rigid three-part lists, excessive em dashes, canned contrasts, and stock endings. Replace them with direct sentences appropriate to the original register.

Do not mechanically ban a word or punctuation mark that is necessary, quoted, conventional in the domain, or characteristic of a user-provided voice sample.

## Rewrite method

Work silently through these checks:

1. Inventory the source's claims and immutable details.
2. Identify the structural causes of the robotic tone, including repeated sentence shapes, predictable transitions, over-sectioning, redundant summaries, and abstract phrasing.
3. Rebuild the prose freely where useful: reorder supporting sentences, merge or split paragraphs, vary sentence length, choose more direct verbs, and remove scaffolding that carries no information.
4. Compare the rewrite against the original claim by claim. Restore any omitted qualification or altered fact.
5. Read the result once for cadence. Fix remaining formulaic openings, transitions, and endings without changing content.

Prefer structural rewriting over superficial synonym replacement. Keep the result coherent; sentence-length variation should feel deliberate rather than random.

## Output

By default, return only the rewritten text, with no preface, score, detector claim, change log, or offer to continue. If the user asks for comparison, reasoning, tracked changes, or multiple variants, provide that requested format.

Never promise that a rewrite will pass an AI detector. Describe the result as a naturalness and clarity edit if the user asks about detection.
