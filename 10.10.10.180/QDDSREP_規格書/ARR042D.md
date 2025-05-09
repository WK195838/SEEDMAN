# 應收帳款系統—匯款退票明細查詢顯示檔規格書

## 一、基本資訊
- **顯示檔名稱**：ARR042D
- **程式名稱**：ARR042
- **作者**：A1139 JANE
- **系統**：應收帳款系統
- **子系統**：帳款明細查詢
- **功能說明**：匯款退票明細查詢
- **建立日期**：81/04/08

## 二、顯示格式

### 1. 螢幕規格
- **螢幕大小**：24行 x 80列
- **訊息位置**：第24行
- **游標位置**：D#ROW, D#COL

### 2. 功能鍵設定
- **F3**：返回前頁
- **F4**：說明/HELP

### 3. 標題區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 1,2 | 程式名稱 | 'ARR042' | 高亮度 |
| 1,26 | 訊息內容 | MSGCON(030 URE9999 *LIBL/REMF) | 高亮度 |
| 1,62 | 日期標籤 | '日期:' | - |
| 1,70 | 系統日期 | $EGMDY (6Y) | EDTCDE(Y) |
| 2,2 | 程式代碼 | 'SCR001' | - |
| 2,34 | 功能標題 | '匯款退票明細查詢' | 高亮度 |
| 2,62 | 時間標籤 | '時間:' | - |
| 2,70 | 系統時間 | TIME | EDTWRD('  :  :  ') |
| 3,62 | 使用者標籤 | 'USER :' | - |
| 3,70 | 使用者代碼 | $USER (10A) | 輸出(O) |

### 4. 輸入區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 4,26 | 客戶代碼起 | DSI01S | 輸入(B)，參照SI01 |
| 4,43 | 客戶代碼迄 | DSI01E | 輸入(B)，參照SI01 |
| 6,26 | 銀行代碼起 | DSI03S | 輸入(B)，參照SI03 |
| 6,43 | 銀行代碼迄 | DSI03E | 輸入(B)，參照SI03 |
| 7,26 | 業務員代碼起 | DSI04S | 輸入(B)，參照SI04 |
| 7,43 | 業務員代碼迄 | DSI04E | 輸入(B)，參照SI04 |
| 8,26 | 期初日期起 | DSI31S | 輸入(B)，參照SI31 |
| 8,47 | 期初日期迄 | DSI31E | 輸入(B)，參照SI31 |
| 9,26 | 發票日期起 | DSI12S | 輸入(B)，參照SI12 |
| 9,47 | 發票日期迄 | DSI12E | 輸入(B)，參照SI12 |
| 10,26 | 核對日期 | DSI35 (6Y) | 輸入(B)，EDTWRD('  /  /  ') |
| 12,26 | 查詢類別 | DSEL (1A) | 輸入(B)，VALUES('A','B')，A-全部客戶，B-全部業務員 |
| 16,26 | 是否列印 | $EVR (1Y) | 輸入(B)，VALUES(1,2)，1-列印 2-不列印 |
| 17,26 | 列印份數 | $CPY (3Y) | 輸入(B) |
| 18,26 | 列印機代碼 | $PRTID (2Y) | 輸入(B) |

### 5. 功能說明區
| 位置(行,列) | 說明 | 特性 |
|------------|------|------|
| 20,27 | '***請選擇查詢條件***' | 高亮度 |
| 22,2 | '注意' | - |
| 22,10 | 'F3=返回前頁' | - |
| 22,26 | 'F4=說明/HELP' | - |

### 6. 錯誤訊息區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 24,2 | 錯誤訊息1 | ERR1 (50A) | 輸出(O)，MSGID(UPT 2140 PTMF)，高亮度 |
| 24,2 | 錯誤訊息2 | ERR2 (50A) | 輸出(O)，MSGID(UPT 2110 PTMF)，高亮度 |
| 24,2 | 錯誤訊息3 | ERR3 (50A) | 輸出(O)，MSGID(UPT 2150 PTMF)，高亮度 |
| 24,2 | 錯誤訊息4 | ERR4 (50A) | 輸出(O)，MSGID(UPT 0010 PTMF)，高亮度 |
| 24,2 | 錯誤訊息5 | ERR5 (50A) | 輸出(O)，MSGID(UPT 2010 PTMF)，高亮度 |
| 24,2 | 錯誤訊息6 | ERR6 (50A) | 輸出(O)，MSGID(UPT 0040 PTMF)，高亮度 |
| 24,2 | 錯誤訊息7 | ERR7 (50A) | 輸出(O)，MSGID(UPT 1011 PTMF)，高亮度 |
| 24,2 | 錯誤訊息8 | ERR8 (50A) | 輸出(O)，MSGID(UPT 0041 PTMF)，高亮度 |
| 24,2 | 錯誤訊息9 | ERR9 (50A) | 輸出(O)，MSGID(UPT 0011 PTMF)，高亮度 |
| 24,66 | 系統訊息 | MSGCON(014 UPT9999 *LIBL/PTMF) | 高亮度 |

## 三、功能說明

1. **主要功能**
   - 提供匯款退票明細查詢及列印作業。
   - 支援多條件查詢（客戶、銀行、業務員、日期、查詢類別等）。
   - 支援查詢結果列印與多份數設定。

2. **操作流程**
   - 輸入查詢條件（客戶、銀行、業務員、日期、查詢類別等）。
   - 按F3返回、F4說明，或執行查詢。
   - 可選擇是否列印及份數、印表機。

3. **資料驗證**
   - 各欄位格式、範圍、必填性檢查。
   - 日期欄位格式（6Y）、查詢類別/是否列印等選項有效性。

4. **特殊處理**
   - 支援HELP說明（F4）。
   - 多重錯誤訊息提示。

## 四、相關檔案

1. **相關程式**
   - ARR042：匯款退票明細查詢主程式

2. **訊息檔案**
   - PTMF：系統訊息檔案
   - REMF：錯誤訊息檔案

本規格書已依據 ARR042D.txt 製作，完整記錄 ARR042D 顯示檔結構與用途。如需調整或有其他需求，歡迎隨時告知！ 