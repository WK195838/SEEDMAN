# 禮券銷售主檔規格書（W2BEPF）

## 一、基本資訊
- **檔案名稱**：W2BEPF
- **檔案說明**：禮券銷售主檔
- **檔案類型**：實體檔案（Physical File）
- **關鍵欄位**：BE01 + BE02 + BE03
- **備註**：UNIQUE索引

## 二、記錄格式（BE0）

### 1. 欄位定義
| 欄位名稱 | 長度 | 屬性 | 說明 | 檢核規則 |
|----------|------|------|------|----------|
| BE01     | 8    | 數值(0) | 銷售日期 | 必填，主鍵的一部分，無小數位 |
| BE02     | 5    | 字元 | 作業點 | 必填，主鍵的一部分 |
| BE03     | 12   | 字元 | 銷售名稱 | 必填，主鍵的一部分 |
| BE04     | 11   | 數值(2) | 總金額 | 必填，2位小數 |
| BE05     | 10   | 字元 | 確認人員 | 選填 |
| BE06     | 5    | 字元 | 單位碼 | 必填 |
| BEXX     | 8    | 數值(0) | 更新日期 | 系統自動產生，無小數位 |
| BEYY     | 6    | 數值(0) | 更新時間 | 系統自動產生，無小數位 |
| BEZZ     | 10   | 字元 | 更新人員 | 系統自動產生 |

### 2. 索引定義
- **主索引**：BE01（銷售日期）+ BE02（作業點）+ BE03（銷售名稱）（唯一索引）

## 三、關聯與檢核規則

### 1. 主鍵檢核
- BE01（銷售日期）+ BE02（作業點）+ BE03（銷售名稱）組成唯一主鍵
- 不允許重複的主鍵值

### 2. 資料完整性檢核
- BE01（銷售日期）：必須是有效的日期格式，無小數位
- BE02（作業點）：必須是系統中已定義的有效作業點
- BE03（銷售名稱）：必須是有效的銷售名稱
- BE04（總金額）：必須是有效的金額，含2位小數且大於等於0
- BE05（確認人員）：若填寫，必須是系統中有效的操作員ID
- BE06（單位碼）：必須是系統中定義的有效單位代碼

### 3. 業務規則
- 每個銷售日期、作業點和銷售名稱的組合只能有一筆記錄
- 銷售日期（BE01）通常使用系統日期自動填入
- 總金額（BE04）應等於該銷售關聯的所有明細項目金額總和
- 確認人員（BE05）記錄銷售資料的審核或處理人員
- 單位碼（BE06）用於標識銷售的計量單位或部門代號
- 系統會自動記錄更新相關資訊（BEXX、BEYY、BEZZ）

## 四、使用說明

### 1. 檔案用途
- 儲存禮券銷售的基本資料
- 記錄不同作業點的銷售情況
- 提供銷售金額的總計資訊
- 作為銷售明細的參照主檔

### 2. 操作注意事項
- 新增記錄時，必須確保BE01、BE02、BE03組合的唯一性
- 系統會自動維護BEXX（更新日期）、BEYY（更新時間）和BEZZ（更新人員）欄位
- 修改記錄時，應注意保留原有的主鍵值，避免造成資料關聯性問題
- 銷售資料一經確認，應避免隨意修改或刪除
- 此檔案通常與禮券訂單主檔（W2BCPF）和禮券卡片主檔（W2BAPF）有關聯

本規格書依據W2BEPF.txt製作，完整記錄W2BEPF檔案結構、欄位屬性與檢核規則。如需調整或有其他需求，歡迎隨時告知！ 