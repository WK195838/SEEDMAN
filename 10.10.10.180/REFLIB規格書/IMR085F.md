# 倉庫產品統計檔規格書

## 一、倉庫產品統計檔 (IMR085F)
- **檔案說明**：倉庫產品統計檔
- **用途**：記錄各倉庫點產品庫存統計資料
- **特性**：提供倉庫、產品相關庫存數量統計資訊

## 二、主鍵結構
- 主鍵組合：WF01 + WF03（倉庫點編號 + 產品編號）

## 三、欄位定義

| 欄位名稱 | 欄位說明 | 長度 | 屬性 | 參考欄位 | 檢核規則 |
|---------|---------|------|-----|---------|----------|
| WF01 | 倉庫點編號 | - | 文字 | IA02 | - |
| WF02 | 倉庫點名稱 | 22 | 輸出 | - | - |
| WF03 | 產品編號 | - | 文字 | IA03 | - |
| WF04 | 產品名稱 | - | 文字 | MA02 | - |
| WF05 | 單位換算 | - | 文字 | MA16 | - |
| WF06 | 安全存量 | - | 文字 | IA06 | - |
| WF07 | 數量 | 8 | 數值 | - | - |

## 四、檔案關聯說明

1. **主要關聯**
   - 與倉庫主檔相關（WF01關聯倉庫點編號）
   - 與產品主檔相關（WF03關聯產品編號）
   - 與庫存管理系統相關
   - 與進出口管理系統相關
   - 與採購系統相關

2. **數量計算關係**
   - WF07（數量）：實際庫存數量統計
   - WF06（安全存量）：系統設定的庫存警戒點

3. **欄位分組與使用重點**
   - 倉庫相關：WF01（倉庫點編號）、WF02（倉庫點名稱）
   - 產品相關：WF03（產品編號）、WF04（產品名稱）、WF05（單位換算）
   - 數量相關：WF06（安全存量）、WF07（數量）

## 五、特殊說明

1. **檔案用途**
   - 提供倉庫產品庫存統計資料
   - 用於倉庫存量監控和管理
   - 支援庫存異動追蹤和歷史記錄
   - 提供跨倉庫產品統計分析基礎

2. **資料維護重點**
   - 定期更新實際庫存數量
   - 監控低於安全存量的產品項目
   - 確保倉庫編號和產品編號的準確性
   - 定期核對實際庫存與系統記錄的一致性

3. **報表應用**
   - 庫存警示報表：顯示低於安全存量的產品
   - 庫存分布報表：依倉庫顯示產品分布情況
   - 庫存價值報表：結合產品單價計算庫存總值
   - 庫存週轉率分析：結合銷售數據分析產品週轉情況
   - 倉庫使用效率分析：評估各倉庫儲存效率

4. **資料異動管理**
   - 透過進貨單增加庫存數量
   - 透過出貨單減少庫存數量
   - 透過調撥單實現倉庫間庫存移動
   - 透過盤點作業調整實際庫存與系統記錄差異

這份規格書詳細說明了倉庫產品統計檔的結構和用途。該檔案記錄各倉庫點產品的庫存統計資料，透過主鍵「倉庫點編號 + 產品編號」建立唯一識別，並與倉庫主檔和產品主檔建立關聯。此檔案在庫存管理、採購規劃和倉儲分析中扮演重要角色，提供必要的數據支援來優化庫存控制和倉儲效率。 