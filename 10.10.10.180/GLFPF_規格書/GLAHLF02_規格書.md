# GLAHLF02 檔案規格書

## 基本資訊
- 檔案名稱: GLAHLF02
- 檔案類型: 邏輯檔案 (LF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 會計認證主檔邏輯檢視檔 (按期別事由排序)

## 紀錄格式
- 紀錄格式名稱: AH0
- 來源實體檔案: GLAHPF
- 特性: UNIQUE (唯一索引)

## 欄位規格
同GLAHPF檔案中的所有欄位

## 主鍵欄位
- AH01 (部門別)
- AH04 (會計期別)
- AH10 (認證事由)
- AH02 (認證編號)
- AH03 (認證年度)

## 索引資訊
按照以下順序建立唯一索引：
1. 部門別 (AH01)
2. 會計期別 (AH04)
3. 認證事由 (AH10)
4. 認證編號 (AH02)
5. 認證年度 (AH03)

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/GLAHLF02.txt檔案內容產生
- 原始檔案中的中文顯示有編碼問題，欄位說明是根據欄位名稱和系統用途推測
- 此邏輯檔案是GLAHPF的另一個唯一索引視圖，但索引順序與GLAHLF01不同
- 特點是將會計期別(AH04)和認證事由(AH10)加入索引前端，以便於按期別和事由進行查詢和排序
- 索引結構專為以下場景設計：
  - 需要按會計期別查詢特定期間的認證
  - 需要按認證事由分類查詢認證
  - 需要生成按期別和事由排序的報表
- 與GLAHLF01相比，此檔案更適合會計期間報表和事由分析的需求
- 保留認證編號(AH02)和認證年度(AH03)在索引末端，確保完整的唯一性
- 此設計使系統可以高效地查詢特定期別下特定事由的認證資料 