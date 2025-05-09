# GLA353D 螢幕顯示檔案規格書

## 基本資訊
- 檔案名稱：GLA353D
- 檔案類型：螢幕顯示檔案 (DSPF)
- 來源目錄：QDDSSRC_GLPLIB
- 程式說明：會計科目格式設定明細處理畫面
- 系統：茂世會計系統
- 子系統：總帳系統
- 作者：MAY (A1149)
- 建立日期：1992.11.02
- 更新日期：無

## 螢幕規格
- 顯示大小：24x80
- 參考檔案：GLRF (總帳欄位定義檔)
- 螢幕代號：GLA353.1
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：CA03(03), CF04(04), CF05(05), CF12(12)

## 螢幕佈局
```
<GLA353.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                會計科目格式設定明細處理畫面        時間: [時間]









          公司代號: [  ] - [  ]  公司名稱: [                              ]

          會計科目代號: [        ]  會計科目名稱: [                              ]

          會計科目格式: [  ] [  ] [  ]

          處理選項: [ ] (1.新增 2.修改 4.刪除 5.查詢)

          會計科目編號: [                                                  ]

          會計科目類型: [ ] (1.借方 2.貸方)

[會計科目格式明細清單]
序號  會計科目  加減號  會計科目名稱        會計科目類別  會計科目格式  會計科目說明  會計科目備註
----  --------  ------  ----------------  -----------  -----------  -----------  -------------------
[001] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[002] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[003] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[004] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[005] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[006] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[007] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[008] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]
[009] [        ]  [  ]  [                ]  [          ]  [  ] [  ]  [        ]  [                                  ]

[會計科目類別說明]
@S -借方 @T -明細處理 @- -無效 @C -取消

[錯誤訊息顯示區域]
注意    PF3 =返回前頁    PF4 =查詢資料    PF5 =開始處理    PF12=返回前一頁
注意    PA1 =下一頁      PA2 =上一頁
                                                           【茂世資訊】
```

