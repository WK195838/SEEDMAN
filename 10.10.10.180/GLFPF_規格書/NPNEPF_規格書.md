# NPNEPF 檔案規格書

## 基本資訊
- 檔案名稱: NPNEPF
- 檔案類型: 實體檔案 (PF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 沖銷會計憑證檔案

## 紀錄格式
- 紀錄格式名稱: NE0
- 參考檔案: NPRF (參考欄位定義檔)
- 唯一性: UNIQUE (不允許重複記錄)

## 欄位規格
| 欄位名稱 | 參考欄位 | 資料型態 | 欄位長度 | 欄位說明 | 備註 |
|---------|---------|---------|---------|---------|------|
| NE01 | AA01 | 字元 | 2 | 部門別 | 識別部門的代碼 |
| NE02 | AF02 | 字元 | 8 | 會計憑證 | 會計憑證的識別碼 |
| NE97 | AA97 | 時間戳記 | 6 | 建立時間 | 記錄建立的時間 |
| NE98 | AA98 | 日期 | 8 | 建立日期 | 記錄建立的日期 |
| NE99 | AA99 | 字元 | 10 | 建立者 | 記錄建立者的識別碼 |

## 索引資訊
檔案的索引鍵包含以下欄位:
1. NE01 (部門別)
2. NE02 (會計憑證)

## 特殊欄位說明
1. NE01 (部門別): 
   - 識別部門的代碼，用於區分不同部門的沖銷會計憑證記錄
   - 參照GLRF中的AA01欄位定義，長度為2個字元
   - 用於與其他相關檔案進行部門層級的連結

2. NE02 (會計憑證):
   - 會計憑證的唯一識別碼
   - 參照GLRF中的AF02欄位定義，長度為8個字元
   - 用於識別特定的會計憑證記錄

3. NE97 (建立時間):
   - 記錄建立的時間
   - 參照GLRF中的AA97欄位定義，格式為6位數的時間戳記
   - 用於稽核和追蹤記錄的建立時間點

4. NE98 (建立日期):
   - 記錄建立的日期
   - 參照GLRF中的AA98欄位定義，格式為8位數的日期
   - 用於稽核和追蹤記錄的建立日期

5. NE99 (建立者):
   - 記錄建立者的識別碼
   - 參照GLRF中的AA99欄位定義，長度為10個字元
   - 用於追蹤誰建立了該筆記錄

## 檢核規則
1. 主索引鍵規則:
   - NE01 + NE02 組合必須唯一
   - 不允許重複的部門別和會計憑證組合

2. 欄位檢核:
   - NE01 (部門別) 必須是有效的部門代碼
   - NE02 (會計憑證) 必須是有效的會計憑證識別碼
   - NE97-NE99 (稽核欄位) 必須符合系統日期時間格式要求

## 相關檔案
- NPRF: 參考欄位定義檔，提供欄位的詳細資料型態和長度
- GLRF: 提供參考欄位(AA01, AF02等)的定義
- NPNBPF: A&P會計憑證檔案，與此檔案共同管理會計憑證
- NPNDPF: 年度A&P預算與實支檔案，可能參照此檔案中的會計憑證資訊
- NPNFPF: 支出年度和認證檔，與此檔案的沖銷憑證相關

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/NPNEPF.txt檔案內容產生
- NPNEPF是用於管理沖銷會計憑證資訊的檔案
- 檔案採用UNIQUE關鍵字，確保每一組部門別和會計憑證的組合都是唯一的
- 此檔案可能用於追蹤已沖銷的會計憑證，作為A&P(Accounts Payable)系統的一部分
- 檔案結構相對簡單，主要是識別憑證和追蹤記錄建立資訊
- 與NPNBPF檔案具有類似的結構，但可能針對不同的業務流程
- 此檔案在A&P系統中的主要功能是管理沖銷相關的會計憑證，協助完成憑證的生命週期管理 