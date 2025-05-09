# GLA160D 螢幕顯示檔案規格書

## 基本資訊
- 檔案名稱：GLA160D
- 檔案類型：螢幕顯示檔案 (DSPF)
- 來源目錄：QDDSSRC_GLPLIB
- 程式說明：科目明細表
- 系統：茂世會計系統
- 子系統：總帳系統
- 作者：JOYCE (A1087)
- 建立日期：1992.12.10
- 更新日期：無

## 螢幕規格
- 顯示大小：24x80
- 參考檔案：GLRF (總帳欄位定義檔)
- 螢幕代號：GLA160.1
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：CA03(03), CF04(04), CF14(14), CF18(18)

## 螢幕佈局
```
<GLA160.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                科目明細表                       時間: [時間]









                         會計科目代號: [  ] - [  ]

                         會計期間: [YYMMDD]

                         查詢選項: [ ] (1:查詢 2:列印)









                         會計年度: [   ]

                         會計月份: [  ]  期間範圍: [YYYY/MM/DD - YYYY/MM/DD]

                         科目範圍: [  ] - [  ]

                         科目類別範圍: [  ] - [  ]













                         列印份數: [   ]

                         列印代號: [  ]

[處理訊息顯示區域]

[科目資料清單]
序號  科目代號  科目名稱                          部門代號  部門名稱
----  --------  ------------------------------  --------  --------
[1]   [  ]      [                              ]  [  ]      [        ]
[2]   [  ]      [                              ]  [  ]      [        ]
[3]   [  ]      [                              ]  [  ]      [        ]
[4]   [  ]      [                              ]  [  ]      [        ]
[5]   [  ]      [                              ]  [  ]      [        ]
[6]   [  ]      [                              ]  [  ]      [        ]
[7]   [  ]      [                              ]  [  ]      [        ]
[8]   [  ]      [                              ]  [  ]      [        ]
[9]   [  ]      [                              ]  [  ]      [        ]
[10]  [  ]      [                              ]  [  ]      [        ]

[錯誤訊息顯示區域]
注意    PF3 =返回前頁    PF4 =查詢資料    PF14=批次處理    PF18=科目查詢
                                                           【茂世資訊】
```

## 記錄格式
### DSPD1 - 主畫面
- 游標位置控制
- 條件指示器：CA03(03), CF04(04), CF14(14), CF18(18)
- 強制資料顯示
- 鎖定模式
- 標題：<GLA160.1>
- 公司名稱：CONAME (32A, 輸出)
- 日期：DDATE (6Y, 輸出, 日期格式)
- 使用者：$USERN (10A, 輸出)

### 輸入欄位
1. 會計科目代號 (DAP01)
   - 參考欄位：AP01
   - 位置：5,39
   - 條件指示器：60

2. 會計期間 (DAP06)
   - 參考欄位：AP06
   - 位置：7,39
   - 格式：7位數字，日期格式
   - 條件指示器：61

3. 查詢選項 (DOP)
   - 位置：8,39
   - 選項值：1(查詢), 2(列印)
   - 說明：8,42

4. 會計期間設定
   - 會計年度 (DYEAR)：11,39
     - 格式：3位數字
     - 條件指示器：62
   - 會計月份 (DMM)：12,39
     - 格式：2位數字
     - 條件指示器：63
   - 期間範圍顯示：12,44-12,66

5. 科目範圍
   - 起始科目 (DAP02S)：13,39
   - 結束科目 (DAP02E)：13,51
   - 參考欄位：AP02
   - 條件指示器：64,65

6. 科目類別範圍
   - 起始類別 (DAP03S)：14,39
   - 結束類別 (DAP03E)：14,51
   - 參考欄位：AP03
   - 條件指示器：66,67

7. 列印設定
   - 列印份數 ($CPY)：16,39
     - 格式：3位數字
     - 必填欄位
   - 列印代號 ($PRTCD)：17,39
     - 格式：2位字元
     - 高亮度顯示

### 子檔案格式
1. SFLSRD/SFLCRD - 上層子檔案
   - 子檔案大小：60筆
   - 每頁顯示：10筆
   - 條件指示器：50,51,52
   - 欄位：
     - 序號 (RRND)
     - 科目相關欄位 (DAQ02D, DAQ02B, DAQ02A, DAQ12D)
     - 部門相關欄位 (DAH01D 至 DAH22D)

2. SFLSRC/SFLCRC - 下層子檔案
   - 子檔案大小：60筆
   - 每頁顯示：10筆
   - 條件指示器：50,51,52
   - 欄位：同上層子檔案

## 訊息顯示
1. 錯誤訊息 (ERRMSG)
   - 位置：22,2
   - 格式：70A
   - 條件指示器：99
   - 高亮度顯示

2. 處理訊息
   - 位置：21,28
   - 條件指示器：27,28
   - 顯示處理狀態和進度

## 功能鍵說明
| 功能鍵 | 說明 |
|-------|------|
| PF3 | 返回前頁 |
| PF4 | 查詢資料 |
| PF14 | 批次處理 |
| PF18 | 科目查詢 |

## 輸入欄位驗證
1. 會計科目代號 (DAP01)
   - 必填欄位
   - 格式：需符合科目代碼表

2. 會計期間 (DAP06)
   - 格式：YYYY/MM/DD
   - 需為有效日期

3. 會計年度和月份
   - 年度 (DYEAR)：3位數字
   - 月份 (DMM)：2位數字，1-12
   - 必填欄位

4. 科目範圍 (DAP02S/DAP02E)
   - 格式：需符合科目代碼表
   - 起始科目需小於等於結束科目

5. 科目類別範圍 (DAP03S/DAP03E)
   - 格式：需符合科目類別代碼表
   - 起始類別需小於等於結束類別

6. 列印份數 ($CPY)
   - 必填欄位
   - 格式：3位數字
   - 範圍：1-999

## 錯誤處理
1. 錯誤訊息顯示位置：第22行
2. 錯誤訊息類型：
   - 必填欄位未填
   - 資料格式錯誤
   - 日期範圍錯誤
   - 科目範圍錯誤
   - 系統錯誤

## 使用說明
1. 查詢條件設定：
   - 可設定會計科目代號
   - 可設定會計期間
   - 可選擇查詢或列印模式
   - 可設定會計年度和月份
   - 可設定科目範圍
   - 可設定科目類別範圍

2. 列印設定：
   - 可設定列印份數
   - 可選擇列印代號

3. 功能操作：
   - 可進行資料查詢
   - 可進行批次處理
   - 可進行科目查詢
   - 可返回前頁

4. 子檔案操作：
   - 上層子檔案顯示主要資料
   - 下層子檔案顯示明細資料
   - 每頁顯示10筆資料
   - 可上下捲動瀏覽 