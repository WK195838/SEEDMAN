# GAR103D 螢幕顯示檔案規格書

## 基本資訊
- 檔案名稱: GAR103D
- 檔案類型: 顯示檔案 (DSPF)
- 來源目錄: QDDSSRC_GLPLIB
- 程式說明: 參數日曆系統管理報表
- 系統: 總帳系統
- 修改記錄: 19940414 (SD D910121)

## 螢幕規格
- 顯示大小: 24行 x 80列
- 參考檔案: *LIBL/GLRF (引用總帳參考欄位定義檔)
- 螢幕代號: GAR103.1

## 記錄格式
- 記錄格式名稱: DSPD1
- 功能鍵設定: 
  - CA03(03) - 返回主畫面
  - CF04(04) - 重新查詢
  - CF14(14) - 處理作業
- 游標位置: CSRLOC(#LIN #COL)

## 螢幕佈局
```
<GAR103.1>                     [公司名稱]                        [日期]
[使用者ID]                   測試參數系統報表

                         


                         
                         
                         
                         
                         

                         輸出裝置: [ ] (0-螢幕 1-印表 2-檔案)

                         列印份數: [   ]

                         列印機台: [  ]


[錯誤訊息顯示區域]
注意    PF3 =回主畫面    PF4 =重新查詢    PF14 =處理作業
                                                           【茂世資訊】
```

## 欄位規格
| 欄位名稱 | 參考欄位 | 說明 | 資料型態 | 長度 | 輸入/輸出 | 屬性 | 編輯碼/格式 |
|---------|---------|------|---------|------|---------|------|------------|
| #LIN | - | 游標行位置 | 數值 | 3S,0 | H | - | - |
| #COL | - | 游標列位置 | 數值 | 3S,0 | H | - | - |
| CONAME | - | 公司名稱 | 字元 | 32A | O | - | 訊息ID: US# 9001 S#MF |
| DDATE | - | 系統日期 | 數值 | 6Y,0 | O | - | EDTCDE(Y) |
| $USERN | - | 使用者ID | 字元 | 10A | O | - | - |
| $PENV | - | 輸出裝置 | 字元 | 1A | B | - | VALUES('0', '1', '2') |
| $CPY | - | 列印份數 | 數值 | 3Y,0 | B | - | EDTCDE(3), CHECK(RB) |
| $PRTCD | - | 列印機台 | 字元 | 2A | B | 條件HI(非99) | - |
| ERRID | - | 錯誤訊息ID | 字元 | 7A | H | - | - |
| ERRF | - | 錯誤訊息檔案 | 字元 | 10A | H | - | - |
| ERRMSG | - | 錯誤訊息內容 | 字元 | 70A | O | HI | MSGID(&ERRID &ERRF) |

## 條件指示器
| 指示器 | 說明 | 用途 |
|-------|------|------|
| 28 | 強制資料輸入指示 | 控制FRCDTA與LOCK屬性 |
| 27 | 錯誤訊息顯示指示 | 控制「請正確輸入各欄位資料」訊息 |
| 99 | 隱藏條件指示 | 控制錯誤訊息顯示 |

## 功能鍵
| 功能鍵 | 說明 | 作用 |
|-------|------|------|
| PF3 (CA03) | 回主畫面 | 返回上一層主選單 |
| PF4 (CF04) | 重新查詢 | 清除已輸入的條件 |
| PF14 (CF14) | 處理作業 | 執行處理作業 |

## 輸入欄位檢核
1. 輸出裝置($PENV): 限制只能輸入0、1或2
   - 0: 螢幕
   - 1: 印表
   - 2: 檔案
2. 列印份數($CPY): 使用CHECK(RB)只允許數字，使用EDTCDE(3)添加千位分隔符
3. 列印機台($PRTCD): 由指示器控制高亮顯示，當非相關條件時隱藏

## 錯誤處理
- 整體錯誤透過指示器27顯示「請正確輸入各欄位資料」訊息
- 處理中使用指示器28顯示「正在處理中，請等待」訊息
- 特定錯誤訊息通過ERRMSG欄位與MSGID功能顯示

## 使用說明
1. 此螢幕用於產生參數日曆系統管理報表
2. 使用者可選擇輸出方式、列印份數及印表機
3. 按PF3返回主選單，按PF4重新設定查詢條件，按PF14執行處理

## 程式功能
1. 程式主要用於系統管理員測試與維護參數日曆系統
2. 可產生系統設定與參數使用狀況的報表
3. 提供系統測試與資料檢查的功能

## 備註
- 本螢幕採用DS3設備規格
- 使用指示器28控制處理中的畫面鎖定
- 畫面右下角顯示系統開發公司名稱【茂世資訊】
- 此畫面較簡單，僅提供輸出控制選項，無需多項查詢條件
- 此功能主要供系統管理使用，非一般使用者常用功能 