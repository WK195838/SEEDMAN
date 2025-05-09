# GLA450D 螢幕顯示檔案規格書

## 基本資訊
- 檔案名稱：GLA450D
- 檔案類型：螢幕顯示檔案 (DSPF)
- 來源目錄：QDDSSRC_GLPLIB
- 程式說明：部門專案格式設定處理
- 系統：茂世會計系統
- 子系統：總帳系統
- 作者：ANGY (A1152)
- 建立日期：1992.10.28
- 更新日期：無

## 螢幕規格
- 顯示大小：24x80
- 參考檔案：GLRF (總帳欄位定義檔)
- 螢幕代號：GLA450.1
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：CA03(03), CF18(18)

## 螢幕佈局
```
<GLA450.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                部門專案格式設定處理               時間: [時間]









          公司代號: [  ] - [  ]  公司名稱: [                              ]

          部門代號: [        ]  部門名稱: [                              ]

          專案代號: [        ]  專案名稱: [                              ]

          公司代號格式: [  ]  部門代號格式: [  ]  專案代號格式: [  ]

          處理選項: [ ] (1.新增 2.修改 4.刪除 5.查詢)

[部門專案格式設定]
  部門代號: [        ]
  專案代號: [        ]
  專案名稱: [                              ]
  專案類別: [ ] (1.專案 2.預算)

[錯誤訊息顯示區域]
注意    PF3 =返回前頁    PF12=返回前一頁    PF18=批次查詢
                                                           【茂世資訊】
```

## 記錄格式
### DSPD1 - 主畫面
- 條件指示器：CA03(03), CF18(18)
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

4. 公司代號 (DAE01)
   - 位置：4,14
   - 參考欄位：AE01
   - 條件指示器：60
   - 顯示屬性：PC, RI

5. 部門代號 (DAE02)
   - 位置：5,14
   - 參考欄位：AE02
   - 條件指示器：61
   - 顯示屬性：PC, RI

6. 專案代號 (DAE03)
   - 位置：6,14
   - 參考欄位：AE03
   - 條件指示器：62
   - 顯示屬性：PC, RI

7. 公司代號格式 (DAE01C)
   - 位置：7,33
   - 參考欄位：AE01
   - 條件指示器：63
   - 顯示屬性：PC, RI

8. 部門代號格式 (DAE02C)
   - 位置：7,36
   - 參考欄位：AE02
   - 條件指示器：64
   - 顯示屬性：PC, RI

9. 專案代號格式 (DAE03C)
   - 位置：7,39
   - 參考欄位：AE03
   - 條件指示器：65
   - 顯示屬性：PC, RI

10. 處理選項 (DOPT)
    - 位置：8,14
    - 格式：1Y
    - 編輯碼：4
    - 值：1, 2, 4, 5
    - 說明：(1.新增 2.修改 4.刪除 5.查詢)

### DSPD2 - 明細畫面
- 條件指示器：CA03(03), CF12(12)
- 錯誤訊息ID (ERRID)：7A
- 錯誤訊息檔案 (ERRF)：10A

### 明細畫面欄位
1. 部門代號 (DAE04)
   - 位置：12,14
   - 參考欄位：AE04
   - 條件指示器：60, 31
   - 顯示屬性：PC, RI, UL, PR

2. 專案代號 (DAE05)
   - 位置：13,14
   - 參考欄位：AE05
   - 條件指示器：61, 31
   - 顯示屬性：PC, RI, UL, PR

3. 專案名稱 (DAE06)
   - 位置：14,14
   - 參考欄位：AE06
   - 條件指示器：31
   - 顯示屬性：UL, PR

4. 專案類別 (DAE07)
   - 位置：15,14
   - 參考欄位：AE07
   - 值：'1', '2'
   - 條件指示器：31
   - 顯示屬性：UL, PR
   - 說明：(1.專案 2.預算)

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
| PF18 | 批次查詢 |

## 輸入欄位驗證
1. 公司代號 (DAE01)
   - 必填欄位
   - 需為有效公司代號

2. 部門代號 (DAE02)
   - 必填欄位
   - 需為有效部門代號

3. 專案代號 (DAE03)
   - 必填欄位
   - 需為有效專案代號

4. 處理選項 (DOPT)
   - 必填欄位
   - 值需為 1, 2, 4, 5 其中之一

5. 專案類別 (DAE07)
   - 必填欄位
   - 值需為 '1' 或 '2'

## 錯誤處理
1. 錯誤訊息顯示位置：第22行
2. 錯誤訊息類型：
   - 必填欄位未填
   - 資料格式錯誤
   - 公司代號錯誤
   - 部門代號錯誤
   - 專案代號錯誤
   - 專案名稱錯誤
   - 專案類別錯誤
   - 系統錯誤

## 使用說明
1. 查詢條件設定：
   - 需輸入公司代號
   - 需輸入部門代號
   - 需輸入專案代號
   - 需選擇處理選項

2. 部門專案格式維護：
   - 可新增部門專案格式
   - 可修改部門專案格式
   - 可刪除部門專案格式
   - 可查詢部門專案格式

3. 功能操作：
   - 可進行資料查詢
   - 可返回前頁
   - 可進行批次查詢

4. 注意事項：
   - 公司代號為必填欄位
   - 部門代號為必填欄位
   - 專案代號為必填欄位
   - 處理選項需選擇 1, 2, 4, 5 其中之一
   - 專案類別需為 1 或 2
   - 處理完成後會顯示處理結果 