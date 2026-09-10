# OSINT Evidence Forge（繁體中文）

[English](README.md) | [简体中文](README.zh-CN.md) | [Русский](README.ru.md) | [Українська](README.uk.md)

**面向 AI 智能體的開源情報認知衛生技能。**

OSINT Evidence Forge 是一個 [Hermes Agent](https://hermes-agent.nousresearch.com) 技能，也可作為通用 agent skill 使用。它教會 AI 智能體從異質證據中重建調查線索：聊天記錄、圖片、影片、元資料、時間線、財務資訊、交通模式與地理線索。

它的核心價值**不是**猜地點的技巧，而是一條在證據嘈雜、殘缺、自相矛盾且被後驗污染時，讓智能體保持誠實的紀律流水線：

```text
字面證據 → 來源鑑定 → 競爭假設
→ 區分度加權 → 反事實檢驗
→ 修正傳播 → 有界結論
```

## 它強制執行什麼

本技能圍繞十條**硬性不變量**構建，包括：

1. **T0/T1/H 時間邊界** —— 區分「當時已知」「後來獲得」「僅事後可知」；後見之明永不追溯性地正當化此前的決策。
2. **推斷前逐字解析** —— 限定詞、介詞、代名詞、約略語在改寫前先解析；解析一旦改變，所有依賴結論全部作廢。
3. **競爭假設帳本** —— 結論是可修訂的候選，標註支持、矛盾、前提假設與失效條件；新證據必須對*每一個*候選檢驗，絕不硬套當前最優。
4. **相容 ≠ 支持** —— 「無衝突」計零分，永不提升候選。
5. **三軸證據評分** —— 可靠性 × 區分度 × 獨立性；真實但無區分度的事實無法定位任何東西。
6. **漏斗而非鏈條** —— 結構性約束（交通、目的地、時距、人際關係）先於視覺匹配求交；結論必須通過消融測試。
7. **約束帶而非點** —— 物理測量與口頭時間估計以約束帶傳播，拒絕假精確。
8. **地理定位的預測性驗證** —— 宣布位置前，先預測該機位還應看到什麼，並逐項確認。
9. **負面證據需要覆蓋記錄** —— 「我找了沒找到」只有在記錄搜尋覆蓋範圍與可檢測性之後才算證據。
10. **安全邊界** —— 禁止騷擾、起底、無正當理由的私人精確位置；生物辨識保留為外部授權人類步驟；福利緊急情況轉交真實救援方。

## 安裝

### skills.sh（支援 Claude Code 及 40+ 種智能體）

```bash
npx skills add infinmalum/osint-evidence-forge
```

### Hermes Agent

```bash
hermes skills tap add infinmalum/osint-evidence-forge
hermes skills install infinmalum/osint-evidence-forge
```

或直接從 SKILL.md URL 安裝：

```bash
hermes skills install https://raw.githubusercontent.com/infinmalum/osint-evidence-forge/main/SKILL.md
```

### 其他智能體（Cursor 及相容 SKILL.md 的執行環境）

本技能採用標準 `SKILL.md` + `references/` 佈局，無需執行程式碼。將本倉庫指向你的執行環境技能目錄，或把 `SKILL.md` 和 `references/` 複製進其技能資料夾即可。

## 方法論來源

流程提煉自真實調查及其事後復盤，包括 Bellingcat 公開方法風格的地理定位與核驗案例研究（漸進式定位、時間定位、陰影約束、搜尋網格、來源恢復），以及一次平民福利尋人重建。不包含任何真實案件名稱、當事人、地點或資料——所有示例均為虛構。

## 安全性

本技能面向記者、研究人員、保護專業人員與合法調查者。它明確拒絕騷擾、跟蹤、起底和對私人個體未經正當理由的曝光。完整的「權限 + 手段」模型見 `SKILL.md` 中的 *Safety and Authorization Boundary* 章節。

## 授權條款

[MIT](LICENSE)
