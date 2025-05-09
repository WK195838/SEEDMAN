# GLA360D 螢幕顯示檔案規格書

## 基本資訊
- 檔案名稱：GLA360D
- 檔案類型：螢幕顯示檔案 (DSPF)
- 來源目錄：QDDSSRC_GLPLIB
- 程式說明：會計期間設定
- 系統：茂世會計系統
- 子系統：總帳系統
- 作者：JANE (A1139)
- 建立日期：1992.11.02
- 更新日期：無

## 螢幕規格
- 顯示大小：24x80
- 參考檔案：GLRF (總帳欄位定義檔)
- 螢幕代號：GLA360.1
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：CA03(03), CF12(12)

## 螢幕佈局
```
<GLA360.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                會計期間設定                       時間: [時間]









          公司代號: [  ] - [  ]  公司名稱: [                              ]

          年度: [   ]  年度格式: [   ]

          處理選項: [ ] (1.新增 2.修改 4.刪除 5.查詢)

[期間設定明細]
期間  開始日期  結束日期  會計科目
----  --------  --------  --------
01    [  /  /  ]  [  /  /  ]  [        ]
02    [  /  /  ]  [  /  /  ]  [        ]
03    [  /  /  ]  [  /  /  ]  [        ]
04    [  /  /  ]  [  /  /  ]  [        ]
05    [  /  /  ]  [  /  /  ]  [        ]
06    [  /  /  ]  [  /  /  ]  [        ]
07    [  /  /  ]  [  /  /  ]  [        ]
08    [  /  /  ]  [  /  /  ]  [        ]
09    [  /  /  ]  [  /  /  ]  [        ]
10    [  /  /  ]  [  /  /  ]  [        ]
11    [  /  /  ]  [  /  /  ]  [        ]
12    [  /  /  ]  [  /  /  ]  [        ]

[錯誤訊息顯示區域]
注意    PF3 =返回前頁    PF12=返回前一頁
                                                           【茂世資訊】
```

## 記錄格式
### DSPD1 - 主畫面
- 條件指示器：CA03(03)
- 錯誤訊息ID (ERRID)：7A
- 錯誤訊息檔案 (ERRF)：10A

### 主畫面欄位
1. 公司名稱 (CONAME)
   - 位置：1,25
   - 格式：32A
   - 訊息ID：US# 9001 S#MF

2. 日期 (DDATE)
   - 位置：1,72
   - 格式：6Y
   - 編輯碼：Y

3. 使用者 ($USERN)
   - 位置：2,2
   - 格式：10A

4. 公司代號 (DAC01)
   - 位置：4,14
   - 參考欄位：AC01
   - 條件指示器：60
   - 顯示屬性：PC, RI

5. 年度 (DAC02)
   - 位置：5,14
   - 格式：3Y
   - 編輯碼：2
   - 條件指示器：61
   - 顯示屬性：PC, RI

6. 公司代號格式 (DAC01C)
   - 位置：5,28
   - 參考欄位：AC01
   - 條件指示器：62
   - 顯示屬性：PC, RI

7. 年度格式 (DAC02C)
   - 位置：5,31
   - 格式：3Y
   - 編輯碼：2
   - 條件指示器：63
   - 顯示屬性：PC, RI

8. 處理選項 (DOPT)
   - 位置：6,14
   - 格式：1Y
   - 編輯碼：4
   - 值：1, 2, 4, 5
   - 說明：(1.新增 2.修改 4.刪除 5.查詢)

### DSPD2 - 明細畫面
- 條件指示器：CA03(03), CF12(12)
- 錯誤訊息ID (ERRID)：7A
- 錯誤訊息檔案 (ERRF)：10A

### 明細畫面欄位
1. 公司名稱 (CONAME)
   - 位置：1,25
   - 格式：32A
   - 訊息ID：US# 9001 S#MF

2. 日期 (DDATE)
   - 位置：1,72
   - 格式：6Y
   - 編輯碼：Y

3. 使用者 ($USERN)
   - 位置：2,2
   - 格式：10A

4. 公司代號 (DAC01)
   - 位置：4,14
   - 參考欄位：AC01

5. 公司名稱 (#B02)
   - 位置：4,17
   - 參考欄位：#B02 *LIBL/PTRF

6. 年度 (DAC02)
   - 位置：5,14
   - 格式：3Y
   - 編輯碼：3

7. 公司代號格式 (DAC01C)
   - 位置：5,28
   - 參考欄位：AC01

8. 年度格式 (DAC02C)
   - 位置：5,31
   - 格式：3Y
   - 編輯碼：2

9. 處理選項 (DOPT)
   - 位置：6,14
   - 格式：1Y
   - 編輯碼：4
   - 值：1, 2, 4, 5
   - 說明：(1.新增 2.修改 4.刪除 5.查詢)

10. 期間設定 (D01S-D12E)
    - 位置：10-15行
    - 格式：7位元
    - 編輯碼：'   /  /  '
    - 條件指示器：60-72
    - 顯示屬性：PC, RI, UL, PR

11. 會計科目 (DAC03-DAC14)
    - 位置：10-15行
    - 參考欄位：AC03-AC14
    - 條件指示器：60-72
    - 顯示屬性：PC, RI, UL, PR

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

## 輸入欄位驗證
1. 公司代號 (DAC01)
   - 必填欄位
   - 需為有效公司代號

2. 年度 (DAC02)
   - 必填欄位
   - 需為有效年度

3. 處理選項 (DOPT)
   - 必填欄位
   - 值需為 1, 2, 4, 5 其中之一

4. 期間設定 (D01S-D12E)
   - 必填欄位
   - 需為有效日期格式

5. 會計科目 (DAC03-DAC14)
   - 必填欄位
   - 需為有效會計科目

## 錯誤處理
1. 錯誤訊息顯示位置：第22行
2. 錯誤訊息類型：
   - 必填欄位未填
   - 資料格式錯誤
   - 公司代號錯誤
   - 年度錯誤
   - 期間設定錯誤
   - 會計科目錯誤
   - 系統錯誤

## 使用說明
1. 查詢條件設定：
   - 需輸入公司代號
   - 需輸入年度
   - 需選擇處理選項

2. 會計期間維護：
   - 可新增會計期間
   - 可修改會計期間
   - 可刪除會計期間
   - 可查詢會計期間

3. 功能操作：
   - 可進行資料查詢
   - 可進行資料處理
   - 可返回前頁

4. 注意事項：
   - 公司代號和年度為必填欄位
   - 處理選項需選擇 1, 2, 4, 5 其中之一
   - 期間設定需符合日期格式
   - 會計科目需為有效科目
   - 處理完成後會顯示處理結果 