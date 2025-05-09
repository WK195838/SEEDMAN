# GLRF0001.txt 檔案規格書

## 檔案概述
GLRF0001.txt 是一個定義總帳模組(GL模組)中各種資料結構的參照檔案，包含了多個與會計和財務處理相關的資料結構定義。這個檔案提供了系統中不同檔案格式和欄位的參照關係，有助於維護系統的一致性和資料的完整性。

## 檔案結構
檔案以DDS (Data Description Specifications) 格式定義，包含了33個主要的資料結構，從01到33編號，每個結構代表了一個與總帳處理相關的特定檔案類型。檔案格式採用「全域參照民國年」的時間表示方式，如檔案第35行所示：`A*  資料結構檔格式：　全域　　參照　　民國年`。

### 主要結構摘要
以下是檔案中定義的主要資料結構：

1. GLAAPF - 輸入程式基準表
2. GLABPF - 會計期間檔
3. GLACPF - 會計年度主檔
4. GLADPF - 科目基準表
5. GLAEPF - 借貸科目檔案
6. GLAFPF - 會計憑證檔
7. GLAGPF - 大分類組檔
8. GLAHPF - 會計傳票檔
9. GLAIPF - 年度彙總檔
10. GLAJPF - 序號產生檔
11. GLAKPF - 總帳參數檔
12. GLALPF - 借貸彙總主檔
13. GLAMPF - 借貸彙總明細檔
14. GLANPF - 固定傳票主檔
15. GLAOPF - 固定傳票明細檔
16. GLAPPF - 預算人員主檔
17. GLAQPF - 固定傳票明細檔
18. GLARPF - 報表格式設定主檔
19. GLASPF - 報表格式設定明細檔
20. GLATPF - 預算檔主檔
21. GLAUPF - 預算檔明細檔
22. GLAVPF - 歸類科目類別明細檔
23. GLAWPF - 客戶群組主檔
24. GLAXPF - 客戶群組明細檔
25. GLAYPF - 歸類科目群組主檔
26. GLAZPF - 歸類科目群組明細檔
27. GLA1PF - 明細預算檔主檔
28. GLA2PF - 明細預算檔明細檔
29. GLA3PF - 暫結科目檔案
30. GLA4PF - 套印檔案
31. GLA5PF - 傳票來源閉帳檔
32. GLA6PF - 預算比例科目檔
33. GLA7PF - 核銷檔案

## 欄位結構說明

### 通用欄位模式
檔案中定義了一個共同的記錄格式 GLRFR（第38行：`A R GLRFR`），各個檔案結構都參照此格式，並遵循以下命名規則：

- 每個結構欄位以字母代號加數字編號組成，如 AA01, AB01, AC01 等
- 每個結構都包含以下通用欄位：
  - xx01: 公司代碼欄位，通常為2字元，用於識別相關資料所屬的公司
  - xx97: 建立時間欄位，通常為6位數值型態 (6S 0)
  - xx98: 建立日期欄位，通常為8位數值型態 (8S 0)
  - xx99: 建立者欄位，通常為10字元

### 欄位定義特點
檔案中大量使用 REFFLD 關鍵字來參照已定義的欄位，這有助於保持欄位定義的一致性。例如：

```
A            AB01      R               COLHDG('輸入程式基準表')
A                                      REFFLD(AA01)
```

這裡 AB01 欄位的格式是參照 AA01 欄位的定義。

### COLHDG 說明
每個欄位都使用 COLHDG('說明文字') 來定義欄位標題，這些標題在報表或顯示中會顯示為欄位名稱。然而，在當前檔案中，許多欄位的 COLHDG 值似乎未完全對應其實際用途，而是重複使用一些標準文字如「借貸科目檔案」、「會計憑證檔案」等，可能需要在實際應用中根據欄位實際用途進行調整。

## 主要功能分類

### 會計基礎資料
- **會計期間檔(GLABPF)**：定義會計期間相關資訊，包含 AB01(公司代碼)、AB02(會計期間)、AB03(會計年度)等欄位
- **會計年度主檔(GLACPF)**：定義會計年度相關設定，包含 AC01(公司代碼)、AC02(會計年度)、AC03-AC15(各月份結帳狀態)欄位
- **科目基準表(GLADPF)**：定義會計科目的基本資訊，包含 AD01(公司代碼)、AD02(科目代碼)、AD03(科目名稱)、AD04(科目說明)、AD05(科目類型)等欄位

