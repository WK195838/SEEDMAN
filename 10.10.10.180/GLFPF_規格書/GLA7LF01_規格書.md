# GLA7LF01 檔案規格書

## 基本資訊
- 檔案名稱: GLA7LF01
- 檔案類型: 邏輯檔案 (LF)
- 來源目錄: QDDSSRC_GLFLIB
- 檔案說明: 借款記錄檢視檔 (Join GLAHPF與GLA7PF)

## 紀錄格式
- 紀錄格式名稱: A70
- 參考檔案: GLAHPF, GLA7PF
- 特性: JOIN, DYNSLT, JDFTVAL

## 連結規格
- 主檔案: GLAHPF
- 從檔案: GLA7PF
- 連結欄位: 
  - GLAHPF.AH01 = GLA7PF.A701 (部門別)
  - GLAHPF.AH02 = GLA7PF.A702 (認證編號)
  - GLAHPF.AH03 = GLA7PF.A703 (認證年度)

## 欄位規格

| 欄位名稱 | 來源檔案 | 欄位說明 | 備註 |
|---------|---------|---------|------|
| AH01 | GLAHPF | 部門別 | - |
| AH02 | GLAHPF | 認證編號 | - |
| AH03 | GLAHPF | 認證年度 | - |
| AH04 | GLAHPF | 認證日期 | - |
| AH12 | GLAHPF | 金額 | - |
| AH13 | GLAHPF | 確認旗標 | - |
| A701 | GLA7PF | 部門別 | - |
| A702 | GLA7PF | 認證編號 | - |
| A703 | GLA7PF | 認證年度 | - |
| A704 | GLA7PF | 借款狀態旗標 | 'V'-借款撤銷,'D'-認證取消 |
| A705 | GLA7PF | 借出人 | - |
| A706 | GLA7PF | 金額 | - |
| A707 | GLA7PF | 備註 | - |

## 主鍵欄位
- AH01 (部門別)
- AH02 (認證編號)
- AH03 (認證年度)

## 索引資訊
按照以下順序建立索引：
1. 部門別 (AH01)
2. 認證編號 (AH02)
3. 認證年度 (AH03)

## 備註
- 本檔案規格書根據QDDSSRC_GLFLIB/GLA7LF01.txt檔案內容產生
- 原始檔案中的中文顯示有編碼問題，欄位說明是根據欄位名稱和系統用途推測
- 此邏輯檔案將GLAHPF(認證主檔)和GLA7PF(借款記錄檔)連結在一起，提供完整的借款記錄查詢視圖
- DYNSLT選項允許動態選擇記錄
- JDFTVAL選項允許使用預設值
- 可用於查詢借款記錄與對應的認證資訊 