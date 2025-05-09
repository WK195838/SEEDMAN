# GLAWF01 檔案規格書

## 基本資訊
- 檔案名稱: GLAWF01
- 檔案類型: 實體檔案 (PF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 薪資列印暫存檔

## 紀錄格式
- 紀錄格式名稱: GLWF01R
- 參考檔案: GLRF
- 特性: FIFO (先進先出)

## 欄位規格
| 欄位名稱 | 欄位說明 | 資料類型 | 長度 | 備註 |
|---------|---------|---------|------|------|
| WF0101 | 作業日期 | A | 6 | 文字格式的日期 |
| WF0102 | 部門人員 | A | 10 | 員工識別資訊 |
| WF0103 | 上月應付金額 | R | - | 參考AH12欄位 |
| WF0104 | 上月剩餘金額 | R | - | 參考AH13欄位 |
| WF0105 | 本月應付金額 | R | - | 參考AH12欄位 |
| WF0106 | 本月剩餘金額 | R | - | 參考AH13欄位 |

## 主鍵欄位
- WF0101 (作業日期)
- WF0102 (部門人員)

## 索引資訊
按照以下順序建立索引：
1. 作業日期 (WF0101)
2. 部門人員 (WF0102)

## 程式設計說明
```
A*****************************************************************
A*          薪資列印暫存檔(GLWF01)   KEY=WF0101-WF0108
A*****************************************************************
A                                      FIFO
A                                      REF(GLRF)
A          R GLWF01R
A            WF0101         6A         COLHDG('作業日期')
A            WF0102        10A         COLHDG('部門人員')
A            WF0103    R               COLHDG('上月應付金額')
A                                      REFFLD(AH12)
A            WF0104    R               COLHDG('上月剩餘金額')
A                                      REFFLD(AH13)
A            WF0105    R               COLHDG('本月應付金額')
A                                      REFFLD(AH12)
A            WF0106    R               COLHDG('本月剩餘金額')
A                                      REFFLD(AH13)
A*
A          K WF0101
A          K WF0102
```

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/GLAWF01.txt檔案內容產生
- 原始檔案中的中文顯示有編碼問題，欄位說明是根據欄位名稱和系統用途推測
- 原始檔案註解表示主鍵為WF0101-WF0108，但實際索引僅設定WF0101和WF0102兩個欄位
- GLAWF01是工作檔案，主要用於薪資處理過程中的暫存資料
- 檔案設計特點：
  1. FIFO特性確保記錄按照插入順序處理，適合批次作業的順序處理
  2. 使用REF(GLRF)參考主系統欄位定義，確保資料一致性，尤其是金額欄位
  3. 金額欄位(WF0103-WF0106)均參考自AH12或AH13，表示與會計認證主檔(GLAHPF)金額欄位相容
  4. 索引設計簡單，僅包含作業日期和部門人員，方便按日期和人員進行查詢
- 此工作檔案主要用途：
  1. 臨時儲存薪資處理過程中的上月和本月金額資訊
  2. 支援薪資列印和報表生成
  3. 比較上月和本月的應付金額和剩餘金額變化
  4. 作為薪資批次處理的工作區域
- 欄位WF0101(作業日期)和WF0102(部門人員)共同唯一識別一筆薪資記錄
- 此檔案是臨時性工作檔案，資料可能在薪資處理完成後被清空 