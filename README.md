# dxsp02 

## Project Overview

客服每日處理大量用戶來信（LINE、網站表單、電話紀錄等），但回報格式不一致，缺乏標準分類，

導致人力成本高
回覆品質不一

無法追蹤問題趨勢：無有效的結構化資料積累

每個自動化背後，我都有設定關鍵資料點，建立結構化資料基礎，為後續分析做準備，逐步導入數據驅動的決策流程
---

## Objetives

- 自動化客服回報流程，降低人工判讀與分派負擔。
- 累積高品質、結構化的客訴資料，作為後續 BI 分析基礎。
- 提升處理效率與服務水準，讓流程從「能執行」進化為「能優化」。
- 演示如何設計具備擴充性、商業價值導向的數位轉型落地原型。
- 釐清常見問題類型分佈（TOP 5）
- kpi:平均處理時間與 SLA 完成率
- kpi:重複通報率、時間分布（高峰時段）
- kpi:各客服人員處理量與回覆效率
- 問題分類與客訴主題文字雲
---

## Project Stages
**目標1：讓客服通報轉為結構化格式，並自動分派分類與責任人**
- 工具:Typeform＋n8n
- 流程：
  客服填寫客訴表單（標準欄位：客戶ID、通路、問題類型、描述）
  表單送出 → 透過 Zapier 自動分類（根據關鍵字 rule-based）
  自動更新 Google Sheet / Trello 任務板 / Slack 通
- 價值：
  減少 30% 工時
  建立客訴結構化資料表（基礎資料點開始累積）

**目標2：數據分析與流程調整**
- 工具: BigQuery＋ Looker Studio
- 流程：
  問題類型 TOP 5、處理時間分布、重複通報率
  各客服績效統計（處理件數、回覆時效）
- 價值：
  發現問題趨勢:「80%問題集中在3類場景」→ 可以製作 FAQ 原型
  根據通報密度重新分配值班人力

**目標3：導入NLP預測與智慧指派**
- 工具: ChatGPT API（或 Huggingface 模型）＋ Webhook
- 流程：
  自動讀取敘述 → 回傳建議分類＋建議解決方案
  可提供客服複製回覆草稿
  有效件數與準確率回饋機制設計（例如客服可按 👍👎）
- 價值：
  預估可再節省 40% 的初階分類時間
  協助新客服快速上手、知識內化為模組
---

## Technical Stack

- **自動化工具**：n8n
- **表單與資料平台**：Google Sheets、Bigquery
- **資料視覺化**：Looker Studio
- **NLP 分類實驗**：Python、Huggingface、OpenAI GPT
- **API 串接**：Webhook、JSON 請求格式設計
---

## Folder Structure
```bash
customer-service-dx-transform/
├── README.md
├── .gitignore
├── CHANGELOG.md
├── docs/
│   ├── project_overview.md
│   ├── process_diagram.drawio.png
│   ├── data_model.xlsx
│   └── dashboard_sample.png
├── automation_prototypes/
│   ├── zapier_ticket_routing.png
│   └── webhook_integration_example.json
├── datasets/
│   ├── ticket_sample_data.csv
│   └── ticket_data_dictionary.md
├── dashboards/
│   └── looker_studio_dashboard_link.md
├── notebooks/
│   └── nlp_classification_demo.ipynb
├── scripts/
│   └── classifier_api_demo.py
└── notion_link.md
```
---

## Workflow Diagram 工作流程圖

---

## Environment Setup Guide 環境配置指南

略，請參考docs/.md各個環境與設定指南
---

## Project Highlights
- 資料結構設計可延伸應用於產品問題追蹤、客服知識庫建立等
- 為後續導入智慧客服、語意理解模型等提供資料基礎
---

## Follow-up Optimization

---

## 👤 Author Maintainer

- **Rex C.**
- **chanminglung126@gmail.com**
- [**Profile**](https://github.com/Rexgogo/dxsp01_brand_survey_automation.git)
- [**GitHub**](https://github.com/Rexgogo/dxsp01_brand_survey_automation.git)
- **Skills:**
  - Python/SQL
  - ETL (Airflow)
  - Data extract (Airbyte)
  - Data Modeling & Transformation (dbt, BigQuery)
  - Cloud Data Warehouse (BigQuery)
  - BI Dashboarding (Superset, Looker Studio)
  - Automation tool (Zapier, n8n)
