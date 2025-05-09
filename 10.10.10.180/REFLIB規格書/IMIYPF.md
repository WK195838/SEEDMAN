# 庫存年度統計檔規格書

## 一、庫存年度統計檔 (IMIYPF)
- **檔案說明**：庫存年度統計檔
- **用途**：記錄各客戶、倉庫、產品之年度庫存統計資料
- **特性**：提供年度庫存相關數量統計資訊

## 二、主鍵結構
- 主鍵組合：IY15 + IY01 + IY02 + IY03（年度年月 + 客戶別 + 倉庫點編號 + 產品編號）

## 三、欄位定義

| 欄位名稱 | 欄位說明 | 長度 | 屬性 | 參考欄位 | 檢核規則 |
|---------|---------|------|-----|---------|----------|
| IY15 | 統計年月 | 6 | 數值 | - | - |
| IY01 | 客戶別 | - | 文字 | - | - |
| IY02 | 倉庫點編號 | - | 文字 | - | - |
| IY03 | 產品編號 | - | 文字 | - | - |
| IY04 | 產品名稱 | - | 文字 | - | - |
| IY05 | 產品類別 | - | 文字 | - | - |
| IY06 | 安全存量 | - | 文字 | - | - |
| IY07 | 開始量 | - | 文字 | - | - |
| IY08 | 結束量 | - | 文字 | - | - |
| IY09 | 承諾量 | - | 文字 | - | - |
| IY10 | 可用量 | - | 文字 | - | - |
| IYXX | 異動日期 | 8 | 數值 | - | - |
| IYYY | 異動時間 | - | 文字 | - | - |
| IYZZ | 異動者 | - | 文字 | - | - |

## 四、檔案關聯說明

1. **主要關聯**
   - 與客戶主檔相關（IY01關聯客戶別）
   - 與倉庫主檔相關（IY02關聯倉庫點編號）
   - 與產品主檔相關（IY03關聯產品編號）
   - 與庫存管理系統相關
   - 與進出口管理系統相關
   - 與採購系統相關

2. **數量計算關係**
   - IY06（安全存量）：系統設定的庫存警戒點
   - IY07（開始量）：期初庫存數量
   - IY08（結束量）：期末庫存數量
   - IY09（承諾量）：已承諾但尚未出庫的數量
   - IY10（可用量）：實際可調度使用的庫存數量（結束量減去承諾量）

3. **欄位分組與使用重點**
   - 識別相關：IY15（統計年月）、IY01（客戶別）、IY02（倉庫點編號）、IY03（產品編號）
   - 產品相關：IY04（產品名稱）、IY05（產品類別）
   - 數量相關：IY06（安全存量）、IY07（開始量）、IY08（結束量）、IY09（承諾量）、IY10（可用量）
   - 異動相關：IYXX（異動日期）、IYYY（異動時間）、IYZZ（異動者）

## 五、特殊說明

1. **檔案用途**
   - 提供年度庫存統計資料
   - 用於庫存年度趨勢分析
   - 支援年度庫存報表產生
   - 提供客戶、倉庫、產品三維度的庫存分析基礎
   - 用於庫存年度預測與計劃制定

2. **資料維護重點**
   - 每年度結算時更新統計資料
   - 確保客戶別、倉庫編號和產品編號的準確性
   - 監控低於安全存量的產品項目
   - 定期核對實際庫存與系統記錄的一致性
   - 正確記錄庫存異動資訊

3. **報表應用**
   - 年度庫存趨勢報表：顯示產品全年庫存變化趨勢
   - 年度庫存分布報表：依倉庫顯示產品年度分布情況
   - 年度庫存價值報表：結合產品單價計算年度庫存總值
   - 年度庫存週轉率分析：評估產品年度週轉效率
   - 客戶年度庫存分析：依客戶評估庫存使用情況

4. **資料異動管理**
   - 年度結算時自動產生新年度統計記錄
   - 記錄每次異動的日期、時間和操作人員
   - 確保資料的正確性和完整性
   - 與月度、季度庫存統計資料的整合與比對

5. **UNIQUE標記說明**
   - 檔案設有UNIQUE屬性，確保主鍵組合的唯一性
   - 避免重複記錄造成統計錯誤
   - 保證資料完整性和一致性

這份規格書詳細說明了庫存年度統計檔的結構和用途。該檔案記錄各客戶、倉庫、產品的年度庫存統計資料，透過主鍵「年度年月 + 客戶別 + 倉庫點編號 + 產品編號」建立唯一識別，並與客戶主檔、倉庫主檔和產品主檔建立關聯。此檔案在庫存年度管理、趨勢分析和報表生成中扮演重要角色，提供必要的數據支援來評估庫存年度變化、制定庫存策略和優化資源分配。 