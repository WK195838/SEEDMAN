# 發票年度檔設定顯示檔規格書

## 一、基本資訊
- **顯示檔名稱**：ARA001D
- **程式名稱**：ARA001
- **作者**：A1139 JANE
- **系統**：人事薪資系統
- **子系統**：發票帳款子系統
- **功能說明**：發票年度檔設定(A/U/D/I)
- **建立日期**：1981/03/10
- **修改記錄**：
  - M001：1998/10/26，MICHELLE修改以支援Y2K問題
  - M002：2013/12/17，DAISY新增類型欄位

## 二、顯示檔格式

### 1. 畫面格式總覽
- **畫面大小**：24行 x 80列
- **訊息位置**：第24行
- **資料參照庫**：*LIBL/RERF

### 2. 子檔結構 (SFLSR)

#### 子檔欄位

| 欄位名稱 | 欄位說明 | 類型/長度 | 位置(行,列) | 屬性 |
|---------|---------|----------|------------|------|
| RRN | 記錄編號 | 4S 0 | - | 隱藏(H) |
| DOPT1 | 選項 | 1A | 10,2 | 輸入(B)，有效值：' '、'2'、'4'、'5' |
| AA01 | 廠商代碼 | R | 10,6 | 輸出(O) |
| DAA02 | 發票年月 | 5 0 | 10,13 | 輸出(O)，格式'YY/MM' |
| HAA02 | 發票年月(隱藏) | R | - | 隱藏(H) |
| AA03A | 類型 | 1 | 10,24 | 輸出(O) |
| AA03 | 稅別 | R | 10,30 | 輸出(O) |
| AA04 | 字軌 | R | 10,36 | 輸出(O) |
| AA05 | 起始號碼 | R | 10,41 | 輸出(O) |
| AA06 | 終止碼 | R | 10,54 | 輸出(O) |
| AA07 | 使用號碼 | R | 10,66 | 輸出(O) |

### 3. 子檔控制格式 (SFLCR)
- **子檔大小**：20筆記錄
- **每頁顯示**：10筆記錄
- **功能鍵**：
  - F3：返回主畫面
  - F6：新增
  - 滾動(ROLLUP)：下一頁

#### 顯示欄位

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 1,2 | 程式編號 | 'ARA001' | 固定顯示 |
| 1,26 | 系統標題 | MSGCON(030 URE9999) | 高亮顯示 |
| 1,62 | 日期標籤 | '日期:' | 固定顯示 |
| 1,70 | 系統日期 | $EGMDY (6Y 0) | 輸出(O)，EDTCDE(Y) |
| 2,2 | 畫面編號 | 'SCR001' | 固定顯示 |
| 2,31 | 功能標題 | '發票年度檔設定' | 高亮顯示 |
| 2,62 | 時間標籤 | '時間:' | 固定顯示 |
| 2,70 | 系統時間 | TIME | 格式'  :  :  ' |
| 3,62 | 用戶標籤 | ' USER :' | 固定顯示 |
| 3,70 | 用戶ID | $USER (10A) | 輸出(O) |
| 4,2 | 提示訊息 | '輸入作業年度:' | 固定顯示 |
| 5,5 | 功能說明2 | '2=修改' | 固定顯示 |
| 5,15 | 功能說明4 | '4=刪除' | 固定顯示 |
| 5,25 | 功能說明5 | '5=查詢' | 固定顯示 |
| 7,10 | 列表標題 | '發票年度' | 固定顯示 |
| 8,2 | 欄位標題 | 'A 廠商  (YY/MM)   類型稅別字軌起始號碼   終止碼  使用號碼' | 底線(UL) |

#### 輸入欄位

| 欄位名稱 | 欄位說明 | 位置(行,列) | 長度/類型 | 屬性 | 限制/檢核 |
|---------|---------|------------|----------|------|----------|
| DBGN1 | 廠商代碼 | 9,6 | R | 輸入(B) | - |
| DBGN2 | 發票年月 | 9,13 | 5Y 0 | 輸入(B) | 格式'YY/MM' |

### 4. 底部控制格式 (DSPC1)

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 22,2 | 功能鍵說明 | '功能 F3 =返回主畫面 F6 =新增' | 固定顯示 |
| 24,2 | 訊息顯示 | DMSG (78A) | 高亮顯示(HI) |
| 24,66 | 系統訊息 | MSGCON(014 UPT9999) | 高亮顯示(HI) |

### 5. 詳細資料畫面 (DSPD2)
- **功能鍵**：
  - F3：返回主畫面
  - F12：返回前畫面

#### 顯示欄位

