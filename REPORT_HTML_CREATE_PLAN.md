可以，下面這份可以直接存成：

```text
COPILOT_PRESENTATION_BUILD_GUIDE.md
```

然後放到專案資料夾，讓 Copilot 依照這份指南製作或整合 HTML 簡報。

````markdown
# ABAP FI 專案簡報 HTML 製作指南

## 一、製作目標

請製作一份單一 HTML 簡報頁面，用來展示 SAP ABAP FI 專案的期中與期末成果。

整份簡報要清楚分成三個主要部分：

1. 期中專案：FI 三層互動式 WRITE Report
2. 期末專案第一題：Dialog Programming 升級版
3. 期末專案第二題：三個 ALV 整合應用工作台

簡報用途是上台報告時輔助說明，後續會進 SAP 系統實際 Demo，因此簡報不要塞太多程式碼，重點放在：

- 商業邏輯
- 程式架構
- SAP 表格與欄位
- ER Model
- 方法呼叫流程

---

## 二、檔案整合方式

目前資料夾中已有以下參考檔案：

```text
TABLES_WE_USED.html
ER_MODEL.md
MID_CODE_FLOW.html
Q1_CODE_FLOW.html
Q2_CODE_FLOW.html
```
````

請建立新的主檔：

```text
index.html
```

或：

```text
FI_AUDIT_PRESENTATION.html
```

整份簡報請盡量使用單一 HTML 檔案控制三個專案內容。

可以把原本幾個 HTML 檔案中的內容整合進主檔，不需要用 iframe。
CSS 和 JavaScript 可以直接寫在同一個 HTML 中，方便提交與展示。

---

## 三、整體版面設計

請使用清楚、簡潔、正式的簡報風格。

建議結構如下：

```text
index.html

[Top Navbar / Tabs]
- Overview
- 期中專案
- 期末第一題
- 期末第二題
- Demo Checklist

[Overview]
- 專案主軸
- 三個程式的演進關係

[期中專案]
- 商業邏輯與痛點
- SAP 標準操作流程
- 三層程式架構
- 使用資料表與欄位
- ER Model
- Code Flow

[期末第一題]
- Dialog 商業意義
- Screen 100 / Screen 200 功能
- Dialog 呼叫流程
- Code Flow

[期末第二題]
- ALV Workbench 商業意義
- 三個 ALV 互動架構
- 新增資料表與欄位
- ER Model
- Code Flow

[Demo Checklist]
- SAP Demo 講解提示
```

---

## 四、互動設計需求

### 1. 頁面切換

請使用 JavaScript 製作 tab 或 navbar 切換效果。

需求：

- 點擊「期中專案」只顯示期中內容
- 點擊「期末第一題」只顯示 Q1 Dialog 內容
- 點擊「期末第二題」只顯示 Q2 ALV 內容
- 點擊「Overview」顯示總覽
- 點擊「Demo Checklist」顯示 Demo 提示

不要讓三個專案內容混在同一個長頁面中，避免報告時不好控制。

---

### 2. 三個專案的視覺區分

請用不同顏色或標籤區分三個部分：

| 區塊       | 建議主題色 | 標籤                    |
| ---------- | ---------- | ----------------------- |
| 期中專案   | 藍色       | Midterm / WRITE Report  |
| 期末第一題 | 綠色       | Q1 / Dialog Programming |
| 期末第二題 | 紫色或橘色 | Q2 / ALV Workbench      |

每個區塊標題都要明確標示目前是哪個程式，避免上台時混淆。

---

## 五、首頁 Overview 內容

首頁請放一個專案演進圖，表達三個程式的關係：

```text
期中專案
FI 傳票三層互動式報表
        ↓
期末第一題
加入 Dialog 審核與 Dialog 跳報表
        ↓
期末第二題
升級為三個 ALV 聯動的 FI 稽核工作台
```

首頁主軸文字：

```text
本專案以 SAP FI 銷售相關會計傳票為核心，從期中的三層互動式查詢報表開始，
逐步加入 Dialog 審核功能，最後升級為三個 ALV 聯動的財會稽核工作台。
```

---

# 六、期中專案內容製作

## 6.1 期中商業邏輯

請建立一頁「商業邏輯與痛點」。

內容重點：

```text
財會人員若要查詢銷售相關 FI 傳票，通常可以使用 SAP 標準交易碼 FB03。
但 FB03 偏向單張傳票檢視，若要跨多張傳票檢查傳票抬頭、分錄明細、科目名稱、
客戶資料與借貸平衡，就需要在多個畫面間反覆切換。
```

