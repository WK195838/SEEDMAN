# GLAILF01 檔案規格書

## 基本資訊
- 檔案名稱: GLAILF01
- 檔案類型: 邏輯檔案 (LF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 年度餘額檔邏輯檢視檔

## 紀錄格式
- 紀錄格式名稱: AI0
- 來源實體檔案: GLAIPF
- 特性: UNIQUE (唯一索引)

## 欄位規格
同GLAIPF檔案中的所有欄位

## 主鍵欄位
- AI01 (部門別)
- AI02 (年度)
- AI03 (會計期別)
- AI04A (類別代碼-科目)
- AI05A (類別代碼-費用)
- AI06A (類別代碼-中心)
- AI07A (類別代碼-中心)
- AI08A (類別代碼-項目)
- AI04 (科目代號)
- AI05 (負責人)
- AI06 (供應商代號1)
- AI07 (供應商代號2)
- AI08 (銀行)

## 索引資訊
按照以下順序建立唯一索引：
1. 部門別 (AI01)
2. 年度 (AI02)
3. 會計期別 (AI03)
4. 科目類別代碼 (AI04A)
5. 費用類別代碼 (AI05A)
6. 中心類別代碼 (AI06A)
7. 中心類別代碼 (AI07A)
8. 項目類別代碼 (AI08A)
9. 科目代號 (AI04)
10. 負責人 (AI05)
11. 供應商代號1 (AI06)
12. 供應商代號2 (AI07)
13. 銀行 (AI08)

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/GLAILF01.txt檔案內容產生
- 原始檔案中的中文顯示有編碼問題，欄位說明是根據欄位名稱和系統用途推測
- 此邏輯檔案具有以下特點：
  1. 使用UNIQUE關鍵字建立唯一索引，確保指定的欄位組合不會重複
  2. 從GLAIPF(年度餘額檔)提取數據，提供一個唯一索引的檢視
- 索引結構涵蓋了非常詳細的維度，包括部門、年度、期別、科目、費用、中心和供應商等
- 這種複雜的索引結構設計適合處理財務報表和分析，特別是需要按照多個維度進行彙總的情況
- 此檔案可能用於年度餘額的查詢和報表生成，尤其是需要保證數據唯一性的場合
- 所有以A結尾的欄位表示對應主欄位的類型代碼，這些欄位優先排序表明類型分類優先於實際代碼
- 從索引結構可以看出系統對於數據的組織方式：先按行政架構(部門)、時間(年度、期別)、再按會計科目類型和實際科目進行分類 