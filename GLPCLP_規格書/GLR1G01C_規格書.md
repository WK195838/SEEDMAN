# 程式功能規格書

## 1. 基本資料
- **程式名稱**：GLR1G01C
- **程式說明**：會計系統會計科目報表執行程式
- **程式語言**：CLP
- **程式位置**：QCLSRC_GLPLIB/GLR1G01C
- **開發人員**：A1150
- **建立日期**：81/11/20
- **系統名稱**：會計系統
- **子系統**：會計處理
- **備註**：會計科目報表執行
- **聯絡電話**：7313250

## 2. 檔案架構與關聯圖
### 使用檔案：
- **資料庫檔案**
  - GLAHLF01：會計科目主檔
- **相關程式**
  - GLR1G01：報表產生程式
  - P64：報表列印控制程式

## 3. 檔案欄位規格說明
### 變數宣告：
| 變數名稱 | 型態 | 長度 | 說明 |
|---------|------|------|------|
| &DAH01 | 字元 | 2位元 | 科目代號 |
| &DAH10F | 字元 | 8位元 | 起始日期 |
| &DAH10T | 字元 | 8位元 | 結束日期 |
| &DFLD | 字元 | 1位元 | 資料過濾條件 |
| &$PENV | 字元 | 1位元 | 環境變數 |
| &$CPY | 字元 | 3位元 | 公司代號 |
| &$PRTCD | 字元 | 2位元 | 列印代號 |
| &P6401I | 字元 | 10位元 | 報表名稱 |
| &P6403I | 數值 | 3位元 | 公司代號 |

## 4. 輸出/入螢幕布局與說明
- 無螢幕輸出
- 使用報表檔案：GLR1G0P
- 報表格式：
  * 頁面大小：100行
  * 字體大小：12 CPI

## 5. 處理流程程序說明
### 1. 程式初始化
- 宣告變數
- 從LDA資料區讀取參數：
  * 科目代號（LDA 501-502）
  * 起始日期（LDA 503-510）
  * 結束日期（LDA 511-518）
  * 資料過濾條件（LDA 519）

### 2. 主要處理邏輯
1. 資料庫檔案處理：
   - 覆蓋資料庫檔案（GLAHLF01）為共享模式
   - 根據過濾條件（&DFLD）建立查詢檔案：
     * 條件1：AH18 = 'V'
     * 條件2：AH19 = 'V' 且 AH20 = ' '
     * 條件3：AH20 = ' '

2. 報表產生與列印：
   - 設定報表格式（GLR1G0P）
   - 呼叫GLR1G01產生報表
   - 關閉查詢檔案
   - 刪除覆蓋設定

3. 報表列印控制：
   - 讀取系統參數：
     * 環境設定（LDA 219）
     * 公司代號（LDA 125-127）
     * 列印代號（LDA 217-218）
   - 呼叫P64程式進行報表列印

## 6. 子程序處理邏輯說明
- **GLR1G01**：報表產生程式
  * 負責實際報表內容的產生
  * 使用查詢檔案（GLAHLF01）的資料

- **P64**：報表列印控制程式
  * 控制報表的實際列印
  * 參數：
    - 報表名稱（&P6401I）
    - 環境設定（&$PENV）
    - 公司代號（&P6403I）
    - 列印代號（&$PRTCD）

## 7. 錯誤處理程序說明與訊息清冊
- 查詢檔案建立失敗時會影響報表產生
- 報表列印失敗時會影響實際輸出

## 8. 備註
- 程式主要用於執行會計科目報表的產生和列印
- 支援三種資料過濾條件
- 使用LDA資料區傳遞參數
- 程式結構包含：
  * 參數讀取
  * 資料查詢
  * 報表產生
  * 報表列印 