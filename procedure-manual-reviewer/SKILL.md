---
name: procedure-manual-reviewer
description: Review and directly revise Markdown-based Japanese procedure documents, 手順書, and user manuals. Use when editing manuals with numbered header sections, numbered procedure steps, screenshots, image references, captions, terminology consistency checks, UI-label preservation, terminology table maintenance, and original writing style preservation.
---

# Procedure Manual Reviewer

## Purpose

Use this skill to review and directly modify Markdown-based 手順書 or ユーザーマニュアル.

The document usually contains:

- Numbered header-based sections such as `# 1 xxx`, `## 1.1 xxx`, `### 1.1.1 xxx`
- Large sections under headers
- Numbered procedure steps such as `1.`, `2.`, `3.`
- Screenshot image references and captions
- Repeated operation terms, UI terms, product names, and manual-specific wording

The goal is to improve terminology consistency and procedural clarity while preserving the original Markdown structure and writing style.

## Core Rules

Directly modify the Markdown when the user asks for revision.

Preserve the existing header hierarchy unless restructuring is explicitly requested.

Apply small, local numbering and formatting fixes directly. When a change would affect many sections, cross-references, image filenames, or existing anchors, stop and ask the user with a concise proposed approach before editing.

Keep terminology consistent across headers and numbered procedure steps.

Preserve the original writing style, including tone, sentence endings, and level of formality.

Do not normalize literal UI labels unless the user confirms the UI label itself should change.

Treat button names, menu names, screen names, tab names, field labels, system messages, and other displayed UI text as fixed terms.

Prefer minimal edits that improve consistency, clarity, and manual quality.

Prefer the standard manual format unless the user provides a different project convention:

```markdown
# 1 xxx
## 1.1 xxx
### 1.1.1 xxx
1. xxx
2. xxx
```

Do not run Markdown formatters or whitespace cleanup that may remove intentional image-line trailing spaces.

## Workflow

Follow this editing order:

1. Inspect the manual structure.
2. Locate or create the terminology table.
3. Identify fixed UI terms.
4. Extract terminology candidates.
5. Decide preferred terms.
6. Review and edit headers.
7. Review and edit procedure steps.
8. Check procedure continuity.
9. Check grammar and spelling.
10. Check Markdown syntax.
11. Check header and procedure numbering.
12. Check images and captions.
13. Preserve Markdown and non-text elements.
14. Prepare the final output.

### 1. Inspect the Manual Structure

Identify:

- Document title
- Major sections
- Subsections
- Numbered procedure blocks
- Screenshot image references and captions
- Existing terminology table or glossary
- Notes, warnings, tables, links, screenshots, and code blocks

Do not edit before understanding the document's structure and style.

### 2. Locate or Create the Terminology Table

If a terminology table or glossary already exists, use it as the source of truth and update it as needed.

If no terminology table exists, create one when terminology consistency work is requested.

Keep the terminology table focused on target-system-specific terms, product concepts, feature names, abbreviations, and technical domain terms.

Do not fill the terminology table with broad generic operation words such as "click", "select", "create", or "delete" unless the user explicitly wants those terms governed by the table.

Use this format for the terminology table that appears in the actual manual:

| Preferred Term | Definition / 名詞解釈 |
|---|---|
| ワークフロー | データを処理・変換するための一連の処理フロー。 |
| LLM | 大規模言語モデルを指す技術用語。 |
| データセット | ナレッジや処理対象データをまとめた単位。 |

These entries are examples only. If the target system is Dify, terms such as `ワークフロー`, `LLM`, and `データセット` may be appropriate. For other target systems, infer or ask for the relevant product-specific terms instead of reusing these examples.

The table may include:

- Target-system concepts
- Product-specific feature names
- Technical abbreviations
- Domain-specific Japanese translations
- Short noun definitions for each term

Keep UI labels out of the terminology table unless they are also target-system-specific concepts or the existing table already includes UI labels.

When adding or updating a terminology table entry, include a concise noun definition that explains what the term means in the target system. Keep definitions factual and short; do not turn them into procedural instructions.

If a UI label differs from a preferred term, preserve the UI label in operation steps. Use the terminology table to define concepts, not to rewrite visible UI strings.

### 3. Identify Fixed UI Terms

Before editing terminology, identify terms that appear to be literal UI labels.

Examples:

