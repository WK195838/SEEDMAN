# GLAWPF 檔案規格書

## 基本資訊
- 檔案名稱: GLAWPF
- 檔案類型: 實體檔案 (PF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 二三式帳票抬頭主檔

## 紀錄格式
- 紀錄格式名稱: AW0
- 參考檔案: GLRF
- 特性: UNIQUE (唯一索引)

## 欄位規格
| 欄位名稱 | 欄位說明 | 資料類型 | 長度 | 備註 |
|---------|---------|---------|------|------|
| AW01 | 部門碼 | R | - | 部門編碼識別 |
| AW02 | 帳套 | R | - | 帳務套別識別 |
| AW97 | 更新時間 | R | - | 記錄更新時間 |
| AW98 | 更新者 | R | - | 記錄更新人員 |
| AW99 | 更新機 | R | - | 記錄更新機器 |

## 主鍵欄位
- AW01 (部門碼)

## 索引資訊
按照以下順序建立索引：
1. 部門碼 (AW01)

## 程式設計說明
```
A*****************************************************************
A*        23式帳票抬頭主檔(GLAWPF)                               *
A*****************************************************************
A                                      REF(GLRF)
A                                      UNIQUE
A          R AW0
A            AW01      R               COLHDG('部門碼')
A*
A            AW02      R               COLHDG('帳套')
A            AW97      R               COLHDG('更新時間')
A            AW98      R               COLHDG('更新者')
A            AW99      R               COLHDG('更新機')
A          K AW01
```

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/GLAWPF.txt檔案內容產生
- 原始檔案中的中文顯示有編碼問題，欄位說明是根據欄位名稱和系統用途推測
- 檔案設計特點：
  1. UNIQUE特性確保每個部門碼只有一筆記錄，避免重複
  2. 使用REF(GLRF)參考主系統欄位定義，確保資料一致性
  3. 索引建立在部門碼(AW01)上，優化依部門查詢的效能
  4. 具有標準的更新追蹤欄位(AW97-AW99)，記錄資料變更歷史
- 此主檔主要用途：
  1. 儲存與管理二三式帳票的抬頭資訊，提供標準化的報表抬頭資料
  2. 支援不同部門的帳票格式需求
  3. 集中管理帳票抬頭設定，確保企業報表格式一致性
  4. 與帳套(AW02)欄位相關聯，確保報表與正確的帳務系統連結
- 此檔案是常駐性主檔，與暫存性工作檔案不同，用於長期儲存帳票抬頭的基本資料
- 檔案結構簡潔，專注於部門與帳套關聯，這表明其在會計報表系統中的基礎角色 