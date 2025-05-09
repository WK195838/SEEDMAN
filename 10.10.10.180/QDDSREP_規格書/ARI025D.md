# 應收帳款系統顯示檔規格書

## 一、基本資訊
- **顯示檔名稱**：ARI025D
- **程式名稱**：ARI025
- **作者**：A1087 JOYCE
- **系統**：應收帳款系統
- **子系統**：應收帳款子系統
- **功能說明**：分批收款明細查詢（含分批收款明細）
- **建立日期**：81/04/06
- **修改記錄**：
  - M004 00.06.12 增加稅額、分批收款欄位

## 二、顯示格式

### 1. 螢幕規格
- **螢幕大小**：24行 x 80列
- **訊息位置**：第24行
- **游標位置**：D#ROW, D#COL

### 2. 功能鍵設定
- **F3**：返回前頁
- **F12**：返回主選單

### 3. 標題區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 1,2 | 程式名稱 | 'ARI025' | 高亮度 |
| 1,26 | 訊息內容 | MSGCON(030 URE9999 *LIBL/REMF) | 高亮度 |
| 1,62 | 日期標籤 | '日期:' | - |
| 1,70 | 系統日期 | $EGMDY (6Y) | EDTCDE(Y) |
| 2,2 | 程式代碼 | 'SCR001'/'SCR002' | - |
| 2,33 | 功能標題 | '分批收款明細查詢' | 高亮度 |
| 2,62 | 時間標籤 | '時間:' | - |
| 2,70 | 系統時間 | TIME | EDTWRD('  :  :  ') |
| 3,62 | 使用者標籤 | ' USER :' | - |
| 3,70 | 使用者代碼 | $USER (10A) | 輸出(O) |

### 4. 明細列表區（主明細）
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 9,2 | 功能選項 | DOPT1 (1A) | 輸入(B)，VALUES(' ' '5') |
| 9,4 | 發票號碼 | AG03 | 輸出(O) |
| 9,15 | 客戶代碼 | AG09 | 輸出(O) |
| 9,21 | 幣別 | AG10 | 輸出(O) |
| 9,26 | 客戶名稱 | ME04 | 輸出(O) |
| 9,46 | 其他 | AG01 | 輸出(O) |

### 5. 明細列表區（分批收款明細）
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 11,2 | 發票日期 | DAG11 (6Y) | 輸出(O)，EDTWRD('  /  /  ') |
| 11,11 | 付款方式 | AG02 | 輸出(O) |
| 11,24 | 幣別 | SG02 | 輸出(O) |
| 11,37 | 金額 | AG04 | 輸出(O) |
| 11,48 | 稅額1 | AG12 (9Y) | 輸出(O)，EDTCDE(3) |
| 11,54 | 稅額2 | AG13 (9Y) | 輸出(O)，EDTCDE(3) |
| 11,59 | 稅額3 | AG06 (9Y) | 輸出(O)，EDTCDE(3) |
| 11,70 | 分批收款金額 | W0721 (9Y) | 輸出(O)，EDTCDE(3) |
| 12,68 | 分批收款金額2 | AG21 (9Y) | 輸出(O)，EDTCDE(3) |

### 6. 功能說明區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 5,4 | 功能鍵說明 | '5=明細查詢' | - |
| 7,2 | 說明 | 'A欄位內容...' | 底線(UL) |
| 22,2 | 功能說明 | '注意' | - |
| 22,10 | 功能鍵說明 | 'F3=返回前頁' | - |
| 22,26 | 功能鍵說明 | 'F12=返回主選單' | - |

### 7. 錯誤訊息區
| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 24,2 | 錯誤訊息 | DMSG (78A) | 輸出(O)，高亮度 |
| 24,2 | 錯誤訊息1-8 | ERR1-ERR8 (63A) | 輸出(O)，MSGID(UPT/URE/CPF)，高亮度 |
| 24,66 | 系統訊息 | MSGCON(014 UPT9999 *LIBL/PTMF) | 高亮度 |

## 三、功能說明

1. **主要功能**
   - 提供分批收款明細查詢介面
   - 支援明細查詢、分批收款查詢、稅額查詢等功能

2. **操作流程**
   - 選擇功能選項（查詢/分批收款查詢）
   - 輸入或查詢明細資料
   - 執行查詢

3. **資料驗證**
   - 發票號碼、客戶代碼、日期、金額、稅額等格式檢查
   - 欄位內容合理性檢查

4. **特殊處理**
   - 金額、日期格式化
   - 稅額、分批收款金額計算

## 四、相關檔案

1. **相關程式**
   - ARI025：分批收款明細查詢主程式

2. **訊息檔案**
   - PTMF：系統訊息檔案
   - REMF：錯誤訊息檔案

這份顯示檔規格書詳細說明了ARI025D的結構和用途。作為分批收款明細查詢的顯示介面，此檔案提供了完整的查詢、稅額處理與錯誤處理機制，確保系統能夠有效地查詢與管理分批收款資料。 