- Button labels
- Menu labels
- Screen names
- Tab names
- Dialog titles
- Form field labels
- System messages
- Error messages

Preserve these terms even if they differ from the preferred terminology.

If uncertain whether a term is a UI label, do not change it silently. Flag it or ask the user.

### 4. Extract Terminology Candidates

Collect repeated terms from:

- Headers
- Numbered steps
- Tables
- Notes
- Procedure descriptions
- Captions
- Existing glossary

For the terminology table, focus on target-system-specific terms such as:

- Feature names
- Screen names
- Product names
- Product-specific role names
- Status names
- Object names
- Technical abbreviations
- Domain-specific concepts

Examples:

- LLM / 大規模言語モデル
- dataset / データセット
- workflow / ワークフロー
- embedding / 埋め込み

Check generic operation wording separately for consistency, but do not automatically add it to the terminology table.

Examples of generic operation wording to check outside the terminology table:

- クリック / 選択 / 押下
- 登録 / 作成 / 追加
- 削除 / 取消 / キャンセル

### 5. Decide Preferred Terms

When choosing preferred terms, prioritize in this order:

1. Existing terminology table or glossary
2. User-provided terminology rules
3. Literal UI labels
4. Target-system official wording when available in the document
5. Most common usage in headers
6. Most common usage in procedure steps
7. Manual style and context

Record target-system-specific terminology decisions in the terminology table.

For generic wording decisions, apply consistent edits in the manual text and mention the decision in the final summary only when it materially affects the document.

If two terms are equally valid and no source of truth exists, keep the current wording and ask the user.

### 6. Review and Edit Headers

Check headers for:

- Terminology consistency
- Same feature names
- Same object names
- Consistent naming style within the same header level
- Alignment with the terminology table

Preserve the original header style where possible.

Examples of patterns to keep consistent:

- `ユーザーを作成する`
- `ユーザー作成`
- `ユーザーの作成`

Do not force a new style across the document unless the existing style is clearly inconsistent.

### 7. Review and Edit Procedure Steps

For each numbered procedure, check:

- Same operation uses the same verb
- Same object uses the same term
- UI labels are preserved
- Steps remain clear and action-oriented
- Numbered list syntax remains valid
- The original sentence style is maintained

Examples:

- Keep `「保存」をクリックします。` if the document uses quoted UI labels.
- Keep `保存ボタンを押下します。` if that is the document's established style.
- Do not change `「保存」` to `「登録」` merely for terminology consistency.

### 8. Check Procedure Continuity

Check continuity between adjacent procedure steps and related sections.

Confirm that:

- Each step starts from the state produced by the previous step.
- Objects, screens, files, users, settings, or other targets used in a step were introduced earlier.
- Required selections, inputs, confirmations, or prerequisites are not skipped.
- The screen or system state does not jump unexpectedly.
- The result of a procedure section provides a reasonable starting point for the next related section.
- Preconditions are added when a procedure depends on a prior setup or state.

When continuity is broken, add the minimum missing step, precondition, or transition sentence while preserving the original writing style.

Ask the user before adding speculative steps if the missing operation cannot be inferred from the surrounding manual or screenshots.

### 9. Check Grammar and Spelling

Check grammar and spelling while preserving the original writing style.

Confirm that:

- Japanese grammar, particles, and sentence endings are natural for the document's existing style.
- Sentences are complete and do not omit required subjects, objects, or conditions when that omission would make the procedure unclear.
- Product names, target-system terms, technical terms, abbreviations, and English words are spelled consistently.
- Katakana, kanji, full-width, and half-width forms are consistent when they refer to the same term.
- Corrections do not rewrite literal UI labels or change the intended operation.

Fix clear grammar and spelling errors directly. When a correction may change meaning, flag it or ask the user instead of guessing.

### 10. Check Markdown Syntax

Check Markdown syntax separately from grammar and spelling.

Confirm that:

- Headings, numbered lists, bullet lists, tables, links, images, emphasis, and code blocks remain valid Markdown.
- Table rows contain the expected number of cells and still render as a table.
- List indentation does not accidentally change nesting.
- Code fences are balanced and code block contents are not edited unless requested.
- Link and image syntax uses valid brackets, parentheses, and paths.
- Intentional image-line trailing spaces are preserved.

Fix clear Markdown syntax errors directly, but do not run broad formatters that may remove intentional spacing or alter unrelated Markdown.

### 11. Check Header and Procedure Numbering

