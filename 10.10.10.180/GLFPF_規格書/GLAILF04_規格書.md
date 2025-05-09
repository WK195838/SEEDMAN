# GLAILF04 檔案規格書

## 基本資訊
- 檔案名稱: GLAILF04
- 檔案類型: 邏輯檔案 (LF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 年度餘額邏輯檢視檔按部門科目排序

## 紀錄格式
- 紀錄格式名稱: AI0
- 實體檔案: GLAIPF (年度餘額檔)
- 特性: FIFO (先進先出)

## 主要識別欄位
- AI01 (部門別)
- AI02 (年度)
- AI03 (會計期別)
- AI04 (科目代號)

## 索引資訊
按照以下順序建立索引：
1. 部門別 (AI01)
2. 年度 (AI02)
3. 會計期別 (AI03)
4. 科目代號 (AI04)

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/GLAILF04.txt檔案內容產生
- 原始檔案中的中文顯示有編碼問題，欄位說明是根據欄位名稱和系統用途推測
- GLAILF04是年度餘額檔的邏輯檢視，提供按部門科目排序的檢視
- 檔案設計特點：
  1. FIFO特性確保記錄按照插入順序獲取
  2. 索引結構優先考慮部門別，其次是年度、會計期別，最後是科目代號
  3. 與其他GLAILF系列檔案相比，此檔案提供了不同的索引順序
- 此邏輯檔案主要用途：
  1. 快速查詢特定部門的財務資料
  2. 按部門、年度、期別追蹤科目餘額變化
  3. 生成部門級財務報表
  4. 對特定部門進行財務分析和績效評估
- 此邏輯檔案的索引結構適合以下業務場景：
  1. 部門財務狀況分析
  2. 部門預算控制與執行追蹤
  3. 部門間財務比較
  4. 部門科目餘額監控
- 與GLAILF02和GLAILF01相比，GLAILF04提供了以部門為主要維度的查詢視角，滿足不同角度的財務分析需求 