請用卡片或條列呈現痛點：

| 痛點         | 說明                                               |
| ------------ | -------------------------------------------------- |
| 查詢分散     | 標準 FB03 偏向單張傳票查詢，不適合一次檢視多張傳票 |
| 人工比對多   | 科目代碼、科目名稱、客戶資料需要另外確認           |
| 稽核效率低   | 多張傳票查詢時，需要重複進入不同畫面               |
| 異常不易發現 | 借貸方向與金額平衡需要人工檢查                     |

---

## 6.2 SAP 標準操作流程

請建立一頁「沒有程式時的 SAP 操作流程」。

流程如下：

```text
FB03
→ Document List
→ 輸入公司代碼、會計年度、傳票類型 RV
→ 取得傳票清單
→ 點進單張傳票
→ 查看傳票明細行
→ 檢查 Posting Key、SHKZG、DMBTR、HKONT、KUNNR
→ 若要理解科目名稱，需要對應 SKAT
→ 若要理解科目屬性，需要查 SKA1
→ 若要理解客戶資料，需要查 KNA1
```

請用流程圖或 step card 顯示，不要只放純文字。

---

## 6.3 期中程式三層架構

請建立一頁「三層互動式報表架構」。

圖示如下：

```text
Level 1：傳票清單
資料來源：BKPF
顯示公司代碼、傳票號碼、會計年度、傳票類型、文件日期、過帳日期
        ↓ 雙擊傳票

Level 2：傳票明細
資料來源：BSEG + SKAT
顯示行號、總帳科目、科目名稱、借貸方向、本位幣金額、客戶代碼
        ↓ 點擊 HKONT 或 KUNNR

Level 3A：科目主檔
資料來源：SKA1
顯示科目表、總帳科目、資產負債表科目標記、損益表科目類型、科目群組

Level 3B：客戶主檔
資料來源：KNA1
顯示客戶代碼、客戶名稱、城市、國家、地址、電話
```

---

## 6.4 期中使用資料表與欄位

請整理成表格，所有 SAP 德文縮寫都要加中文說明。

### BKPF：會計傳票抬頭表

| 欄位  | 中文說明     | 用途                 |
| ----- | ------------ | -------------------- |
| BUKRS | 公司代碼     | 查詢條件、Join Key   |
| BELNR | 會計傳票號碼 | 傳票主要識別欄位     |
| GJAHR | 會計年度     | 查詢條件、Join Key   |
| BLART | 傳票類型     | 篩選 RV 銷售相關傳票 |
| BLDAT | 文件日期     | 第一層顯示           |
| BUDAT | 過帳日期     | 第一層顯示           |

### BSEG：會計傳票明細表

| 欄位  | 中文說明     | 用途                   |
| ----- | ------------ | ---------------------- |
| BUKRS | 公司代碼     | 與 BKPF 關聯           |
| BELNR | 會計傳票號碼 | 與 BKPF 關聯           |
| GJAHR | 會計年度     | 與 BKPF 關聯           |
| BUZEI | 傳票明細行號 | 第二層顯示             |
| HKONT | 總帳科目     | 科目下鑽 Key           |
| KUNNR | 客戶代碼     | 客戶下鑽 Key           |
| SHKZG | 借貸指標     | S = 借方，H = 貸方     |
| DMBTR | 本位幣金額   | 顯示金額與計算借貸平衡 |
| MENGE | 數量         | 第二層輔助顯示         |
| MEINS | 單位         | 第二層輔助顯示         |
| MATNR | 物料代碼     | 第二層輔助顯示         |

### SKAT：總帳科目文字表

| 欄位  | 中文說明     | 用途               |
| ----- | ------------ | ------------------ |
| SPRAS | 語言代碼     | 避免多語系文字重複 |
| KTOPL | 科目表       | 篩選 GL00          |
| SAKNR | 總帳科目號碼 | 對應 BSEG-HKONT    |
| TXT20 | 科目短文字   | 顯示科目名稱       |

### SKA1：總帳科目主檔表

| 欄位  | 中文說明           | 用途                     |
| ----- | ------------------ | ------------------------ |
| KTOPL | 科目表             | 第三層顯示               |
| SAKNR | 總帳科目號碼       | 對應 BSEG-HKONT          |
| XBILK | 資產負債表科目標記 | 判斷是否為資產負債表科目 |
| GVTYP | 損益表科目類型     | 顯示科目分類             |
| KTOKS | 科目群組           | 顯示科目群組             |

