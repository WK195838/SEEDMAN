# 發票帳款子系統報表檔規格書

## 一、基本資訊
- **報表檔名稱**：ARA015AP
- **程式名稱**：ARA015AP
- **作者**：AN MING HSIA
- **系統**：人事薪資系統
- **子系統**：發票帳款子系統
- **功能說明**：統一發票到期處理報表
- **建立日期**：1982/03/05
- **修改記錄**：
  - M001 | MICHELLE | 990820 | 原始程式碼遺失重新修改

## 二、報表格式

### 1. 標題區 (PH1A)

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 31 | 系統標題 | MSGCON(030 URE9999 REMF) | - |
| 34 | 報表標題 | '統一發票到期處理報表' | - |
| 64 | 日期標籤 | '日期:' | - |
| 72 | 系統日期 | $EGMDY (6 0) | 輸出(O)，EDTCDE(Y) |
| 82 | 頁碼標籤 | '頁碼:' | - |
| 89 | 頁碼 | PAGNBR | EDTCDE(Z) |
| 1 | 廠商代號標籤 | '廠商代號:' | - |
| 13 | 廠商代號 | SG01 | - |
| 14 | 廠商代號 | #B03 | - |
| 64 | 時間標籤 | '時間:' | - |
| 72 | 系統時間 | TIME | - |
| 1 | 到期日期標籤 | '到期日期:' | - |
| 13 | 到期日期起 | DSG06S (6 0) | EDTWRD('  /  /  ') |
| 22 | 分隔符號 | '-' | - |
| 24 | 到期日期迄 | DSG06E (6 0) | EDTWRD('  /  /  ') |
| 64 | 使用者標籤 | 'USER :' | - |
| 72 | 使用者代碼 | $USER (10) | 輸出(O) |
| 83 | 程式名稱 | '<ARR015A>' | - |

### 2. 表頭區

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 1 | 分隔線 | '====================+' | - |
| 40 | 分隔線 | '----' | - |
| 44 | 欄位標題1 | '統一發票金額' | - |
| 54 | 分隔線 | '---' | - |
| 58 | 分隔線 | '---' | - |
| 61 | 欄位標題2 | '合計到期金額' | - |
| 73 | 分隔線 | '--' | - |
| 3 | 欄位標題3 | '本期金額' | - |
| 17 | 欄位標題4 | '上期金額' | - |
| 29 | 欄位標題5 | '本期到期' | - |
| 41 | 欄位標題6 | '本期' | - |
| 50 | 欄位標題7 | '上期' | - |
| 59 | 欄位標題8 | '本期' | - |
| 68 | 欄位標題9 | '上期' | - |
| 80 | 欄位標題10 | '合計到期日' | - |
| 1 | 分隔線 | '--------------------+' | - |

### 3. 明細區 (PD1A)

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 2 | 廠商代號 | SG09 | - |
| 16 | 廠商名稱 | SG02 | - |
| 30 | 本期金額 | SH03 | - |
| 41 | 上期金額 | SH04 | EDTCDE(J) |
| 51 | 本期到期 | SH05 | EDTCDE(J) |
| 59 | 本期金額 | USH12 | EDTCDE(J)，REFFLD(SH04) |
| 69 | 上期金額 | USH13 | EDTCDE(J)，REFFLD(SH05) |
| 76 | 備註 | '無資料可列印' | - |

### 4. 明細區 (PD2A)

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 2 | 廠商代號 | SG09 | - |
| 16 | 廠商名稱 | SG02 | - |
| 30 | 本期金額 | SH03 | - |
| 41 | 上期金額 | SH04 | EDTCDE(J) |
| 51 | 本期到期 | SH05 | EDTCDE(J) |
| 59 | 本期金額 | USH12 | EDTCDE(J)，REFFLD(SH04) |
| 69 | 上期金額 | USH13 | EDTCDE(J)，REFFLD(SH05) |
| 76 | 備註 | '無資料可列印' | - |

### 5. 表尾區 (PE1A, PE2A)

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 1 | 分隔線 | '====================+' | - |
| 2 | 結束標記 | '***結束***' | - |
| 1 | 分隔線 | '====================+' | - |
| 2 | 程式標記 | '<<ARR015A>>--->報表結束' | - |

## 三、功能說明

1. **主要功能**
   - 提供統一發票到期處理報表列印功能
   - 支援多條件查詢
   - 提供完整的報表格式

2. **報表內容**
   - 廠商基本資料
   - 統一發票金額明細
   - 合計到期金額
   - 系統資訊

3. **資料格式**
   - 日期格式：使用EDTCDE(Y)和EDTWRD('  /  /  ')
   - 金額格式：使用EDTCDE(J)和REFFLD參照
   - 頁碼格式：使用EDTCDE(Z)

4. **特殊處理**
   - 自動計算合計金額
   - 自動分頁處理
   - 日期格式化處理
   - 無資料提示處理

## 四、相關檔案

1. **參照檔案**
   - RERF：欄位參照檔案

2. **訊息檔案**
   - REMF：系統訊息檔

3. **相關程式**
   - ARA015A：統一發票到期處理主程式

這份報表檔規格書詳細說明了ARA015AP的結構和用途。作為統一發票到期處理報表的輸出介面，此檔案提供了完整的報表格式和資料處理機制，確保系統能夠有效地產生統一發票到期相關的報表。 