## 記錄格式
### SFLSR - 子檔案記錄
- 條件指示器：54 (SFLNXTCHG)
- 新增標記 (DNEW)：1位元
- 記錄編號 (F#RRN)：4S
- 刪除選項 (DDEL)：1位元，值：'4', ' '
- 條件指示器：32, 31
- 顯示屬性：UL, PR

### 子檔案欄位
1. 會計科目代號 (DAS04)
   - 位置：12,4
   - 參考欄位：AS04
   - 條件指示器：62
   - 顯示屬性：PC, RI, UL, PR

2. 加減號 (DAS05)
   - 位置：12,10
   - 格式：1A
   - 值：'+', '-', ' '
   - 條件指示器：63
   - 顯示屬性：PC, RI, UL, PR

3. 會計科目名稱 (DAS06)
   - 位置：12,13
   - 參考欄位：AS06
   - 條件指示器：64, 99
   - 顯示屬性：PC, RI, UL, PR, HI

4. 會計科目類別 (DAS07)
   - 位置：12,23
   - 參考欄位：AS07
   - 條件指示器：65, 99
   - 顯示屬性：PC, RI, UL, PR, HI

5. 會計科目格式 (DAS08, DAS09)
   - 位置：12,32-34
   - 參考欄位：AS08, AS09
   - 值：'V', ' '
   - 條件指示器：66, 67
   - 顯示屬性：PC, RI, UL, PR

6. 會計科目說明 (A)
   - 位置：12,37
   - 格式：8A
   - 條件指示器：68, 99
   - 顯示屬性：PC, RI, UL, PR, HI

7. 會計科目備註 (DAS10)
   - 位置：12,46
   - 格式：34O
   - 條件指示器：69
   - 顯示屬性：PC, RI, UL, PR

### SFLCR - 子檔案控制
- 子檔案大小：65筆
- 每頁顯示：9筆
- 覆蓋顯示
- 游標位置控制：#LIN, #COL
- 條件指示器：CA03(03), CF04(04), CF05(05), CF12(12)
- 捲動行數：25
- 訊息ID：CPF5203

### 主畫面欄位
1. 公司名稱 (CONAME)
   - 位置：1,25
   - 格式：32A
   - 訊息ID：US# 9001 S#MF

2. 日期 (DDATE)
   - 位置：1,71
   - 格式：6Y
   - 編輯碼：Y

3. 使用者 ($USERN)
   - 位置：2,2
   - 格式：10A

4. 公司代號 (DAR01)
   - 位置：4,16
   - 參考欄位：AR01

5. 公司名稱 (D#B02)
   - 位置：4,20
   - 參考欄位：#B02 PT#BPF

6. 會計科目代號 (DAR02)
   - 位置：5,16
   - 參考欄位：AR02

7. 會計科目名稱 (DAR03)
   - 位置：5,19
   - 參考欄位：AR03

8. 會計科目格式 (DAR01C, DAR02C, DAR03C)
   - 位置：5,32-38
   - 參考欄位：AR01, AR02, AR03

9. 處理選項 (DOPT)
   - 位置：6,16
   - 格式：1Y
   - 編輯碼：4
   - 值：1, 2, 4, 5
   - 說明：(1.新增 2.修改 4.刪除 5.查詢)

10. 會計科目編號 (DAR04)
    - 位置：8,16
    - 參考欄位：AR04
    - 條件指示器：60
    - 顯示屬性：PC, RI, UL, PR

11. 會計科目類型 (DAR05)
    - 位置：8,57
    - 參考欄位：AR05
    - 值：'1', '2'
    - 條件指示器：61
    - 顯示屬性：PC, RI, UL, PR
    - 說明：(1.借方 2.貸方)

## 訊息顯示
1. 錯誤訊息 (ERRMSG)
   - 位置：22,2
   - 格式：70A
   - 條件指示器：99
   - 高亮度顯示

2. 會計科目類別說明
   - 位置：21,2
   - 說明：@S -借方 @T -明細處理 @- -無效 @C -取消

## 功能鍵說明
| 功能鍵 | 說明 |
|-------|------|
| PF3 | 返回前頁 |
| PF4 | 查詢資料 |
| PF5 | 開始處理 |
| PF12 | 返回前一頁 |
| PA1 | 下一頁 |
| PA2 | 上一頁 |

## 輸入欄位驗證
1. 公司代號 (DAR01)
   - 必填欄位
   - 需為有效公司代號

2. 會計科目代號 (DAR02)
   - 必填欄位
   - 需為有效會計科目代號

3. 會計科目名稱 (DAR03)
   - 必填欄位
   - 需為有效會計科目名稱

4. 會計科目編號 (DAR04)
   - 必填欄位
   - 需為有效會計科目編號

5. 會計科目類型 (DAR05)
   - 必填欄位
   - 值需為 '1' 或 '2'

## 錯誤處理
1. 錯誤訊息顯示位置：第22行
2. 錯誤訊息類型：
   - 必填欄位未填
   - 資料格式錯誤
   - 公司代號錯誤
   - 會計科目錯誤
   - 系統錯誤

## 使用說明
1. 查詢條件設定：
   - 需輸入公司代號
   - 需輸入會計科目代號
   - 需輸入會計科目名稱
   - 需選擇處理選項

2. 會計科目格式維護：
   - 可新增會計科目格式
   - 可修改會計科目格式
   - 可刪除會計科目格式
   - 可查詢會計科目格式

3. 功能操作：
   - 可進行資料查詢
   - 可進行資料處理
   - 可返回前頁
   - 可切換頁面

4. 注意事項：
   - 公司代號、會計科目代號和名稱為必填欄位
   - 會計科目類型需設定為 1 或 2
   - 處理選項需選擇 1, 2, 4, 5 其中之一
   - 處理完成後會顯示處理結果 