### KNA1：客戶主檔一般資料表

| 欄位  | 中文說明 | 用途            |
| ----- | -------- | --------------- |
| KUNNR | 客戶代碼 | 對應 BSEG-KUNNR |
| NAME1 | 客戶名稱 | 第三層顯示      |
| LAND1 | 國家代碼 | 第三層顯示      |
| ORT01 | 城市     | 第三層顯示      |
| STRAS | 街道地址 | 第三層顯示      |
| TELF1 | 電話     | 第三層顯示      |

---

## 6.5 期中 ER Model

不要使用 Mermaid。

請用 HTML card / table / SVG 方式畫出以下關係：

```text
BKPF
  ↓ BUKRS + BELNR + GJAHR
BSEG
  ├─ HKONT → SKAT
  ├─ HKONT → SKA1
  └─ KUNNR → KNA1
```

請在圖旁邊放關係說明：

| 關係        | 說明                                  |
| ----------- | ------------------------------------- |
| BKPF → BSEG | 一張傳票抬頭可以有多筆傳票明細        |
| BSEG → SKAT | 用 HKONT 對應 SAKNR，取得科目文字     |
| BSEG → SKA1 | 用 HKONT 對應 SAKNR，取得科目主檔屬性 |
| BSEG → KNA1 | 用 KUNNR 對應客戶主檔                 |

---

## 6.6 期中 Code Flow

請參考 `MID_CODE_FLOW.html`，整合以下流程：

```text
START-OF-SELECTION
→ CREATE OBJECT go_report
→ go_report->start()
→ get_level1()
→ display_level1()

AT LINE-SELECTION
→ handle_interaction()
→ get_level2()
→ display_level2()

第二層點 HKONT
→ get_level3_skat()
→ display_level3_skat()

第二層點 KUNNR
→ get_level3_kna1()
→ display_level3_kna1()
```

可以用流程卡片呈現。

---

# 七、期末第一題內容製作

## 7.1 商業邏輯

請建立一頁「Dialog 升級的商業意義」。

內容重點：

```text
期中報表主要提供查詢與下鑽能力。
期末第一題在原本 FI 傳票查詢流程中加入 Dialog Screen，
讓財會或稽核人員可以針對指定傳票進行審核註記、狀態確認，
並透過另一個 Screen 輸出審核摘要報表。
```

請強調：

```text
期中：查詢
期末第一題：查詢 + 審核互動 + 摘要報表
```

---

## 7.2 Screen 100 功能

請建立卡片：

```text
Screen 0100：傳票審核畫面
```

內容：

| 功能             | 說明                            |
| ---------------- | ------------------------------- |
| 顯示被選取的傳票 | 從第二層明細進入指定傳票        |
| 輸入審核結果     | 例如 Approved / Hold / Rejected |
| 儲存本次審核資料 | 以 internal table 模擬審核紀錄  |
| 清除輸入         | 重新填寫審核資訊                |
| 查看摘要         | 呼叫 Screen 0200                |

---

## 7.3 Screen 200 功能

請建立卡片：

```text
Screen 0200：審核摘要報表
```

內容：

| 技術                     | 說明                   |
| ------------------------ | ---------------------- |
| SUPPRESS DIALOG          | 不顯示一般 Dynpro 畫面 |
| LEAVE TO LIST-PROCESSING | 切換到 List 輸出模式   |
| display_review_summary() | 輸出審核摘要報表       |

商業意義：

```text
使用者完成審核後，可以立即查看本次審核結果摘要，
不需要離開流程再重新執行另一支報表。
```

---

## 7.4 Dialog 呼叫流程圖

請畫成：

```text
Report Program
        ↓ AT LINE-SELECTION
CALL SCREEN 0100
        ↓ 使用者按 VIEW / SUMM
CALL SCREEN 0200
        ↓ PBO
SUPPRESS DIALOG
        ↓
LEAVE TO LIST-PROCESSING
        ↓
display_review_summary()
```

---

## 7.5 Q1 Code Flow

請參考 `Q1_CODE_FLOW.html`，整合以下流程：

```text
START-OF-SELECTION
→ go_report->start()
→ get_level1()
→ display_level1()

AT LINE-SELECTION
→ handle_interaction()

第二層雙擊審核行
→ prepare_review_dialog()
→ CALL SCREEN 0100

Screen 0100
→ user_command_0100
→ save_review()
→ clear_review_input()
→ CALL SCREEN 0200
→ LEAVE TO SCREEN 0

Screen 0200
→ status_0200
→ SUPPRESS DIALOG
→ LEAVE TO LIST-PROCESSING
→ display_review_summary()
```

