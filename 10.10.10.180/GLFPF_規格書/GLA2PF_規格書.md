# GLA2PF 檔案規格書

## 基本資訊
- 檔案名稱: GLA2PF
- 檔案類型: 實體檔案 (PF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 預算固定項明細檔

## 紀錄格式
- 紀錄格式名稱: A20
- 參考檔案: GLRF
- 特性: UNIQUE (唯一索引)

## 欄位規格

| 欄位名稱 | 欄位說明 | 資料類型 | 備註 |
|---------|---------|---------|------|
| A201 | 部門別 | R | 參考GLRF檔案的定義 |
| A202 | 年度 | R | 參考GLRF檔案的定義 |
| A203 | 期別 | R | 參考GLRF檔案的定義 |
| A204 | 預算代號 | R | 參考GLRF檔案的定義 |
| A205 | 核定日期 | R | 參考GLRF檔案的定義 |
| A206 | 總金額 | R | 參考GLRF檔案的定義 |
| A207 | 金額1 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A208 | 金額2 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A209 | 金額3 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A210 | 金額4 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A211 | 金額5 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A212 | 金額6 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A213 | 金額7 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A214 | 金額8 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A215 | 金額9 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A216 | 金額10 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A217 | 金額11 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A218 | 金額12 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A219 | 金額13 | R | 參考GLRF檔案的定義，月份或其他分類的子金額 |
| A297 | 輸入時間 | R | 系統記錄用欄位 |
| A298 | 輸入日期 | R | 系統記錄用欄位 |
| A299 | 輸入者 | R | 系統記錄用欄位 |

## 主鍵欄位
- A201 (部門別)
- A202 (年度)
- A203 (期別)
- A204 (預算代號)
- A205 (核定日期)

## 索引資訊
按照以下順序建立唯一索引：
1. 部門別 (A201)
2. 年度 (A202)
3. 期別 (A203)
4. 預算代號 (A204)
5. 核定日期 (A205)

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/GLA2PF.txt檔案內容產生
- 原始檔案中的中文顯示有編碼問題，欄位說明是根據欄位名稱推測
- 所有標記為資料類型R的欄位，其實際長度和資料類型需參考GLRF檔案中的對應欄位定義
- 此檔案擴展了GLA1PF的功能，提供更詳細的預算金額分配，包含總金額和13個子金額
- 金額1至金額13可能代表12個月份的預算金額加上一個額外類別或調整項目
- 此檔案與多個邏輯檔案(如GLA2LF01、GLA2LF03)關聯，提供不同的索引和查詢方式 