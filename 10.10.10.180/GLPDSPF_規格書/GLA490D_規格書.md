# GLA490D 螢幕顯示檔規格書

## 一、基本資訊
- 檔案名稱：GLA490D
- 檔案類型：螢幕顯示檔
- 來源目錄：10.10.10.180/QDDSSRC_GLPLIB
- 程式說明：採購單據格式設定
- 系統：會計總帳系統
- 子系統：會計總帳系統
- 作者：ANGY (A1152)
- 建立日期：1992.10.30
- 更新日期：

## 二、螢幕規格
- 顯示大小：24x80
- 參考檔案：GLRF
- 訊息位置：第22行
- 列印功能：支援
- 條件指示器：
  - CA03(03)：主畫面顯示控制
  - CF14(14)：批次處理控制

## 三、螢幕佈局
```
<GLA490.1>                [公司名稱]                       日期: [YYMMDD]
[使用者ID]                採購單據格式設定                   時間: [時間]









          起始採購單號: [        ]  結束採購單號: [        ]

          起始傳票: [    ]  結束傳票: [    ]

          處理選項: [ ] (1.設定採購單 2.設定採購單及允許 3.設定採購單及允許檢查)

[採購單據格式明細]
  傳票號碼: [    ]
  採購單號: [        ]
  是否允許: [ ]

[錯誤訊息顯示區域]
注意    PF3 =返回前頁    PF14=批次處理傳票
                                                           【茂世資訊】
```

## 四、記錄格式

### 1. 主畫面 (DSPD1)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| CONAME | 1,25 | 32 | A | O | 公司名稱 |
| DDATE | 1,72 | 6 | Y | O | 系統日期 |
| $USERN | 2,2 | 10 | A | O | 使用者代號 |
| DAE01F | 4,19 | - | R | B | 起始採購單號 |
| DAE02F | 5,19 | - | R | B | 起始傳票 |
| DAE02T | 5,24 | - | R | B | 結束傳票 |
| DAE01T | 7,19 | - | R | B | 結束採購單號 |
| DOPT | 9,19 | 1 | Y | B | 處理選項 |
| ERRMSG | 22,2 | 70 | A | O | 錯誤訊息 |

### 2. 明細畫面 (DSPD2)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| DAE02 | 17,17 | - | R | O | 傳票號碼 |
| DAE03 | 18,17 | - | R | O | 採購單號 |
| COVE | 19,17 | 1 | A | B | 是否允許 |

## 五、功能鍵說明
- PF3：返回前頁
- PF14：批次處理傳票

## 六、輸入欄位驗證
1. 必填欄位：
   - 起始採購單號 (DAE01F)
   - 結束採購單號 (DAE01T)
   - 起始傳票 (DAE02F)
   - 結束傳票 (DAE02T)
   - 處理選項 (DOPT)

2. 資料格式：
   - 採購單號：必須為有效採購單號
   - 傳票號碼：必須為有效傳票號碼
   - 處理選項：1(設定採購單)、2(設定採購單及允許)、3(設定採購單及允許檢查)

## 七、錯誤處理
- 錯誤訊息顯示位置：第22行
- 錯誤訊息格式：MSGID(&ERRID &ERRF)
- 錯誤類型：
  - 必填欄位未輸入
  - 資料格式錯誤
  - 採購單號不存在
  - 傳票號碼無效
  - 處理選項無效

## 八、使用說明
1. 查詢條件設定：
   - 輸入起始採購單號
   - 輸入結束採購單號
   - 輸入起始傳票
   - 輸入結束傳票
   - 選擇處理選項

2. 處理選項說明：
   - 選項1：設定採購單
   - 選項2：設定採購單及允許
   - 選項3：設定採購單及允許檢查

3. 功能操作說明：
   - 使用PF3返回前頁
   - 使用PF14進行批次處理傳票

4. 注意事項：
   - 採購單號必須為有效值
   - 傳票範圍必須合理
   - 處理選項必須符合需求
   - 批次處理時需確認資料正確性 