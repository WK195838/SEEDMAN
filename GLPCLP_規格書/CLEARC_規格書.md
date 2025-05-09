# 程式功能規格書

## 1. 基本資料
- **程式名稱**：CLEARC
- **程式說明**：清除會計系統相關檔案資料
- **程式語言**：CLP
- **程式位置**：QCLSRC_GLPLIB/CLEARC

## 2. 檔案架構與關聯圖
### 使用檔案：
- **顯示檔案**
  - CLEARD
- **會計主檔**
  - GLABPF, GLAGPF, GLAHPF, GLAIPF, GLALPF, GLAMPF, GLA5PF
- **會計明細檔**
  - GLACPF, GLANPF, GLAOPF, GLAPPF, GLAQPF, GLARPF, GLASPF, GLAWPF, GLAXPF, GLAYPF, GLAZPF
- **會計統計檔**
  - GLAAPF, GLADPF, GLAEPF, GLAFPF, GLAJPF, GLA3PF, GLAKPF
- **系統參數檔**
  - PT#APF, PT#BPF, PT#YPF, PT#ZPF
- **會計報表檔**
  - GLATPF, GLAUPF, GLAVPF, GLA1PF, GLA2PF

## 3. 檔案欄位規格說明
### 變數宣告：
| 變數名稱 | 型態 | 長度 | 說明 |
|---------|------|------|------|
| &WDATE | 日期 | 8位元 | 日期變數 |
| &$USER | 字元 | 10位元 | 使用者代號 |
| &P3101I | 數值 | 8位元 | 數值變數 |
| &P3102I | 字元 | 1位元 | 預設值'2' |
| &P3103I | 字元 | 1位元 | 預設值'1' |
| &P3104I | 字元 | 1位元 | 字元變數 |
| &P3105I | 字元 | 1位元 | 字元變數 |
| &P3101O | 數值 | 8位元 | 數值變數 |

## 4. 輸出/入螢幕布局與說明
- 使用CLEARD顯示檔案
- 記錄格式：DSPD1

## 5. 處理流程程序說明
### 1. 程式初始化
- 宣告變數
- 讀取使用者資料區
- 讀取系統日期
- 讀取參數資料區

### 2. 主要處理邏輯
- 顯示清除選項畫面
- 根據選擇的選項(&DOPID)執行不同的清除作業：
  * 選項01-04：清除會計主檔
  * 選項02-04：清除會計明細檔
  * 選項03-04：清除會計統計檔
  * 選項04：清除系統參數檔並複製預設值
  * 選項05：清除會計報表檔

## 6. 子程序處理邏輯說明
- 呼叫P31程式進行日期轉換處理

## 7. 錯誤處理程序說明與訊息清冊
- 使用MONMSG指令處理CPF9999錯誤訊息

## 8. 備註
- 程式使用資料區(*LDA)儲存使用者資訊和日期
- 清除作業分為五個層級，可選擇性執行
- 系統參數檔清除後會自動複製預設值 