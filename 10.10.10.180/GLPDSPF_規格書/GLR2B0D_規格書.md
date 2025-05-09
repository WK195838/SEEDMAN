# GLR2B0D 螢幕規格書

## 一、基本資訊
- 檔案名稱：GLR2B0D
- 檔案類型：螢幕顯示檔
- 來源目錄：10.10.10.180/QDDSSRC_GLPLIB
- 程式說明：結帳處理
- 系統：會計系統
- 子系統：總帳系統
- 作者：A1149 MAY
- 建立日期：1992.11.19
- 更新日期：
- 備註：結帳處理螢幕顯示

## 二、螢幕規格
- 顯示大小：24x80
- 參考檔案：*LIBL/GLRF
- 列印功能：支援
- 游標位置：變數 #LIN 和 #COL
- 功能鍵設定：
  - PF3：返回
  - PF4：查詢
  - PF14：處理年度

## 三、螢幕佈局

### 主畫面 (GLR2B0.1)
```
[公司名稱]                                    [系統日期]
[使用者代號]    結帳處理

公司代號: [    ]
會計期間: [  /  /  ]
會計月份: [ ] ( 1 - 8 )

處理選項: [ ] (0-查詢 1-列印 2-結帳)
公司代號: [   ]
處理代號: [  ]

***結帳處理中***
***處理完成請按Enter***

[錯誤訊息]

注意
PF3=返回前頁  PF4=重新查詢  PF14=處理年度
                                    (茂世電腦)
```

## 四、紀錄格式

### 主畫面 (DSPD1)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| #LIN | 1 | 3 | S | H | 游標行號 |
| #COL | 1 | 3 | S | H | 游標列號 |
| CONAME | 1,25 | 32 | A | O | 公司名稱 |
| DDATE | 1,69 | 6 | Y | O | 系統日期 |
| $USERN | 2,2 | 10 | A | O | 使用者代號 |
| DAH01 | 5,42 | 4 | A | B | 公司代號 |
| DAH10 | 7,42 | 7 | 0 | B | 會計期間 |
| DOPT | 8,42 | 1 | A | B | 會計月份 |
| $PENV | 15,41 | 1 | A | B | 處理選項 |
| $CPY | 16,41 | 3 | Y | B | 公司代號 |
| $PRTCD | 17,41 | 2 | A | B | 處理代號 |
| ERRID | 22,2 | 7 | A | H | 錯誤代號 |
| ERRF | 22,2 | 10 | A | H | 錯誤檔案 |
| ERRMSG | 22,2 | 70 | A | O | 錯誤訊息 |

## 五、功能鍵說明
1. PF3：返回前頁
   - 功能：返回上一頁
   - 使用時機：需要返回時

2. PF4：重新查詢
   - 功能：重新執行查詢
   - 使用時機：需要重新查詢時

3. PF14：處理年度
   - 功能：處理年度資料
   - 使用時機：需要處理年度資料時

## 六、輸入欄位驗證
1. 必填欄位：
   - 公司代號 (DAH01)
   - 會計期間 (DAH10)
   - 會計月份 (DOPT)
   - 處理選項 ($PENV)
   - 公司代號 ($CPY)
   - 處理代號 ($PRTCD)

2. 資料格式：
   - 公司代號：4位字元
   - 會計期間：7位數值，格式為YY/MM/DD
   - 會計月份：1位字元，值為'1'到'8'
   - 處理選項：1位字元，值為'0'、'1'或'2'
   - 公司代號：3位數值
   - 處理代號：2位字元

## 七、錯誤處理
1. 錯誤訊息顯示位置：
   - 位置：第22行
   - 格式：錯誤代號 + 錯誤檔案 + 錯誤訊息

2. 錯誤類型：
   - 必填欄位未輸入
   - 資料格式錯誤
   - 處理錯誤
   - 系統錯誤

## 八、使用說明
1. 操作步驟：
   - 輸入公司代號
   - 輸入會計期間
   - 輸入會計月份
   - 選擇處理選項
   - 輸入公司代號
   - 輸入處理代號
   - 按Enter執行處理
   - 按PF3返回前頁
   - 按PF4重新查詢
   - 按PF14處理年度

2. 注意事項：
   - 所有必填欄位必須輸入
   - 資料格式必須正確
   - 會計月份必須為'1'到'8'
   - 處理選項必須為'0'、'1'或'2'
   - 公司代號必須存在
   - 處理代號必須正確 