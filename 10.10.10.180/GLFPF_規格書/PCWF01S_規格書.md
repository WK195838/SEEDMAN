# PCWF01S 檔案規格書

## 基本資訊
- 檔案名稱: PCWF01S
- 檔案類型: 工作檔案 (Work File, 含排序)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 催收工作處理排序檔案

## 紀錄格式
- 紀錄格式名稱: CA0
- 參考檔案: PCCAPF (催收資料檔)

## 欄位規格
| 欄位名稱 | 參考欄位 | 資料型態 | 欄位長度 | 欄位說明 | 備註 |
|---------|---------|---------|---------|---------|------|
| CA01 | 參考PCCAPF | 字元 | - | 部門別 | 識別部門的代碼 |
| CA02 | 參考PCCAPF | 字元 | 9 | 催收資料編號 | 格式：C-X-XXXX-XXX (C-處理步-西元年-流水號) |
| CA03 | 參考PCCAPF | 字元 | - | 年度 | 會計年度 |
| CA04 | 參考PCCAPF | 字元 | - | 會計期間 | 會計期間識別 |
| CA05 | 參考PCCAPF | 字元 | - | 供應商代號 | 供應商識別碼 |
| CA05L | - | 字元 | 3 | 供應商代號前三碼 | 供應商前綴部分 |
| CA05A | 參考PCCAPF | 字元 | - | 性質代碼 | 供應商性質分類 |
| CA06 | 參考PCCAPF | 字元 | - | 客戶代號 | 客戶識別碼 |
| CA06A | 參考PCCAPF | 字元 | - | 性質代碼 | 客戶性質分類 |
| CA07 | 參考PCCAPF | 字元 | - | 會計科目1 | 主要會計科目 |
| CA07A | 參考PCCAPF | 字元 | - | 性質代碼 | 科目性質分類 |
| CA08 | 參考PCCAPF | 字元 | - | 會計科目2 | 次要會計科目 |
| CA08A | 參考PCCAPF | 字元 | - | 性質代碼 | 科目性質分類 |
| CA09 | 參考PCCAPF | 字元 | - | 幣別 | 交易幣別 |
| CA09A | 參考PCCAPF | 字元 | - | 性質代碼 | 幣別性質分類 |
| CA10 | 參考PCCAPF | 日期 | - | 入帳日期 | 入帳處理日期 |
| CA11 | 參考PCCAPF | 日期 | - | 到期日期 | 催收款項到期日 |
| CA12 | 參考PCCAPF | 數值 | - | 催收金額 | 需要催收的金額 |
| CA13 | 參考PCCAPF | 數值 | - | 到期金額 | 已到期應收的金額 |
| CA14 | 參考PCCAPF | 數值 | - | 數量 | 相關交易數量 |
| CA14A | 參考PCCAPF | 字元 | - | 性質代碼 | 數量性質分類 |
| CA15 | 參考PCCAPF | 字元 | - | 其他 | 其他相關資訊 |
| CA15A | 參考PCCAPF | 字元 | - | 性質代碼 | 其他資訊分類 |
| CA16 | 參考PCCAPF | 字元 | - | 備註 | 催收相關備註說明 |
| CA17 | 參考PCCAPF | 字元 | 1 | 處理步 | 催收處理階段代碼 |
| CA18 | 參考PCCAPF | 字元 | - | 沖帳旗標 | 沖帳狀態代碼 |
| CA20 | 參考PCCAPF | 字元 | - | 作廢旗標 | 作廢狀態代碼 |
| CA25 | 參考PCCAPF | 日期 | - | 最後更新日期 | 資料更新日期 |
| CA26 | 參考PCCAPF | 字元 | - | 最後更新者工作 | 最後更新者工作識別 |
| CA28 | 參考PCCAPF | 字元 | 6 | 催收人員代號 | 負責催收的員工代號 |
| CA29 | 參考PCCAPF | 日期 | - | 建檔日期 | 催收資料建立日期 |
| CA97 | 參考PCCAPF | 時間戳 | - | 建立時間 | 記錄建立時間 |
| CA98 | 參考PCCAPF | 日期 | - | 建立日期 | 記錄建立日期 |
| CA99 | 參考PCCAPF | 字元 | - | 建立者 | 記錄建立者識別碼 |

## 主鍵資訊
檔案採用以下欄位作為主鍵排序：
1. CA17 (處理步)
2. CA05L (供應商代號前三碼)
3. CA05 (供應商代號)
4. CA04 (會計期間)

## 檔案特性與PCWF01的差異
PCWF01S與PCWF01的主要差異：
1. PCWF01S是一個包含明確排序順序的工作檔案，與PCWF01基本結構相似但關注點不同
2. PCWF01S加入了明確的鍵值定義，依照處理步、供應商前三碼、供應商代號和會計期間排序
3. PCWF01S不包含CA04L(會計期間前兩碼)欄位，而PCWF01有此欄位
4. PCWF01S透過排序結構優化了特定處理情境下的資料讀取效率

## 檔案用途與功能
PCWF01S作為催收排序工作檔案，主要用途包括：
1. 提供按照處理步驟和供應商分類排序的催收資料
2. 便於針對特定處理步驟的批次處理操作
3. 支援供應商為主的催收報表和查詢功能
4. 優化特定處理流程的資料存取效率

## 排序設計目的
檔案的排序設計有特定目的：
1. **處理步(CA17)為第一順位**：便於按照催收階段進行批次處理
2. **供應商前三碼(CA05L)和完整代號(CA05)為第二、三順位**：便於按供應商群組和個別供應商處理
3. **會計期間(CA04)為第四順位**：在同一供應商下按會計期間排序

## 應用場景
PCWF01S特別適用於以下場景：
1. 催收階段性批次處理，如針對特定處理步驟的催收資料進行處理
2. 供應商為主的催收報表生成
3. 按供應商群組的催收資料分析
4. 與PCWF01配合使用，提供不同排序視角的資料處理

## 與其他檔案的關係
PCWF01S在催收系統中具有以下關係：
1. 與PCWF01的關係：
   - 兩者均基於PCCAPF的欄位結構
   - PCWF01S提供排序功能，PCWF01提供更多篩選功能
   - 在不同處理階段可能相互配合使用

2. 與PCCAPF和其他催收檔案的關聯：
   - 作為PCCAPF資料的排序工作副本
   - 與PCCBPF、PCCCPF等其他催收檔案在業務邏輯上相關聯

## 備註
- 此檔案的設計重點在於提供特定排序順序的催收資料視角
- 排序結構特別優化了按處理步驟和供應商分類的資料存取
- 沖帳和作廢機制與PCCAPF保持一致
- 此檔案在催收流程中扮演重要的輔助角色，特別是在需要有序處理資料的情境
- 檔案在使用完畢後通常會被清除，屬於暫時性的工作檔案 