---

# 八、期末第二題內容製作

## 8.1 商業邏輯

請建立一頁「ALV Workbench 商業意義」。

內容重點：

```text
期末第二題將期中的 FI 三層互動式報表升級為 ALV 工作台。
使用者可以在同一個畫面中查看傳票清單、傳票明細，以及科目或客戶主檔檢核資訊，
不需要像 WRITE Report 一樣逐層切換。
```

請強調：

```text
期中：WRITE Report 下鑽
期末第二題：三個 ALV 聯動的稽核工作台
```

---

## 8.2 三個 ALV 互動架構

請畫出以下圖：

```text
ALV1：傳票清單
資料來源：BKPF + BSEG 彙總
顯示傳票號碼、日期、傳票類型、借方合計、貸方合計、風險狀態
        ↓ 點選傳票

ALV2：傳票明細
資料來源：BSEG + SKAT
顯示行號、科目、科目名稱、借貸方向、金額、客戶代碼
        ↓ 點選 HKONT 或 KUNNR

ALV3：主檔 / 檢核資訊
資料來源：SKA1 / KNA1 / KNB1
顯示科目主檔、客戶一般資料、客戶公司代碼資料
```

---

## 8.3 Q2 使用資料表與欄位

期末第二題沿用期中主要表：

```text
BKPF
BSEG
SKAT
SKA1
KNA1
```

並新增：

```text
KNB1
```

### KNB1：客戶公司代碼層級資料表

請加入以下欄位說明：

| 欄位  | 中文說明 | 用途                                 |
| ----- | -------- | ------------------------------------ |
| KUNNR | 客戶代碼 | 對應 KNA1-KUNNR                      |
| BUKRS | 公司代碼 | 表示該客戶在特定公司代碼下的財務設定 |
| AKONT | 統馭科目 | 檢查客戶應收帳款對應的統馭科目       |
| ZTERM | 付款條件 | 查看客戶付款條件                     |
| SPERR | 凍結標記 | 檢查客戶是否在該公司代碼下被凍結     |

請在文字中說明：

```text
KNB1 比 KNA1 更接近財會稽核情境。
KNA1 是客戶的一般主檔，例如名稱、地址、國家；
KNB1 則是客戶在特定公司代碼下的財務設定，例如統馭科目、付款條件與凍結狀態。
```

---

## 8.4 Q2 ER Model

不要使用 Mermaid。

請在期中 ER Model 基礎上加入 KNB1：

```text
BKPF
  ↓ BUKRS + BELNR + GJAHR
BSEG
  ├─ HKONT → SKAT
  ├─ HKONT → SKA1
  └─ KUNNR → KNA1
                ↓ KUNNR + BUKRS
              KNB1
```

關係說明：

| 關係               | 說明                                            |
| ------------------ | ----------------------------------------------- |
| BKPF → BSEG        | 一張傳票抬頭對應多筆傳票明細                    |
| BSEG → SKAT        | 用 HKONT 對應科目文字                           |
| BSEG → SKA1        | 用 HKONT 對應科目主檔                           |
| BSEG → KNA1        | 用 KUNNR 對應客戶一般資料                       |
| KNA1 → KNB1        | 一個客戶可以在不同公司代碼下有不同財務設定      |
| BSEG / BKPF → KNB1 | 用 KUNNR + BUKRS 查客戶在該公司代碼下的財務設定 |

---

## 8.5 Q2 Code Flow

請參考 `Q2_CODE_FLOW.html`，整合以下流程：

```text
START-OF-SELECTION
→ lcl_app->start()
→ load_documents()
→ calculate_document_totals()
→ CALL SCREEN 0100
→ init_screen()
→ display_alvs()

ALV1 點擊傳票
→ handle_doc_row()
→ load_items()
→ refresh_item_alv()
→ refresh_check_alv()

ALV2 點 HKONT
→ handle_item_row()
→ load_account_checks()
→ refresh_check_alv()

ALV2 點 KUNNR
→ handle_item_row()
→ load_customer_checks()
→ refresh_check_alv()

功能鍵 RISK
→ filter_risk_only()
→ refresh_doc_alv()
→ clear_items_and_checks()

功能鍵 ALL
→ show_all_documents()
→ refresh_doc_alv()
→ clear_items_and_checks()

功能鍵 SUMM
→ show_risk_summary()

BACK / EXIT
→ LEAVE TO SCREEN 0
→ LEAVE PROGRAM
```