Prefer this section numbering pattern:

```markdown
# 1 xxx
## 1.1 xxx
### 1.1.1 xxx
```

Check that:

- Header numbers follow the hierarchy.
- `##` numbers belong under the current `#` number.
- `###` numbers belong under the current `##` number.
- Header numbering does not skip unexpectedly.
- Numbered procedure steps under each section use `1.`, `2.`, `3.`.

Correct obvious local numbering inconsistencies when editing the document.

Ask the user before large renumbering if the document appears to have intentional gaps, cross-references, image filename dependencies, anchors, or links that depend on existing numbers.

### 12. Check Images and Captions

For images inside a procedure section, check both the referenced Markdown image and the actual image filename.

Resolve relative image paths from the directory that contains the Markdown manual, not from the current shell working directory.

Use the current procedure section number as the filename prefix. For an image under `### 1.1.1 xxx`, use:

```text
1.1.1-1xxxx.png
1.1.1-2xxxx.png
```

The number after `-` is the image sequence number within the same procedure section. Use `-1`, `-2`, `-3`, and so on when the same procedure section contains multiple images.

Check that:

- The image reference points to an existing file when the file is available in the workspace.
- The referenced filename exactly matches the actual image filename.
- The filename prefix matches the containing procedure section number.
- The sequence number after `-` is correct within the same procedure section.
- The image extension matches the actual file extension.
- The filename remains readable after the sequence number, for example `1.1.1-1login-screen.png`.

Require a caption immediately below each image.

Use this format:

```markdown
![xxxx](1.1.1-1xxxx.png) 
*xxxx*
```

Keep a trailing space after the image reference line so the caption starts on the next line according to the project convention.

Treat the image reference line's trailing space as intentional. Do not remove it during cleanup or formatting.

When the caption is missing, add one if the image context makes the caption clear. If the caption cannot be inferred safely, flag it for the user.

### 13. Preserve Markdown and Non-Text Elements

Preserve:

- Markdown links
- Image paths
- Anchors
- Code blocks
- Tables
- Frontmatter
- HTML blocks
- Screenshot references

Only edit these when the user explicitly requests it or when terminology inside visible manual text must be corrected.

### 14. Final Output

After editing, provide:

- Summary of what changed
- Updated or created terminology table location
- Any terms intentionally left unchanged because they appear to be UI labels
- Any procedure continuity fixes, added preconditions, or unresolved continuity questions
- Any grammar, spelling, or Markdown syntax corrections
- Any image filename, reference, or caption corrections
- Any unresolved terminology questions

If the user asks for review only, provide findings and proposed edits without modifying the file.

## Review Checklist

Before finalizing, confirm:

- Existing terminology table was used if present
- New terminology table was created if none existed
- UI labels were preserved
- Header terminology is consistent
- Header numbering follows `# 1`, `## 1.1`, `### 1.1.1`
- Procedure-step terminology is consistent
- Procedure continuity is preserved between adjacent steps and related sections
- Required preconditions, selections, inputs, and confirmations are not skipped
- Grammar and spelling were checked without changing the original style
- Product names, technical terms, abbreviations, and English words are spelled consistently
- Markdown syntax remains valid
- Tables, lists, links, images, emphasis, and code blocks still render correctly
- Procedure steps use `1.`, `2.`, `3.` numbering
- Original writing style was preserved
- Markdown structure is unchanged
- Numbered lists remain valid
- Image filenames match the containing section number and sequence pattern
- Image references point to the correct files
- Each image has an immediate caption line
- Image reference lines include the trailing space required by the project convention
- Relative image paths were resolved from the manual file's directory
- Links, images, tables, and code blocks are intact
- Ambiguous terminology decisions are reported

## Ambiguity Handling

Ask the user when:

- A term may be a UI label but is not clearly marked
- Existing terminology table conflicts with visible UI labels
- Multiple preferred terms are equally plausible
- A missing procedure step cannot be inferred safely
- The expected starting state for a section is unclear
- A grammar or spelling correction may change the intended meaning
- Markdown syntax appears intentionally unusual or tool-specific
- Image caption text cannot be inferred from surrounding context
- Image numbering conflicts with intentional cross-references or an existing naming rule
- A large stylistic rewrite would be needed
- The manual mixes styles and no dominant original style exists

If the user does not specify, preserve the original style and make only consistency-focused edits.
