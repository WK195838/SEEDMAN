# 應收帳款系統—票據明細查詢列印檔規格書（ARR057P）

## 一、基本資訊
- **列印檔名稱**：ARR057P
- **程式名稱**：ARR057
- **作者**：A1087 JOYCE
- **系統**：應收帳款系統
- **子系統**：票據作業
- **功能說明**：票據明細查詢列印
- **建立日期**：81/05/01
- **異動紀錄**：
  - 01/12/31 MICHELLE：調整資料欄位
  - 2013/12/25 DEREK：增加民國7碼日期
  - 2024/02/06 KEVIN：調整日期欄位長度為3碼
- **備註**：票據明細查詢列印格式

## 二、列印格式

### 1. 標題區
| 位置 | 欄位說明 | 格式/內容 | 特性 |
|------|---------|-----------|------|
| 頁首 | #B02 | #B02 | 參照#B02 |
| 頁首 | #B12 | #B12 | 參照#B12 |
| 頁首 | 年 | PYY (3N) | - |
| 頁首 | 月 | PMM (2N) | - |
| 頁首 | 日 | PDD (2N) | - |
| 頁首 | #B04 | #B04 | 參照#B04 |
| 頁首 | AG02 | AG02 | 參照AG02 |

### 2. 明細資料區（PD1）
| 欄位 | 格式/內容 | 說明 |
|------|-----------|------|
| SI17 | 參照SI17 | 票據號碼 |
| PSIYY | 3N | 年（民國3碼）|
| PSIMM | 2N | 月 |
| PSIDD | 2N | 日 |
| PSI02F | 2N | 幣別 |
| PSI02B | 8N | 銀行代號 |
| MA03 | 參照MA03 | 客戶名稱 |
| QTY | 參照AG05 | 數量 |
| AMT | 參照AG06 | 金額 |
| DATA1 | 10N | 資料1 |
| DATA2 | 7N | 資料2 |
| SI22D | 1N | 資料3 |
| SI22Z | 1N | 資料4 |
| SI22B | 1N | 資料5 |
| DFLD | 4N | 資料6 |

### 3. 小計/合計區（PD21, PD2）
| 欄位 | 格式/內容 | 說明 |
|------|-----------|------|
| TOTC | 11N | 小計金額 |
| TOTD | 7N | 小計數量 |
| TOTA | 11N | 合計金額 |
| TOTB | 7N | 合計數量 |

### 4. 備註區（PE1）
| 欄位 | 格式/內容 | 說明 |
|------|-----------|------|
| ME03 | 參照ME03 | 備註1 |
| MD17 | 參照MD17 | 備註2 |
| ME05 | 參照ME05 | 備註3 |
| ME06 | 參照ME06 | 備註4 |

## 三、功能說明
1. 提供票據明細查詢結果之列印。
2. 支援多條件查詢結果的明細、合計、小計列印。
3. 標題、欄位、明細、合計、備註等區塊分明，便於閱讀與核對。

## 四、資料驗證
- 各欄位格式、範圍、必填性檢查。
- 票據號碼、日期、金額、客戶、銀行代號等欄位資料正確性。

## 五、相關檔案
- **主程式**：ARR057
- **參考欄位定義檔**：RERF
- **訊息檔案**：REMF（系統訊息）

本規格書已依據 ARR057P.txt 製作，完整記錄 ARR057P 列印檔結構與用途。如需調整或有其他需求，歡迎隨時告知！ 