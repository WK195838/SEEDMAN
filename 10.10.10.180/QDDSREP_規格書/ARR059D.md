# 應收帳款系統—應收票據明細查詢顯示檔規格書（ARR059D）

## 一、基本資訊
- **顯示檔名稱**：ARR059D
- **程式名稱**：ARR059
- **作者**：D910095
- **系統**：應收帳款系統
- **子系統**：票據作業
- **功能說明**：應收票據明細查詢
- **建立日期**：1992/10/03
- **備註**：顯示查詢及列印條件畫面

## 二、顯示格式

### 1. 螢幕規格
- **螢幕大小**：24行 x 80列
- **訊息位置**：第24行
- **游標位置**：D#ROW, D#COL
- **列印功能**：支援

### 2. 功能鍵設定
- **F3**：返回前頁（CA03）
- **F4**：說明/HELP（CF04）

### 3. 標題區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 1,2 | 程式名稱 | 'ARR059' | 高亮度 |
| 1,26 | 訊息內容 | MSGCON(030 URE9999 *LIBL/REMF) | 高亮度 |
| 1,62 | 日期標籤 | '日期:' | - |
| 1,70 | 系統日期 | $EGMDY (6Y) | EDTCDE(Y) |
| 2,2 | 程式代碼 | 'SCR001' | - |
| 2,32 | 功能說明 | '票據明細查詢' | 高亮度 |
| 2,62 | 時間標籤 | '時間:' | - |
| 2,70 | 系統時間 | TIME | EDTWRD('  :  :  ') |
| 3,62 | 使用者標籤 | 'USER :' | - |
| 3,70 | 使用者代碼 | $USER (10A) | 輸出(O) |

### 4. 輸入區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 6,26 | 公司別起 | DSI01S (參照AC01) | 必填，反白 |
| 6,46 | 公司別迄 | DSI01E (2A) | 必填，反白 |
| 8,26 | 票據年月 | DSI21 (4Y) | 必填，反白，EDTCDE(Y)，(MM/YY) |
| 16,26 | 是否列印 | $EVR (1Y) | 必填，VALUES(1,2)，1-列印 2-不列印 |
| 17,26 | 列印份數 | $CPY (3Y) | 必填 |
| 18,26 | 列印機代碼 | $PRTID (2Y) | 必填，反白 |

### 5. 功能說明區
| 位置(行,列) | 說明 | 特性 |
|------------|------|------|
| 20,26 | '***請輸入查詢條件後按Enter***' | 高亮度 |
| 22,2 | '注意' | - |
| 22,10 | 'F3 =返回前頁' | - |
| 22,26 | 'F4 =說明/HELP' | - |

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
| 24,66 | 系統訊息 | MSGCON(014 UPT9999 *LIBL/PTMF) | 高亮度 |

## 三、功能說明
1. 提供應收票據明細查詢及列印作業。
2. 支援多條件查詢（公司別、票據年月等）。
3. 支援查詢結果列印與多份數設定。

## 四、資料驗證
- 各欄位格式、範圍、必填性檢查。
- 公司別、票據年月等選項有效性。

## 五、相關檔案
- **主程式**：ARR059
- **參考欄位定義檔**：RERF
- **訊息檔案**：PTMF（系統訊息）、REMF（錯誤訊息）

本規格書已依據 ARR059D.txt 製作，完整記錄 ARR059D 顯示檔結構與用途。如需調整或有其他需求，歡迎隨時告知！ 