| 位置(行,列) | 欄位說明 | 顯示格式 | 特性 |
|------------|---------|---------|------|
| 1,2 | 程式編號 | 'ARA001' | 固定顯示 |
| 1,26 | 系統標題 | MSGCON(030 URE9999) | 高亮顯示(HI) |
| 1,62 | 日期標籤 | '日期:' | 固定顯示 |
| 1,70 | 系統日期 | $EGMDY (6Y 0) | 輸出(O)，EDTCDE(Y) |
| 2,2 | 畫面編號 | 'SCR002' | 固定顯示 |
| 2,32 | 功能標題 | '發票年度檔設定' | 高亮顯示(HI) |
| 2,62 | 時間標籤 | '時間:' | 固定顯示 |
| 2,70 | 系統時間 | TIME | 格式'  :  :  ' |
| 3,2 | 功能說明 | DFUN (6O) | 高亮(RI) |
| 3,62 | 用戶標籤 | ' USER :' | 固定顯示 |
| 3,70 | 用戶ID | $USER (10A) | 輸出(O) |
| 4,2 | 廠商標籤 | '廠商代碼:' | 固定顯示 |
| 4,20 | 廠商說明 | #B03 | 輸出(O) |
| 6,2 | 發票年月標籤 | '發票年月:' | 固定顯示 |
| 6,20 | 年月格式說明 | '(請輸入年月YY/MM )' | 固定顯示 |
| 8,2 | 類型標籤 | '類型　　:' | 固定顯示 |
| 8,18 | 類型說明 | '(E-電子發票; " "-非電子發票)' | 固定顯示 |
| 10,2 | 稅別標籤 | '稅別　　:' | 固定顯示 |
| 12,2 | 字軌標籤 | '字軌　　:' | 固定顯示 |
| 14,2 | 起始號碼標籤 | '起始號碼:' | 固定顯示 |
| 16,2 | 終止碼標籤 | '終止碼:' | 固定顯示 |
| 18,2 | 使用號碼標籤 | '使用號碼:' | 固定顯示 |
| 22,2 | 功能鍵說明 | '功能 F3 =返回主畫面 F12=返回前畫面' | 固定顯示 |

#### 輸入欄位

| 欄位名稱 | 欄位說明 | 位置(行,列) | 長度/類型 | 屬性 | 限制/檢核 |
|---------|---------|------------|----------|------|----------|
| DAA01 | 廠商代碼 | 4,14 | R | 輸入(B) | 條件控制顯示 |
| DAA02 | 發票年月 | 6,14 | 5Y 0 | 輸入(B) | 格式'YY/MM'，條件控制顯示 |
| DAA03A | 類型 | 8,14 | 1A | 輸入(B) | 有效值：'E'、' '，條件控制顯示 |
| DAA03 | 稅別 | 10,14 | R | 輸入(B) | 條件控制顯示 |
| DAA04 | 字軌 | 12,14 | R | 輸入(B) | 條件控制顯示 |
| DAA05 | 起始號碼 | 14,14 | R | 輸入(B) | 條件控制顯示 |
| DAA06 | 終止碼 | 16,14 | R | 輸入(B) | 自動觸發(MDT)，條件控制顯示 |
| AA07 | 使用號碼 | 18,14 | R | 輸出(O) | 條件控制顯示 |

## 三、功能說明

1. **主要功能**
   - 維護發票年度檔，支援新增、修改、刪除和查詢功能
   - 管理不同廠商和年度的發票資料
   - 追蹤發票號碼的使用情況
   - 區分電子發票和非電子發票類型

2. **操作流程**
   - 主畫面顯示已有的發票年度資料清單
   - 使用者可輸入廠商代碼和發票年月進行篩選
   - 針對清單中的記錄，可選擇修改(2)、刪除(4)或查詢(5)
   - 按F6鍵可新增新的發票年度資料
   - 選擇功能後進入詳細資料畫面

3. **資料檢核**
   - 廠商代碼必須存在
   - 發票年月必須符合格式要求
   - 起始號碼必須小於終止碼
   - 使用號碼必須在起始號碼和終止碼之間
   - 類型必須為有效值('E'或空白)

4. **特殊處理**
   - Y2K問題處理：在1998年10月26日已進行修改，支援2000年前後的日期格式
   - 使用者權限控制：不同欄位根據功能模式有不同的顯示屬性
   - 電子發票支援：2013年12月17日新增類型欄位，區分電子發票和傳統發票

## 四、錯誤處理

系統提供多種錯誤訊息處理，包括：
- UPT 2150：資料輸入錯誤
- UPT 2142：資料格式錯誤
- UPT 2050：資料不存在
- UPT 0010：需要輸入
- UPT 2010：資料已存在
- UPT 2020：資料庫檢核錯誤
- UPT 0040：日期格式錯誤
- UPT 0030：必填欄位
- URE 0038：系統錯誤
- URE 0039：權限錯誤

## 五、相關檔案

1. **參照檔案**
   - RERF：欄位參照檔案

2. **訊息檔案**
   - REMF：系統訊息檔
   - PTMF：程式訊息檔

3. **相關程式**
   - ARA001：發票年度檔設定主程式

## 六、變更記錄

| 變更代碼 | 變更日期 | 變更人員 | 變更內容 | 核准人 |
|---------|---------|---------|---------|-------|
| M002 | 2013/12/17 | DAISY | 新增類型欄位 | - |
| M001 | 1998/10/26 | MICHELLE | 修改支援Y2K問題 | - |
| - | 1981/03/10 | A1139 JANE | 初次建立 | - |

這份顯示檔規格書詳細說明了ARA001D的結構和用途。作為發票年度檔設定的主要介面，此檔案提供了完整的資料維護功能，包括資料的新增、修改、刪除和查詢。透過清晰的畫面規劃和完善的資料檢核機制，確保系統能夠有效地管理各廠商不同年度的發票資料，並追蹤發票使用情況。2013年的更新進一步增強了系統功能，加入對電子發票的支援，使系統更符合現代化業務需求。 