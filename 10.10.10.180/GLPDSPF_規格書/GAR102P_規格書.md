# GAR102P 列印檔案規格書

## 基本資訊
- 檔案名稱: GAR102P
- 檔案類型: 列印檔案 (PRTF)
- 來源目錄: QDDSSRC_GLPLIB
- 程式說明: 參數日曆檔案密碼設定作業報表
- 系統: 總帳系統

## 參考檔案
- 參考檔案: GLRF (引用總帳參考欄位定義檔)

## 報表結構
報表包含四個記錄格式：
1. PH1: 報表標題與欄位標頭
2. PD1: 明細資料記錄
3. PT1: 合計線
4. PE9: 無資料訊息

## 報表佈局

### 標題區域 (PH1)
```
[公司名稱]
                                     (跳過2行)
會計參數日曆產生密碼
                                     (跳過2行)
建檔日期: [起始日期] - [結束日期]
參數日期: [起始日期] - [結束日期]
參數代碼: [起始代碼] - [結束代碼]
建檔人  : [建檔人名稱]    (可空白代表*ALL )
參數來源: [參數來源]      (可空白代表*ALL ) [來源說明]      頁次: [頁碼]
顯示內容: [顯示內容][內容說明]                                時間: [時間]    <GAR102P>
========================================================================
參數代碼 建檔日期 參數日期 更新日期 有效 版本 排序 來源      建檔人
------------------------------------------------------------------------
         說明                         成本金額      下架金額      會計科目      專案代碼1      密碼
                                      單位別       專案代碼2      日期          數量          說明
========================================================================
```

### 明細區域 (PD1)
```
[參數代碼] [建檔日期] [參數日期] [更新日期] [有效] [版本] [排序] [來源] [來源說明] [建檔人]
------------------------------------------------------------------------
[說明]    [中文說明]                    [成本金額]     [下架金額]    [會計科目]   [專案代碼1]   [密碼]
                                        [單位別]      [專案代碼2]   [日期]       [數量]        [說明]
```

### 合計線 (PT1)
```
========================================================================
```

### 無資料訊息 (PE9)
```
                無符合條件之資料
```

## 記錄格式詳細說明

### PH1 (標題與欄位標頭格式)
- 跳過前2行 (SKIPB(2))
- 每行間距設定使用SPACEA()控制

| 欄位名稱 | 參考欄位 | 說明 | 位置 | 編輯碼/格式 | 備註 |
|---------|---------|------|------|------------|------|
| #B03 | PTRF.#B03 | 公司名稱 | 1,1 | - | - |
| P25F | AH25 | 建檔日期(起) | 1,13 | EDTWRD('   /  /  ') | - |
| P25T | AH25 | 建檔日期(迄) | 1,25 | EDTWRD('   /  /  ') | - |
| P10F | AH10 | 參數日期(起) | 1,13 | EDTWRD('   /  /  ') | - |
| P10T | AH10 | 參數日期(迄) | 1,25 | EDTWRD('   /  /  ') | - |
| DAH02F | AH02 | 參數代碼(起) | 1,13 | - | - |
| DAH02T | AH02 | 參數代碼(迄) | 1,25 | - | - |
| DAH26F | AH26 | 建檔人 | 1,13 | - | - |
| DAH17F | AH17 | 參數來源 | 1,13 | - | - |
| D#Y03 | - | 來源說明 | 1,+1 | - | 長度6 |
| PDATE | - | 日期 | 1,164 | EDTCDE(Y) | 長度6,0 |
| PAGNBR | - | 頁碼 | 1,181 | EDTCDE(4) | 系統頁碼 |
| DAH19 | AH19 | 顯示內容代碼 | 1,13 | - | - |
| PFLD1 | - | 顯示內容說明 | 1,15 | - | 長度8 |
| TIME | - | 時間 | 1,164 | EDTWRD('  :  :  ') | 系統時間 |

### PD1 (明細資料格式)
- 每筆資料間距設定使用SPACEB(1)和SPACEA(1)控制

