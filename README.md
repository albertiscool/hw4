# 🏋️ AI 私人健身教練 (AI Personal Fitness Coach)

基於 **AI Harness** 架構所打造的智慧化運動編排系統。

## 📝 專案簡介
多數市面上的健身應用程式只能提供固定的「罐頭課表」，無法根據使用者的突發狀況（如肌肉痠痛、時間不足、器材限制）進行動態調整。單純使用 LLM（如 ChatGPT）又容易遭遇「缺乏記憶」與「幻覺（給出危險動作）」的問題。

本專案透過實作 **AI Harness** 架構，將 LLM 升級為 **System Controller（系統控制器）**，賦予其呼叫工具（Function Calling）與記憶（Memory）的能力，打造出一個能動態評估、安全排表、並追蹤進度的 AI 代理系統（Agent）。

## ✨ 核心特色
- **動態課表生成**：根據使用者每天的狀態（時間、痠痛部位）即時調整菜單。
- **嚴格安全限制**：透過呼叫外部 Profile API 確認受傷史，確保 100% 不會推薦禁忌動作。
- **防止 AI 幻覺**：AI 必須從專業的動作庫 API (Exercise DB) 中撈取動作，禁止自行捏造危險動作。
- **長短期記憶機制**：結合 Session Memory 與關聯式資料庫，長期追蹤訓練日誌。

## 🏗️ 系統架構 (System Architecture)
本系統採用 **ReAct (Reasoning and Acting)** 框架，LLM 在進行決策前會先進行思考與環境觀察。主要組件包含：
1. **LLM System Controller**：核心大腦，負責意圖辨識與決策。
2. **AI Harness Orchestrator**：負責攔截 Function Call、執行 API、並管理狀態與資料流。
3. **Tools (功能工具)**：
   - `get_user_profile(user_id)`：獲取健康狀態與受傷史。
   - `search_exercise(muscle, equipment, max_duration)`：精準檢索專業動作。
   - `log_workout(...)`：將訓練成果寫入資料庫。

## 📁 檔案說明
* `ai_harness_report.md` / `ai_harness_report.pdf`：本專案的完整期末系統設計報告書，內含架構圖、工作流循序圖以及系統評估方法。

---
*此為深度強化學習課程作業專案。*