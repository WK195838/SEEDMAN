# 程式功能規格書

## 1. 基本資料
- **程式名稱**：GLR2C01C
- **程式說明**：會計系統明細分類帳報表執行程式
- **程式語言**：CLP
- **程式位置**：QCLSRC_GLPLIB/GLR2C01C
- **開發人員**：A1087 JOYCE
- **建立日期**：1993/01/09
- **系統名稱**：會計系統
- **子系統**：會計處理
- **備註**：明細分類帳報表執行
- **聯絡電話**：7313250

## 2. 檔案架構與關聯圖
### 使用檔案：
- **資料庫檔案**
  - GLWF03：會計主檔
  - GLAHLF07：會計明細檔
- **相關程式**
  - GLR2C01：報表產生程式
  - P64：報表列印控制程式

## 3. 檔案欄位規格說明
### 變數宣告：
| 變數名稱 | 型態 | 長度 | 說明 |
|---------|------|------|------|
| &DAH01S | 字元 | 2位元 | 系統代號起始值 |
| &DAH01E | 字元 | 2位元 | 系統代號結束值 |
| &DAH05S | 字元 | 20位元 | 科目代號起始值 |
| &DAH05E | 字元 | 20位元 | 科目代號結束值 |
| &WAH10S | 字元 | 8位元 | 日期起始值 |
| &WAH10E | 字元 | 8位元 | 日期結束值 |
| &DAR05 | 字元 | 1位元 | 報表格式選擇 |
| &$PENV | 字元 | 1位元 | 環境變數 |
| &$CPY | 字元 | 3位元 | 公司代號 |
| &$PRTCD | 字元 | 2位元 | 列印代號 |
| &P6401I | 字元 | 10位元 | 報表名稱 |
| &P6403I | 數值 | 3位元 | 公司代號 |

## 4. 輸出/入螢幕布局與說明
- 無螢幕輸出
- 報表格式：
  * 支援兩種報表格式（&DAR05）：
    - '1'：GLR2C0P1格式
    - '2'：GLR2C0P2格式

## 5. 處理流程程序說明
### 1. 程式初始化
- 宣告變數
- 從LDA資料區讀取參數：
  * 系統代號範圍（LDA 556-558）
  * 科目代號範圍（LDA 561-581）
  * 日期範圍（LDA 533-541）
  * 報表格式選擇（LDA 549）

### 2. 主要處理邏輯
1. 資料庫檔案處理：
   - 複製GLWF03到QTEMP
   - 清除檔案內容
   - 覆蓋資料庫檔案為共享模式

2. 查詢條件設定：
   - 建立查詢檔案，條件包含：
     * 系統代號範圍（AH01）
     * 科目代號範圍（AH05）
     * 日期範圍（AH10）

3. 報表格式處理：
   - 根據&DAR05選擇報表格式：
     * '2'：使用GLR2C0P2格式
     * 其他：使用GLR2C0P1格式

4. 報表產生與列印：
   - 呼叫GLR2C01產生報表
   - 關閉查詢檔案
   - 刪除覆蓋設定

5. 報表列印控制：
   - 讀取系統參數：
     * 環境變數（LDA 219）
     * 公司代號（LDA 125-127）
     * 列印代號（LDA 217-218）
   - 根據報表格式選擇呼叫P64程式

## 6. 子程序處理邏輯說明
- **GLR2C01**：報表產生程式
  * 負責報表內容的產生
  * 使用GLAHLF07資料來源

- **P64**：報表列印控制程式
  * 控制報表的實際列印
  * 參數：
    - 報表名稱（&P6401I）
    - 環境設定（&$PENV）
    - 公司代號（&P6403I）
    - 列印代號（&$PRTCD）

## 7. 錯誤處理程序說明與訊息清冊
- 資料庫檔案處理錯誤：
  * CPF2817：檔案已存在
  * 查詢檔案建立失敗時會影響報表產生
- 報表列印錯誤：
  * 報表格式設定錯誤時會影響輸出
  * 列印控制失敗時會影響實際輸出

## 8. 備註
- 程式主要用於執行明細分類帳報表的產生和列印
- 支援兩種報表格式：
  * GLR2C0P1：標準格式
  * GLR2C0P2：特殊格式
- 使用LDA資料區傳遞參數
- 程式結構包含：
  * 參數讀取
  * 資料查詢
  * 報表產生
  * 報表列印 