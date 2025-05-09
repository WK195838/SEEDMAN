# GLR2E1W1 檔案規格書

## 檔案基本資訊
- **檔案名稱**: GLR2E1W1
- **描述**: 客戶產品類別銷售報表相關資料檔
- **參考檔案**: REF(*LIBL/GLRF)
- **記錄格式**: E1W1R

## 欄位明細

| 欄位名稱 | 欄位代號 | 資料類型 | 長度 | 小數位 | 說明 |
|---------|---------|---------|------|-------|------|
| 客戶 | E1W101 | R (參照) | 依參照欄位 | - | 參照欄位: AI01 |
| 客戶名稱 | E1W102 | R (參照) | 依參照欄位 | - | 參照欄位: #A01 PT#APF |
| 會計年度 | E1W103 | 數值(S) | 4 | 0 | 4位數會計年度 |
| 會計月份 | E1W104 | 數值(S) | 2 | 0 | 2位數會計月份 |
| 會計期間始 | E1W105 | 數值(S) | 8 | 0 | 會計期間開始日期 (可能為YYYYMMDD格式) |
| 會計期間止 | E1W106 | 數值(S) | 8 | 0 | 會計期間結束日期 (可能為YYYYMMDD格式) |
| 類別 | E1W100 | 字元(O) | 34 | - | 產品類別識別或描述 |
| 產品 | E1W107 | 字元(O) | 34 | - | 產品識別或描述 |
| 本期銷售額 | E1W108 | 數值 | 13 | 2 | 本期產品銷售金額 |
| 本期銷售額% | E1W109 | 數值 | 5 | 2 | 本期銷售額百分比 |
| 上期銷售額 | E1W110 | 數值 | 13 | 2 | 上期產品銷售金額 |
| 上期銷售額% | E1W111 | 數值 | 5 | 2 | 上期銷售額百分比 |
| 同上期差異金額 | E1W112 | 數值 | 13 | 2 | 本期與上期的銷售額差異 |
| 同上期差異金額% | E1W113 | 數值 | 5 | 2 | 本期與上期的銷售額差異百分比 |
| 預算與實際比較額 | E1W114 | 數值 | 13 | 2 | 實際銷售額與預算的差異 |
| 預算與實際比較額% | E1W115 | 數值 | 5 | 2 | 實際銷售額與預算差異的百分比 |

## 主要鍵值說明
由於DDS定義中沒有明確標示主鍵(KEY)欄位，推測可能的主鍵組合為：
- 客戶 (E1W101)
- 會計年度 (E1W103)
- 會計月份 (E1W104)
- 類別 (E1W100)
- 產品 (E1W107)

## 資料屬性說明
- R: 參照欄位，從其他檔案定義參照
- S: 帶符號的數值欄位
- O: 字元欄位

## 功能說明
此檔案主要用於儲存和呈現按客戶、產品類別和產品細分的銷售報表數據，包含各項目在不同會計期間的銷售金額、百分比及其與上期和預算的比較。與GLR2E0W1檔案相比，此檔案增加了產品類別(E1W100)欄位，提供更細緻的產品層級分類，可用於更詳細的銷售分析和績效評估。 