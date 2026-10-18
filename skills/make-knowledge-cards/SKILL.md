---
name: make-knowledge-cards
description: Convert pasted articles or local Markdown/TXT files into concise, source-faithful knowledge cards. Use when the user asks to make study cards, review cards, memory cards, knowledge cards, learning notes, or spaced-review material from an article, essay, chapter excerpt, Markdown file, or TXT file. Supports only pasted text and local .md/.txt inputs; does not support web scraping, PDF, Anki export, or graphical interfaces.
---

# Make Knowledge Cards

## Goal

Turn source material into 5–8 focused knowledge cards that help the user review the most important knowledge. Each card must teach one distinct point and stay faithful to the source.

## Inputs

- Pasted article text: use the text directly.
- Local `.md` or `.txt` file: read the complete file before producing cards.
- If the source is too long for one pass, work section by section, then deduplicate and rank all candidate cards before writing the final set.
- If the user provides a webpage link, PDF, Anki request, or GUI request, state that it is unsupported and ask for pasted text or a `.md`/`.txt` file.

## Workflow

1. Read the full source before selecting知识点.
2. Identify the source's central question, thesis, process, definitions, rules, distinctions, and conclusions.
3. Extract candidate knowledge points as short claims, not sentences copied without purpose.
4. Remove duplicates and merge closely related points. Keep one idea per card.
5. Rank points by learning value:
   - core concepts and definitions;
   - rules, mechanisms, or step-order;
   - important distinctions and common confusion;
   - conclusions supported by the source;
   - examples needed to understand an idea.
6. Produce 5–8 cards when the source supports that many distinct, important points.
7. If the source does not contain enough distinct knowledge, produce fewer cards and state that the count was reduced to avoid padding. Do not create cards from background details, trivial examples, or unsupported assumptions.
8. Check every card against the source before delivery.

## Source Fidelity Rules

- Do not add facts, definitions, numbers, causal claims, examples, or conclusions not supported by the source.
- Preserve important qualifiers, conditions, and limitations.
- Prefer the source's terminology; explain it in plain language without changing meaning.
- If a point is ambiguous, represent the ambiguity briefly instead of resolving it by guesswork.
- If the source contains an example, use it. If it does not, provide a self-test question rather than inventing an example.
- Do not include cards based only on the title, headings, or surrounding context unless the body supports them.

## Output Format

Use Markdown. Start with a one-line source summary, then list the cards.

```markdown
# 知识卡片

**来源主题：** 用一句话概括原文主题
**卡片数量：** X
**数量说明：** 少于 5 张时，用一句话说明原文缺少足够多的独立知识点；5～8 张时省略本行

## 卡片 1：[单一知识点标题]

- **核心知识：**[一句完整、可复习的知识陈述]
- **简明解释：**[用通俗语言解释该知识，通常 2–4 句；只包含原文支持的信息]
- **例子或自测问题：**
  - 例子：[来自原文的例子；没有原文例子时删除本子项]
  - 自测问题：[能检验该知识点理解的问题]

## 卡片 2：[单一知识点标题]
...
```

Use either an example or a self-test question in each card; include both only when both are source-supported and useful.

## Card Quality Checklist

Before finalizing, verify:

- [ ] 5–8 cards were produced when supported, and fewer cards were used only when necessary.
- [ ] Each card covers exactly one distinct knowledge point.
- [ ] No card repeats another card's core claim.
- [ ] Each card has a title, core knowledge, concise explanation, and an example or self-test question.
- [ ] Every factual claim is traceable to the supplied text or local `.md`/`.txt` file.
- [ ] Examples are from the source; missing examples are replaced by self-test questions.
- [ ] The cards are study-ready and do not rely on rereading the original article.
- [ ] No webpage retrieval, PDF processing, Anki export, or GUI action was attempted.