---

# 九、Demo Checklist 頁面

請在最後建立一個 Demo Checklist，方便上台前快速確認。

## 期中 Demo

```text
1. 輸入公司代碼與年度
2. 顯示第一層傳票清單
3. 雙擊某張傳票
4. 顯示第二層傳票明細
5. 點 HKONT 顯示科目主檔
6. 返回後點 KUNNR 顯示客戶主檔
7. 說明借貸方向與金額檢查
```

## 期末第一題 Demo

```text
1. 執行期中式三層報表
2. 在第二層選擇審核功能
3. CALL SCREEN 0100
4. 輸入審核結果
5. SAVE 儲存
6. VIEW / SUMM 進入 Screen 0200
7. 顯示審核摘要報表
8. 說明 SUPPRESS DIALOG 與 LEAVE TO LIST-PROCESSING
```

## 期末第二題 Demo

```text
1. 執行 ALV 工作台
2. ALV1 顯示傳票清單
3. 點選某張傳票
4. ALV2 顯示該傳票明細
5. 點 HKONT
6. ALV3 顯示科目檢核資訊
7. 點 KUNNR
8. ALV3 顯示客戶檢核資訊
9. 展示 RISK / ALL / SUMM 功能
```

---

# 十、視覺與排版要求

## 10.1 基本風格

請使用：

```text
乾淨、正式、簡報風格、適合課堂報告
```

避免：

```text
太花俏
太多動畫
大量程式碼
密密麻麻的文字
```

---

## 10.2 建議元件

請使用以下元件：

| 元件             | 用途                             |
| ---------------- | -------------------------------- |
| card             | 顯示表格、Screen、ALV、痛點      |
| flow diagram     | 顯示方法呼叫流程                 |
| table            | 顯示 SAP 欄位說明                |
| badge            | 標示 Level 1 / Level 2 / Level 3 |
| tab              | 切換三個專案內容                 |
| SVG / HTML boxes | 畫 ER Model                      |

---

## 10.3 ER Model 不要使用 Mermaid

請不要使用 Mermaid。

請使用以下方式之一：

1. HTML card + CSS arrow
2. SVG box + line
3. HTML table-like box + absolute positioned line

重點是圖要清楚，不一定要完全符合專業 ERD 格式。

---

## 10.4 欄位說明格式

所有 SAP 欄位都要使用以下格式：

```text
欄位代碼 + 中文名稱 + 專案用途
```

例如：

```text
BUKRS：公司代碼，用來指定查詢公司與 Join 傳票資料。
BELNR：會計傳票號碼，用來識別單張 FI 傳票。
GJAHR：會計年度，用來定位年度內的傳票資料。
SHKZG：借貸指標，S 代表借方，H 代表貸方。
DMBTR：本位幣金額，用來顯示與加總分錄金額。
```

---

# 十一、不要做的事情

請避免以下修改：

```text
不要改動 ABAP 程式碼
不要新增與專案無關的內容
不要使用 Mermaid
不要把期中、Q1、Q2 三個區塊混在一起
不要塞大量原始碼
不要把 SAP 欄位只寫德文縮寫而不解釋
不要做太複雜的動畫
不要把簡報拆成多個必須手動切換的 HTML 檔案
```

---

# 十二、預期成果

完成後應該有一份主檔：

```text
FI_AUDIT_PRESENTATION.html
```

或：

```text
index.html
```

打開後可以：

1. 透過 navbar / tabs 切換 Overview、期中、Q1、Q2、Demo Checklist。
2. 清楚說明 FI 專案從期中到期末的演進。
3. 看懂每個程式的商業用途。
4. 看懂三層報表、Dialog、三個 ALV 的互動架構。
5. 看懂使用到的 SAP 表格與欄位。
6. 看懂 ER Model 與資料表關聯。
7. 上台時可以配合 SAP Demo 流暢講解。

---

# 十三、簡報核心敘事

整份簡報請圍繞這個主軸：

```text
我們的專案不是單純查表，
而是把 SAP FI 銷售相關會計傳票的查詢、明細展開、科目與客戶檢核，
逐步整合成一個更有效率的財會稽核輔助工具。
```

三個階段分別是：

```text
期中：用 WRITE Report 完成三層下鑽查詢
Q1：加入 Dialog，讓查詢流程具備審核互動
Q2：升級成 ALV Workbench，讓傳票、明細、檢核資訊在同一畫面聯動
```

```

```
