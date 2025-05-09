# 前置倉儲主檔規格書（W1AFPF）

## 一、基本資訊
- **檔案名稱**：W1AFPF
- **檔案說明**：前置倉儲主檔
- **檔案類型**：實體檔案（Physical File）
- **關鍵欄位**：AF01 + AF02
- **備註**：UNIQUE索引

## 二、記錄格式（AF0）

### 1. 欄位定義
| 欄位名稱 | 長度 | 屬性 | 說明 | 檢核規則 |
|----------|------|------|------|----------|
| AF01     | 8    | 數值(0) | 倉儲編號 | 必填，主鍵的一部分，無小數位 |
| AF02     | 12   | 字元 | 倉儲名稱 | 必填，主鍵的一部分 |
| AF03     | 5    | 字元 | 出貨作業點 | 必填 |
| AF04     | 5    | 字元 | 進貨作業點 | 必填 |
| AF05     | 1    | 字元 | 狀態 | 必填 |
| AF06     | 64   | 物件 | 程序 | 系統使用 |
| AFXX     | 8    | 數值(0) | 更新日期 | 系統自動產生，無小數位 |
| AFYY     | 6    | 數值(0) | 更新時間 | 系統自動產生，無小數位 |
| AFZZ     | 10   | 字元 | 更新人員 | 系統自動產生 |

### 2. 索引定義
- **主索引**：AF01 + AF02（唯一索引）

## 三、關聯與檢核規則

### 1. 主鍵檢核
- AF01（倉儲編號）+ AF02（倉儲名稱）組成唯一主鍵
- 不允許重複的主鍵值

### 2. 資料完整性檢核
- AF01（倉儲編號）：必須是有效的數值，無小數位
- AF02（倉儲名稱）：必須是有效的倉儲名稱
- AF03（出貨作業點）：必須是系統中定義的有效作業點
- AF04（進貨作業點）：必須是系統中定義的有效作業點
- AF05（狀態）：必須是有效的狀態碼（如：A=啟用，I=停用等）
- AFXX（更新日期）：系統自動填入當前日期
- AFYY（更新時間）：系統自動填入當前時間
- AFZZ（更新人員）：系統自動填入操作員ID

### 3. 業務規則
- 每個倉儲編號和倉儲名稱的組合只能有一筆記錄
- 狀態碼（AF05）控制倉儲是否可用於系統操作
- 出貨作業點（AF03）與進貨作業點（AF04）必須是系統中已定義的作業點
- 系統會自動記錄更新相關資訊（AFXX、AFYY、AFZZ）

## 四、使用說明

### 1. 檔案用途
- 儲存前置倉儲基本資料
- 管理前置倉儲的進出貨作業點設定
- 控制倉儲的使用狀態

### 2. 操作注意事項
- 新增記錄時，必須確保AF01、AF02組合的唯一性
- 系統會自動維護AFXX（更新日期）、AFYY（更新時間）和AFZZ（更新人員）欄位
- 修改記錄時，應注意保留原有的主鍵值，避免造成資料關聯性問題
- AF06（程序）欄位為系統內部使用，一般操作時不需手動維護

本規格書依據W1AFPF.txt製作，完整記錄W1AFPF檔案結構、欄位屬性與檢核規則。如需調整或有其他需求，歡迎隨時告知！ 