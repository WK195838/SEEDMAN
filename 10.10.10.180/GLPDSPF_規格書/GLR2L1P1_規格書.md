# GLR2L1P1 報表規格書

## 一、基本資訊
- 檔案名稱：GLR2L1P1
- 檔案類型：報表格式檔
- 來源目錄：10.10.10.180/QDDSSRC_GLPLIB
- 程式說明：部門費用分析明細報表格式
- 系統：會計系統
- 子系統：總帳系統
- 作者：A1087 JOYCE
- 建立日期：1992.12.18
- 更新日期：
- 備註：部門費用分析明細報表格式

## 二、報表結構
1. 參考檔案：
   - GLRF

2. 報表格式：
   - 表頭 (PH1)
   - 明細資料 (PD1)
   - 合計資料 (PT1)
   - 簽名欄位 (PNAME1, PNAME2)

## 三、報表佈局

### 表頭 (PH1)
```
[公司名稱]                                    [系統日期]
部門費用分析

[部門代號]

日期: [  /  /  ]    頁次: [    ]
時間: [  :  :  ]    <GLR2L1P>

===========================================================
部門    本期金額    上期金額    差異比率
===========================================================
```

### 明細資料 (PD1)
```
[部門代號]  ([金額])  ([人數])  ([金額])  ([人數])  ([金額])  ([人數])
```

### 合計資料 (PT1)
```
===========================================================
合計  ([金額])  100.00  ([金額])  100.00  ([金額])  100.00
===========================================================
[簽名欄位1]
[簽名欄位2]
```

## 四、報表欄位規格

### 表頭欄位
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| P#B16 | 50 | 32 | A | R | 公司名稱 |
| PDA01 | 62 | 8 | A | O | 系統日期 |
| P0303 | 50 | 34 | A | O | 部門代號 |
| DAK12 | 65 | 6 | 0 | R | 會計日期 |
| PDATE | 109 | 6 | 0 | O | 列印日期 |
| PAGNBR | 126 | 4 | Z | O | 頁次 |
| TIME | 109 | 8 | T | O | 時間 |

### 明細資料欄位 (PD1)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| P0402 | 4 | 34 | A | O | 部門代號 |
| P0403 | 40 | 13 | 2 | O | 本期金額1 |
| P03B | 60 | 5 | 2 | O | 本期人數1 |
| P0404 | 72 | 13 | 2 | O | 本期金額2 |
| P04B | 92 | 5 | 2 | O | 本期人數2 |
| P043 | 103 | 13 | 2 | O | 本期金額3 |
| P43B | 123 | 5 | 2 | O | 本期人數3 |

### 合計資料欄位 (PT1)
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| T0403 | 39 | 13 | 2 | O | 合計金額1 |
| T0404 | 71 | 13 | 2 | O | 合計金額2 |
| T043 | 102 | 13 | 2 | O | 合計金額3 |

### 簽名欄位
| 欄位名稱 | 位置 | 長度 | 型態 | 屬性 | 說明 |
|---------|------|------|------|------|------|
| PNAME1 | 1 | 132 | A | O | 簽名欄位1 |
| PNAME2 | 1 | 132 | A | O | 簽名欄位2 |

## 五、報表標題內容
1. 公司名稱
2. 系統日期
3. 部門代號
4. 會計日期
5. 列印日期
6. 頁次
7. 列印時間

## 六、報表欄位說明
1. 部門代號：顯示部門代號
2. 本期金額：顯示本期金額和人數
3. 上期金額：顯示上期金額和人數
4. 差異比率：顯示差異比率和人數
5. 合計資料：顯示各項金額的合計和比率
6. 簽名欄位：提供簽核使用

## 七、使用說明
1. 報表用途：
   - 顯示部門費用分析明細
   - 提供部門費用分析資訊
   - 用於部門費用分析作業

2. 報表內容：
   - 顯示指定部門的費用明細
   - 包含表頭和合計資訊
   - 提供簽核欄位

3. 注意事項：
   - 報表依部門代號排序
   - 金額欄位使用千分位格式
   - 合計資料顯示在報表最後
   - 比率欄位固定顯示 100.00 