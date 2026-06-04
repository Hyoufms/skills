# Procedure Manual Reviewer

[English](./README.en.md) | 中文

`procedure-manual-reviewer` 是一個 Codex skill，用來審閱並直接修訂 Markdown 格式的日文手順書與使用者手冊，重點放在術語一致性、操作步驟清晰度、章節編號、截圖引用與圖說格式。

## 內容

- `SKILL.md`：skill 的主要說明與工作流程。
- `agents/openai.yaml`：Codex 介面顯示名稱、簡短描述與預設提示。

## 適用場景

這個 skill 適合用在包含以下元素的 Markdown 文件：

- `# 1 xxx`、`## 1.1 xxx`、`### 1.1.1 xxx` 這類編號章節
- `1.`、`2.`、`3.` 這類操作步驟
- 截圖、圖片引用與圖說
- UI 標籤、產品名、功能名與手冊專用術語
- 需要維持原文風格，但改善一致性與可讀性的日文手順書

## 使用方式

在 Codex 中引用這個 skill：

```text
Use $procedure-manual-reviewer to review and revise this Markdown procedure manual while preserving UI labels and original style.
```

或直接請 Codex 使用 `procedure-manual-reviewer` 來審閱 / 修訂指定的 Markdown 手冊。

## 設計原則

- 優先保留原本的 Markdown 結構與書寫風格。
- 不隨意改動畫面上的 UI 標籤。
- 對術語、章節標題、操作步驟、圖片命名與圖說做局部且可追蹤的修正。
- 遇到會牽涉大量章節、交叉引用、圖片檔名或錨點的變更時，先提出方案再動手。
