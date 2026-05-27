日常習慣「隱形開銷」與微型理財儀表板
Micro-Finance & Expense Optimizer 是一個可直接部署到 GitHub Pages 的個人理財作品。它把日常生活中的拿鐵因子、少用訂閱、外送與零碎消費，轉換成月薪分配、長期複利機會成本，以及具體的夢想 BOM 購買力。

專案內容
本 repository 分成兩個部分：

Skill 工作流程：見 SKILL.md，定義 CSV 清洗分類、時間維度標準化、複利公式與夢想 BOM 拆解。
互動式作品：見 index.html、styles.css、script.js，提供可操作的微型理財儀表板。
功能
輸入月薪、必要支出、每日/每週/每月隱形開銷。
使用滑桿調整「降級消費比例」、「年化報酬率」、「觀察年限」。
匯入日常記帳 CSV，依關鍵字自動分類必要支出與隱形開銷。
以原生 CSS conic-gradient 繪製薪資分配圓餅圖，不依賴外部 CDN。
以原生 SVG 繪製「維持現狀」與「改變習慣」的複利折線圖。
將期滿累積金額換算為曼谷自由行、高階羽球拍、雪妃爾 4 股/5 股線材與飲料提袋產量。
使用方式
直接開啟 index.html 即可使用。若部署到 GitHub Pages，不需要後端服務、建置流程或外部圖表套件。

CSV 欄位建議：

date,description,amount
2026-05-01,咖啡,80
2026-05-02,房租,16000
2026-05-03,Netflix 訂閱,390
也可以使用範例檔：

examples/sample-expenses.csv
Python CSV 清洗腳本
scripts/process_expenses.py 可在命令列中分類 CSV：

python scripts/process_expenses.py examples/sample-expenses.csv
輸出會包含必要支出、隱形開銷、其他支出、月份數與月平均摘要，方便把同一套 Skill 用在網頁之外的工作流程。

核心公式
E_month = (E_day * 30.4) + (E_week * 4.33) + E_fixed_monthly
E_year = E_month * 12
E_month_saved = E_hidden_month * downgrade_ratio
FV = E_month_saved * (((1 + r / 12)^(12n) - 1) / (r / 12))
檔案結構
.
├── index.html
├── styles.css
├── script.js
├── SKILL.md
├── README.md
├── scripts/
│   └── process_expenses.py
└── examples/
    └── sample-expenses.csv