### 傳票與憑證
- **會計憑證檔(GLAFPF)**：記錄會計憑證相關資訊，包含多項欄位如AF02(憑證編號)、AF03(憑證名稱)等
- **會計傳票檔(GLAHPF)**：記錄傳票相關資訊，包含AH02(會計年度)、AH03(傳票編號)、AH12/AH13(借/貸方金額)等欄位
- **固定傳票相關檔案**：固定傳票主檔(GLANPF)、固定傳票明細檔(GLAOPF/GLAQPF)等，用於管理固定性重複的傳票資料

### 彙總與報表
- **年度彙總檔(GLAIPF)**：記錄年度財務數據的彙總資訊，包含各期間的借貸金額(AI10-AI23系列欄位)
- **借貸彙總主檔(GLALPF)與明細檔(GLAMPF)**：記錄借貸資料的彙總資訊
- **報表格式設定主檔(GLARPF)與明細檔(GLASPF)**：定義報表格式相關設定

### 預算管理
- **預算檔主檔(GLATPF)與明細檔(GLAUPF)**：管理預算相關資訊
- **明細預算檔主檔(GLA1PF)與明細檔(GLA2PF)**：管理詳細的預算資訊
- **預算比例科目檔(GLA6PF)**：管理預算分配比例，包含12個月的比例欄位(A6041-A604D)
- **預算人員主檔(GLAPPF)**：管理預算相關的人員資訊

### 輔助功能
- **序號產生檔(GLAJPF)**：管理系統中各種序號的產生
- **總帳參數檔(GLAKPF)**：存儲系統各種運行參數設定
- **暫結科目檔案(GLA3PF)**：管理暫時結算的科目
- **套印檔案(GLA4PF)**：管理文件列印格式，包含多種不同尺寸的列印格式欄位
- **核銷檔案(GLA7PF)**：管理憑證核銷相關資訊

## 資料類型與格式

檔案中使用的主要資料類型包括：
- 字元型 (如 1A, 8A 等)
- 數值型 (如 6S 0, 13P 2 等)
- 輸出型 (如 20O, 50O 等，用於顯示用途)
- 日期/時間型 (使用數值表示，如 8S 0 表示日期)

特殊的格式標識：
- P 表示帶精度的數值型，如 13P 2 表示 13 位數字，含 2 位小數
- S 表示帶符號的數值型
- O 表示輸出型欄位
- J 表示特殊日文字元集（於部分欄位使用）

## 關聯性分析

1. **主檔與明細檔關係**：
   - 預算檔主檔(GLATPF)與預算檔明細檔(GLAUPF)
   - 固定傳票主檔(GLANPF)與固定傳票明細檔(GLAOPF)
   - 借貸彙總主檔(GLALPF)與借貸彙總明細檔(GLAMPF)
   - 報表格式設定主檔(GLARPF)與明細檔(GLASPF)

2. **參照關係**：
   - 科目基準表(GLADPF)被多個檔案參照，如會計傳票檔(GLAHPF)
   - 會計年度主檔(GLACPF)與會計期間檔(GLABPF)有時間維度的關聯

## 檔案用途
此檔案主要用途：
1. 作為系統內部各模組間數據交換的參照標準
2. 定義會計總帳系統的基本數據結構
3. 提供系統中各種會計處理相關資料的格式和欄位屬性
4. 設定會計數據處理的基本規則和參數

## 與其他檔案的關聯
此檔案定義的結構與總帳模組中的其他實體檔案緊密關聯，提供了資料結構的藍圖。如檔案中引用了 REF(*LIBL/GLRF) 指令，表示這些定義參照了GLRF庫。相關程式透過參照此檔案來維護數據的一致性。

## 特殊處理考量
1. 在許多欄位定義中使用了REFFLD關鍵字，表示欄位定義參照自另一個已定義的欄位
2. 欄位的COLHDG屬性定義了欄位在報表或顯示中的標題
3. 檔案中有些註解表明了欄位的可能值，如：
   ```
   A            AF09           1          COLHDG('借貸科目檔案')
   A*                                     '1'  -> 借貸科目檔案
   A*                                     '2'  -> 會計憑證檔案
   A*                                     '3'  -> 會計憑證檔案
   A*                                     '4'  -> 會計憑證檔案
   ```

## 結論
GLRF0001.txt是總帳系統的核心結構定義檔案，為系統中所有與會計處理相關的資料提供了標準化的結構定義。該檔案包含了豐富的欄位定義和參照關係，使用了大量的REFFLD技術來保持一致性，並提供了詳細的註解說明。正確理解和維護此檔案對於系統的穩定運行和數據的一致性非常重要。 