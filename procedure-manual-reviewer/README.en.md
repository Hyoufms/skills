# Procedure Manual Reviewer

English | [繁體中文](./README.md)

`procedure-manual-reviewer` is a Codex skill for reviewing and directly revising Markdown-based Japanese procedure documents and user manuals. It focuses on terminology consistency, procedural clarity, section numbering, screenshot references, and caption formatting.

## Contents

- `SKILL.md`: The main skill instructions and workflow.
- `agents/openai.yaml`: The display name, short description, and default prompt used by Codex.

## Use Cases

This skill is useful for Markdown documents that include:

- Numbered sections such as `# 1 xxx`, `## 1.1 xxx`, and `### 1.1.1 xxx`
- Numbered procedure steps such as `1.`, `2.`, and `3.`
- Screenshots, image references, and captions
- UI labels, product names, feature names, and manual-specific terminology
- Japanese procedure documents that should keep their original writing style while improving consistency and readability

## Usage

Reference this skill in Codex:

```text
Use $procedure-manual-reviewer to review and revise this Markdown procedure manual while preserving UI labels and original style.
```

You can also ask Codex directly to use `procedure-manual-reviewer` to review or revise a specific Markdown manual.

## Design Principles

- Preserve the original Markdown structure and writing style whenever possible.
- Do not casually rewrite visible UI labels.
- Make local, traceable improvements to terminology, headings, procedure steps, image naming, and captions.
- When a change may affect many sections, cross-references, image filenames, or anchors, propose an approach before editing.
