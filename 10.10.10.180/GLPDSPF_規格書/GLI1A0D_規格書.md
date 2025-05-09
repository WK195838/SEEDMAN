# GLI1A0D 螢幕顯示檔規格書

## 一、基本資訊
- 檔案名稱：GLI1A0D
- 檔案類型：螢幕顯示檔
- 來源目錄：10.10.10.180/QDDSSRC_GLPLIB
- 程式說明：傳票查詢
- 系統：會計總帳系統
- 子系統：會計總帳系統
- 作者：A1139 JANE
- 建立日期：1992.11.10
- 更新日期：1994.06.20 (由 GRACE 更新)

## 二、螢幕規格
- 顯示大小：24x80
- 參考檔案：GLFLIB/GLRF
- 螢幕代號：GLI1A0.1
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：
  - 50：明細資料顯示控制
  - 51：明細資料控制顯示
  - 52：明細資料清除控制
  - 53：明細資料結束控制
  - 54：明細資料變更控制
  - 60：公司代號顯示控制
  - 61：科目代號顯示控制
  - 96：訊息ID控制
  - 99：錯誤訊息控制

## 三、螢幕佈局

### 主畫面 (GLI1A0.1)
```
<GLI1A0.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                    傳票查詢                       時間: [時間]

公司代號: [    ] [公司名稱]    大日期: [  /  /  ]    小日期: [    ]
科目代號: [    ] [科目名稱]    科目日: [  /  /  ]    小科目: [  /  /  ]
S=5:傳票查詢    預算     [預算代號]    科目     [科目代號]    傳票日期: [    ]

---------------------------------------------------------
S No傳票日期 - 傳票號碼 - 摘要 - 借方金額 - 貸方金額
---------------------------------------------------------
[明細資料顯示區域]
---------------------------------------------------------
[合計區域]
---------------------------------------------------------
[錯誤訊息顯示區域]
注意    PF2 =傳票查詢    PF3 =返回前頁    PF7 =上一頁    PF8 =下一頁
注意    PF12=返回前頁    PA1 =下一頁    PA2 =上一頁
                                                           【茂世資訊】
```

## 四、記錄格式

### 明細畫面 (SFLSR)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| DOPT | 9,2 | 1 | B | O | 選項 |
| RRN | 9,4 | 3 | Y | O | 記錄編號 |
| DAH04 | 9,8 | 16 | - | O | 傳票日期 |
| DAF03 | 9,25 | 22 | - | O | 傳票號碼 |
| DAH12 | 9,48 | 12 | 2 | O | 借方金額 |
| DAH13 | 9,65 | 12 | 2 | O | 貸方金額 |
| AH16 | 10,23 | - | R | O | 摘要 |

### 合計畫面 (DSPC1)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| TAH12 | 20,46 | 13 | 2 | O | 借方合計 |
| TAH13 | 20,64 | 13 | 2 | O | 貸方合計 |

## 五、功能鍵說明
- PF2：傳票查詢
- PF3：返回前頁
- PF7：上一頁
- PF8：下一頁
- PF12：返回前頁
- PA1：下一頁
- PA2：上一頁

## 六、輸入欄位驗證
1. 必填欄位：
   - 公司代號 (DAH01)
   - 科目代號 (DAH02)

2. 資料格式：
   - 公司代號：必須為有效公司代號
   - 科目代號：必須為有效科目代號
   - 日期格式：必須為有效日期格式 (YY/MM/DD)
   - 金額格式：必須為有效金額格式

## 七、錯誤處理
- 錯誤訊息顯示位置：第22行
- 錯誤訊息格式：
  - MSGID(&ERRID &ERRF)：動態錯誤訊息
- 錯誤類型：
  - 必填欄位未輸入
  - 資料格式錯誤
  - 公司代號不存在
  - 科目代號不存在
  - 查詢條件不合理

## 八、使用說明
1. 查詢條件設定：
   - 輸入公司代號
   - 輸入科目代號
   - 設定日期範圍
   - 選擇查詢選項 (S=5:傳票查詢)

2. 功能操作說明：
   - 使用PF2進行傳票查詢
   - 使用PF3返回前頁
   - 使用PF7/PA2查看上一頁
   - 使用PF8/PA1查看下一頁
   - 使用PF12返回前頁

3. 注意事項：
   - 公司代號必須為有效值
   - 科目代號必須為有效值
   - 日期格式必須正確 (YY/MM/DD)
   - 金額格式必須正確
   - 明細資料每頁顯示5筆
   - 合計區域顯示借方和貸方總額 