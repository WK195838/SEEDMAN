# GLI330D 螢幕顯示檔規格書

## 一、基本資訊
- 檔案名稱：GLI330D
- 檔案類型：螢幕顯示檔
- 來源目錄：10.10.10.180/QDDSSRC_GLPLIB
- 程式說明：部門預算設定查詢
- 系統：會計總帳系統
- 子系統：會計總帳系統
- 作者：A1087 JOYCE
- 建立日期：1992.11.02
- 更新日期：

## 二、螢幕規格
- 顯示大小：24x80
- 參考檔案：*LIBL/GLRF
- 螢幕代號：GLI330.1
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：
  - 50：明細資料顯示控制
  - 51：明細資料控制顯示
  - 52：明細資料清除控制
  - 53：明細資料結束控制
  - 96：訊息ID控制
  - 99：錯誤訊息控制
  - CA03：畫面控制
  - CF12：畫面控制

## 三、螢幕佈局

### 主畫面 (GLI330.1)
```
<GLI330.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                    部門預算設定查詢                   時間: [時間]

S (=一筆) : /-查詢
S
 No  公司  部門  預算名稱    預算金額    預算日期    預算類別
---------------------------------------------------------
[明細資料顯示區域]
---------------------------------------------------------
[錯誤訊息顯示區域]
注意    PF3=返回前頁    PF12=返回前頁    PA1=下一頁
注意    PA2=上一頁
                                                           【茂世資訊】
```

## 四、記錄格式

### 明細畫面 (SFLSR)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| DOPT | 8,2 | 1 | A | B | 選項 |
| RRN | 8,4 | 3 | Y | O | 記錄編號 |
| AP01 | 8,9 | - | R | O | 公司代號 |
| AP02 | 8,13 | - | R | O | 部門代號 |
| DAF03 | 8,22 | 22 | A | O | 預算名稱 |
| AP03 | 8,45 | - | R | O | 預算金額 |
| D#A02 | 8,50 | 12 | - | O | 預算日期 |
| DAP05 | 8,63 | 6 | - | O | 預算類別 |
| DAP06 | 8,70 | - | R | O | 預算狀態 |
| AP04 | - | - | R | H | 隱藏欄位 |
| AP05 | - | - | R | H | 隱藏欄位 |

### 主畫面 (DSPC1)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| CONAME | 1,25 | 32 | A | O | 公司名稱 |
| DDATE | 1,72 | 6 | Y | O | 系統日期 |
| $USERN | 2,2 | 10 | A | O | 使用者ID |
| DAP01 | 7,9 | - | R | B | 公司代號 |
| DAP02 | 7,13 | - | R | B | 部門代號 |

## 五、功能鍵說明
- PF3：返回前頁
- PF12：返回前頁
- PA1：下一頁
- PA2：上一頁

## 六、輸入欄位驗證
1. 必填欄位：
   - 公司代號 (DAP01)
   - 部門代號 (DAP02)

2. 資料格式：
   - 公司代號：必須為有效公司代號
   - 部門代號：必須為有效部門代號
   - 選項：必須為 '/' 或空白
   - 預算日期：必須為有效日期格式 (YY/MM/DD)
   - 預算金額：必須為有效金額格式

## 七、錯誤處理
- 錯誤訊息顯示位置：第22行
- 錯誤訊息格式：
  - MSGID(&ERRID &ERRF)：動態錯誤訊息
- 錯誤類型：
  - 必填欄位未輸入
  - 資料格式錯誤
  - 公司代號不存在
  - 部門代號不存在
  - 預算日期格式錯誤
  - 預算金額格式錯誤
  - 查詢條件不合理

## 八、使用說明
1. 查詢條件設定：
   - 輸入公司代號
   - 輸入部門代號
   - 選擇查詢選項

2. 功能操作說明：
   - 使用 PF3 返回前頁
   - 使用 PF12 返回前頁
   - 使用 PA1 查看下一頁
   - 使用 PA2 查看上一頁

3. 注意事項：
   - 公司代號必須為有效值
   - 部門代號必須為有效值
   - 明細資料每頁顯示13筆
   - 可查看預算名稱、金額、日期和類別
   - 預算日期格式為 YY/MM/DD 