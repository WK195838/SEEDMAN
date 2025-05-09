# GLA210D 螢幕顯示檔案規格書

## 基本資訊
- 檔案名稱：GLA210D
- 檔案類型：螢幕顯示檔案 (DSPF)
- 來源目錄：QDDSSRC_GLPLIB
- 程式說明：會計科目餘額查詢畫面
- 系統：茂世會計系統
- 子系統：總帳系統
- 作者：A1150
- 建立日期：1981.12.28
- 更新日期：無

## 螢幕規格
- 顯示大小：24x80
- 參考檔案：GLRF (總帳欄位定義檔)
- 螢幕代號：GLA210.1
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：CA03(03), CF18(18)

## 螢幕佈局
```
<GLA210.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                會計科目餘額查詢畫面              時間: [時間]









          公司代號: [  ] - [  ]

          會計年度: [    ]













[處理訊息顯示區域]

[科目餘額資料清單]
選項  序號  科目代號  科目名稱                          期初餘額  期末餘額  借方金額  貸方金額
----  ----  --------  ------------------------------  --------  --------  --------  --------
[ ]   [001] [        ]  [                              ]  [        ]  [        ]  [        ]  [        ]
[ ]   [002] [        ]  [                              ]  [        ]  [        ]  [        ]  [        ]
[ ]   [003] [        ]  [                              ]  [        ]  [        ]  [        ]  [        ]
[ ]   [004] [        ]  [                              ]  [        ]  [        ]  [        ]  [        ]
[ ]   [005] [        ]  [                              ]  [        ]  [        ]  [        ]  [        ]
[ ]   [006] [        ]  [                              ]  [        ]  [        ]  [        ]  [        ]

[錯誤訊息顯示區域]
注意    PF3 =返回前頁    PF12=返回前一頁    PF18=開始查詢
                                                           【茂世資訊】
```

## 記錄格式
### DSPD1 - 主畫面
- 條件指示器：CA03(03), CF18(18)
- 標題：<GLA210.1>
- 公司名稱：CONAME (32A, 輸出)
- 日期：DDATE (6Y, 輸出, 日期格式)
- 使用者：$USERN (10A, 輸出)

### 輸入欄位
1. 公司代號 (DAF01)
   - 位置：4,14
   - 參考欄位：AF01
   - 條件指示器：60
   - 顯示屬性：PC, RI

2. 會計年度 (DAF02)
   - 位置：5,14
   - 參考欄位：AF02
   - 條件指示器：61
   - 顯示屬性：PC, RI

### SFLSR - 子檔案記錄
- 選項 (DOPT)：1A, 值：'/' 或 ' '
- 記錄編號 (RRN)：3Y, 編輯碼：4
- 科目資料欄位：
  - AE02, AE041-AE045 (金額)
  - AE051-AE055 (借貸方)

### SFLCR - 子檔案控制
- 條件指示器：CF12(12)
- 捲動：25行
- 覆蓋顯示
- 子檔案大小：10筆
- 每頁顯示：6筆
- 訊息ID：CPF5203

### DSPC1 - 控制畫面
- 錯誤訊息顯示
- 功能鍵說明

## 訊息顯示
1. 錯誤訊息 (ERRMSG)
   - 位置：22,2
   - 格式：70A
   - 條件指示器：99
   - 高亮度顯示

## 功能鍵說明
| 功能鍵 | 說明 |
|-------|------|
| PF3 | 返回前頁 |
| PF12 | 返回前一頁 |
| PF18 | 開始查詢 |

## 輸入欄位驗證
1. 公司代號 (DAF01)
   - 必填欄位
   - 需為有效公司代號

2. 會計年度 (DAF02)
   - 必填欄位
   - 需為有效年度

## 錯誤處理
1. 錯誤訊息顯示位置：第22行
2. 錯誤訊息類型：
   - 必填欄位未填
   - 資料格式錯誤
   - 公司代號錯誤
   - 年度錯誤
   - 系統錯誤

## 使用說明
1. 查詢條件設定：
   - 需輸入公司代號
   - 需輸入會計年度

2. 資料顯示：
   - 顯示科目餘額資料
   - 可選擇特定科目
   - 顯示借貸方金額

3. 功能操作：
   - 可進行資料查詢
   - 可返回前頁
   - 可返回前一頁

4. 注意事項：
   - 公司代號和會計年度為必填欄位
   - 查詢結果以子檔案方式顯示
   - 可選擇特定科目進行查詢 