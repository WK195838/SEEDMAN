# 應收帳款系統—應收帳款沖帳明細查詢顯示檔規格書（ARR064D）

## 一、基本資訊
- **顯示檔名稱**：ARR064D
- **程式名稱**：ARR064
- **作者**：AN MING HSIA
- **系統**：應收帳款系統
- **子系統**：沖帳明細
- **功能說明**：應收帳款沖帳明細查詢
- **建立日期**：81/11/23
- **備註**：沖帳明細查詢及列印條件畫面

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
| 1,2 | 程式名稱 | 'ARR064' | 高亮度 |
| 1,26 | 訊息內容 | MSGCON(030 URE9999 *LIBL/REMF) | 高亮度 |
| 1,62 | 日期標籤 | '日期:' | - |
| 1,70 | 系統日期 | $EGMDY (6Y) | EDTCDE(Y) |
| 2,2 | 程式代碼 | 'SCR001' | - |
| 2,30 | 畫面標題 | '沖帳明細查詢' | 高亮度 |
| 2,62 | 時間標籤 | '時間:' | - |
| 2,70 | 系統時間 | TIME | EDTWRD('  :  :  ') |
| 3,62 | 使用者標籤 | 'USER :' | - |
| 3,70 | 使用者代碼 | $USER (10A) | 輸出(O) |

### 4. 輸入區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 5,26 | 公司別起 | DAC01S (參照AC01) | 必填，反白 |
| 5,41 | 公司別迄 | DAC01E (參照AC01) | 必填，反白 |
| 7,26 | 幣別起 | DAC05S (參照AC05) | 必填，反白 |
| 7,41 | 幣別迄 | DAC05E (參照AC05) | 必填，反白 |
| 9,26 | 客戶代號起 | DAC02S (參照AC02) | 必填，反白 |
| 9,44 | 客戶代號迄 | DAC02E (參照AC02) | 必填，反白 |
| 11,46 | 發票日期起 | DAC04S (6,0) | 必填，反白，EDTWRD('  /  /  ')，(MM/DD/YY) |
| 11,57 | 發票日期迄 | DAC04E (6,0) | 必填，反白，EDTWRD('  /  /  ')，(MM/DD/YY) |

### 5. 功能說明區
| 位置(行,列) | 說明 | 特性 |
|------------|------|------|
| 20,27 | '***請輸入查詢條件後按Enter***' | 高亮度 |
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
| 24,2 | 錯誤訊息10 | ERR10 (50A) | 輸出(O)，MSGID(UPT 0041 PTMF)，高亮度 |
| 24,2 | 錯誤訊息11 | ERR11 (50A) | 輸出(O)，MSGID(URE 0081 REMF)，高亮度 |
| 24,2 | 錯誤訊息12 | ERR12 (50A) | 輸出(O)，MSGID(UPT 0011 PTMF)，高亮度 |
| 24,2 | 錯誤訊息8 | ERR8 (63A) | 輸出(O)，MSGID(URE 0051 REMF)，高亮度 |
| 24,66 | 系統訊息 | MSGCON(014 UPT9999 *LIBL/PTMF) | 高亮度 |

## 三、功能說明
1. 提供應收帳款沖帳明細查詢及列印作業。
2. 支援多條件查詢（公司別、幣別、客戶代號、發票日期等）。
3. 支援查詢結果列印與多份數設定。

## 四、資料驗證
- 各欄位格式、範圍、必填性檢查。
- 公司別、幣別、客戶代號、發票日期等選項有效性。

## 五、相關檔案
- **主程式**：ARR064
- **參考欄位定義檔**：RERF
- **訊息檔案**：PTMF（系統訊息）、REMF（錯誤訊息）

本規格書已依據 ARR064D.txt 製作，完整記錄 ARR064D 顯示檔結構與用途。如需調整或有其他需求，歡迎隨時告知！ 