# PCCCPF 檔案規格書

## 基本資訊
- 檔案名稱: PCCCPF
- 檔案類型: 物理檔案 (PF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 催收備註檔案
- 唯一性: UNIQUE (不允許重複記錄)

## 紀錄格式
- 紀錄格式名稱: CC0
- 參考檔案: GLRF (基礎參考欄位定義檔)

## 欄位規格
| 欄位名稱 | 參考欄位 | 資料型態 | 欄位長度 | 欄位說明 | 備註 |
|---------|---------|---------|---------|---------|------|
| CC01 | - | 字元 | 3 | 備註編號 | 備註分類編號 |
| CC02 | AH16 | 字元 | - | 備註 | 催收相關備註說明文字 |
| CC97 | AH97 | - | - | 建立時間 | 記錄建立時間 |
| CC98 | AH98 | - | - | 建立日期 | 記錄建立日期 |
| CC99 | AH99 | - | - | 建立者 | 記錄建立者識別碼 |

## 主鍵資訊
檔案採用以下欄位作為主鍵：
1. CC01 (備註編號)

## 檔案用途與功能
PCCCPF作為催收備註檔案，主要用途包括：
1. 儲存催收作業中常用的備註文字
2. 將備註文字標準化，便於在多個催收案件中重複使用
3. 提供催收備註的統一管理機制
4. 支援系統自動填入預設或標準備註文字

## 備註編號機制
- CC01欄位為3位文字，用於識別不同類型的催收備註
- 編號可能按照催收階段或備註用途分類，例如：
  - 001-099：催收初期備註
  - 100-199：追蹤狀態備註
  - 200-299：結案處理備註
  - 900-999：系統預設備註

## 與催收系統的關係
PCCCPF在催收系統中具有以下關係：
1. 在催收資料建立或更新過程中，可從此檔案中選取預設備註
2. 使用者可將常用備註文字儲存在此檔案中，方便日後重複使用
3. 標準備註有助於催收報表分析和統計，提高資料一致性
4. 與PCCAPF檔案中的備註欄位(CA16)相關，可作為CA16的參考來源

## 相關檔案
- PCCAPF: 催收資料主檔，其中的備註欄位可參考此檔案
- PCCBPF: 催收資料計數器檔案，與催收資料編號相關
- PCCALF01/PCCALF02: 催收資料的邏輯檢視檔案

## 備註
- 此檔案用於標準化和集中管理催收過程中常用的備註文字
- 透過唯一的備註編號(CC01)和對應的備註文字(CC02)建立關聯
- 系統可能提供介面允許使用者維護自定義備註
- 可支援系統預設備註和使用者自訂備註的混合使用
- 標準備註有助於提高催收作業的效率和一致性
- 記錄建立時間、日期和建立者，便於追蹤備註的變更歷史 