| 欄位名稱 | 參考欄位 | 說明 | 位置 | 編輯碼/格式 | 條件指示器 |
|---------|---------|------|------|------------|-----------|
| AH02 | AH02 | 參數代碼 | 1,2 | - | 32 |
| PAH25 | AH25 | 建檔日期 | 1,12 | EDTWRD('   /  /  ') | 31 |
| PAH10 | AH10 | 參數日期 | 1,22 | EDTWRD('   /  /  ') | 31 |
| PAH21 | AH21 | 更新日期 | 1,33 | EDTWRD('   /  /  ') | 31 |
| AH18 | AH18 | 有效 | 1,45 | - | 31 |
| AH19 | AH19 | 版本 | 1,51 | - | 31 |
| AH20 | AH20 | 排序 | 1,57 | - | 31 |
| AH17 | AH17 | 來源 | 1,62 | - | 31 |
| P#Y03 | - | 來源說明 | 1,65 | - | 31 |
| PSU02 | - | 建檔人 | 1,72 | - | 31 |
| PAH04 | - | 說明 | 1,12 | - | 長度10A |
| PAF03 | - | 中文說明 | 1,22 | - | 長度36 |
| AH12 | AH12 | 成本金額 | 1,59 | EDTCDE(2) | - |
| AH13 | AH13 | 下架金額 | 1,77 | EDTCDE(2) | - |
| AH05 | AH05 | 會計科目 | 1,95 | - | - |
| AH07 | AH07 | 專案代碼1 | 1,116 | - | - |
| AH16 | AH16 | 密碼 | 1,137 | - | - |
| AH06 | AH06 | 單位別 | 1,95 | - | - |
| AH08 | AH08 | 專案代碼2 | 1,116 | - | - |
| PAH09 | AH09 | 日期 | 1,137 | EDTWRD('   /  /  ') | - |
| AH14 | AH14 | 數量 | 1,147 | EDTCDE(2) | - |
| AH15 | AH15 | 說明 | 1,166 | - | - |

### PT1 (合計線格式)
- 顯示報表的分隔線
- 跳行顯示 (SPACEB(1))

### PE9 (無資料訊息格式)
- 跳行顯示 (SPACEB(1))
- 顯示訊息: "無符合條件之資料"

## 條件指示器
| 指示器 | 說明 | 用途 |
|-------|------|------|
| 31 | 資料顯示控制 | 控制明細數據的第一行顯示 |
| 32 | 參數代碼顯示控制 | 控制參數代碼欄位的顯示 |

## 編輯碼說明
| 編輯碼 | 說明 |
|-------|------|
| EDTCDE(Y) | 西元年月日格式 (YYMMDD) |
| EDTCDE(2) | 數值格式，含千位分隔符與小數點後兩位 |
| EDTCDE(4) | 無前導零、無千位分隔符的數值格式 |
| EDTWRD('   /  /  ') | 自訂日期格式，以斜線分隔 |
| EDTWRD('  :  :  ') | 自訂時間格式，以冒號分隔 |

## 資料流程
1. 報表首先印出標題區域 (PH1)，顯示報表名稱與查詢條件
2. 如有符合條件的資料，則印出資料明細 (PD1)，每筆資料占用多行
3. 資料尾端印出合計線 (PT1)
4. 如果沒有符合條件的資料，則印出無資料訊息 (PE9)

## 使用說明
1. 此報表用於列印符合指定條件的參數日曆密碼資料
2. 報表可依使用者在GAR102D螢幕中指定的條件進行篩選
3. 報表包含多種參數欄位與密碼相關數據，並以易讀格式呈現
4. 如未找到符合條件的資料，會顯示清楚的提示訊息

## 報表與螢幕的對應關係
- 此報表由GAR102D螢幕產生，接收同樣的查詢條件參數
- 報表中的「密碼」欄位顯示了參數日曆檔案的密碼設定
- 報表格式與GAR101P相似，但主要針對密碼設定功能而設計

## 備註
- 標題區顯示所有查詢條件，便於報表讀者了解資料範圍
- 明細資料分多行顯示，確保所有重要資訊都能呈現
- 日期欄位使用標準格式化顯示，提高可讀性
- 金額欄位使用EDTCDE(2)格式化，包含千位分隔符與兩位小數
- 此報表與GAR102D密碼設定螢幕搭配使用，提供完整的密碼管理功能 