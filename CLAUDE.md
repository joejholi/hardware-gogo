# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 新對話必做

**每次新對話開始時，必須用 Read 工具讀取所有 memory 檔案，讀完才能開始回答或討論。**

**步驟：**
1. 先讀 memory 資料夾的 `MEMORY.md`（索引）
2. 根據索引，用 Read 工具逐一讀取所有列出的 `.md` 檔案
3. **不要用 Glob 搜尋**，直接用已知路徑 Read

## Workflow

1. **Plan First**：非簡單任務（3+ 步驟）進 plan mode，出問題立刻停下來重新規劃，不硬推
2. **Subagent 節制**：簡單搜尋直接用工具，子代理只用於多步驟或獨立上下文的任務
3. **Self-Improvement**：被用戶糾正後更新 memory 記錄，寫規則防止重犯
4. **Verify Before Done**：任務完成前必須證明它能動，不要假設完成
5. **Investigate Before Answering**：回答前**必須先開檔案確認**，不准憑印象回答
6. **Commit to Direction**：選定方向就執行，不反覆比較，做不通再換
7. **Autonomous Bug Fixing**：收到 bug 就直接修，不問用戶怎麼修
8. **CLAUDE.md 同步**：凡改變架構、慣例、格式的修改，完成後必須同步更新此檔案

## Task Management

1. Write plan → 2. Track progress → 3. Mark complete → 4. Update memory after corrections

## Core Principles

- **Simplicity First**：最簡單的改法，影響最少的程式碼
- **No Laziness**：找根本原因，不打暫時補丁
- **Minimal Impact**：只改必要的部分，不動範圍外已正常運作的程式碼
- **Clean Up**：暫存檔案用完刪除
- **Step Back**：非簡單修改前先停下來想——有沒有更乾淨的做法？感覺在打補丁就重新想

## 測試

- 改完後直接用瀏覽器開 HTML 檔案測試（純靜態網站，無需伺服器）
- 測試項目：響應式（手機/平板/桌面）、連結是否正確、圖片是否顯示

## 防錯規則

- **寫 CSS/HTML 前先查現有 class**：先確認既有 class 的行為再動手
- **debug 先診斷再改**：用 Console 測試確認根本原因，不猜測式修改
- **replace_all 後逐一檢查**：批次取代後檢查每個替換點是否合理
- **修改前先讀檔**：不要憑記憶改程式碼，先看過現在的內容
- **圖片路徑注意中文檔名**：部分圖片為中文檔名，注意編碼問題
- **修改要檢查完整影響範圍**：改完後從頭模擬一遍流程，確認「原本正常的東西」沒壞掉

## 溝通原則

- **淺顯易懂**：避免術語，用白話、比喻解釋，讓非工程師也看得懂
- **先討論再實作**：涉及版面配置、文案調整，必須先確認再動手
- **不懂就問**：對用戶的需求有任何不確定、不明白的地方，先用問答釐清，不要猜測後直接動手，避免做白工
- **請用繁體中文回應**

## 修改範圍控制

- **嚴守修改範圍**：討論 A 就只改 A，不擴大去動已定好的 B 和 C
- **版面/排版只改要求的部分**：不確定某個值是否有問題 → 先問，不要自己「修正」

---

## 專案說明

### 五金GOGO購 品牌官網

- **性質**：品牌形象網站（非購物網站），導流至 iOPEN 賣場購買
- **技術**：純 HTML + CSS + JS，無框架、無 build step
- **部署**：GitHub Pages（免費靜態托管）
- **開發檔案**：`test.html`

### 品牌背景

- 台中在地五金工具商，民國 69 年（1980）起經營，超過 45 年
- 代理日本、歐洲超過 30 個專業手工具品牌
- 已有 ERP 系統（HOLI_ERP.html）管理銷售數據

### 雙軌策略（重要）

兩條線是不同的生意模式，不是同一套定價：

| | 后里機器五金行 | 五金GOGO購 |
|---|---|---|
| 客戶 | 長期 B2B 配合客戶 | 網路新客戶 |
| 服務 | 送貨、月結對帳 | 平台出貨 |
| 票期 | 3~4 個月 | 無（收現金） |
| 定價 | 另議（含服務成本） | 明碼標價 |
| 發票 | 后里機器五金行 | 后里機器五金行（同一公司，可內部區分） |

- **兩個名字絕對不能連結在一起**：B2B 老客戶若看到線上標價，會因定價邏輯不同而產生誤解
- **禁止事項**：Schema 的 `alternateName`、頁面文案、任何可見或不可見的地方，都不能出現「后里機器五金行即五金GOGO購」這樣的連結

### 導流策略

- **iOPEN**（主要導流，無手續費）：https://mall.iopenmall.tw/013114/
- **Yahoo拍賣**（17年老店）：https://tw.bid.yahoo.com/booth/Y6932867058
- **蝦皮**（手續費 14.5%，減少依賴）：https://shopee.tw/lan7026

### 聯絡資訊

- 客服專線：0983-218-658
- LINE：搜尋 0983-218-658
- 地區：台中

### 設計風格

- **定位**：品牌形象官網（非購物網站），不突顯電商平台
- **主色**：古銅棕 `#995a2f`
- **背景**：白底，Hero 下方有深色到米白漸層過渡
- **文字**：Hero 區域用 `#d9d9d9`（灰白，不刺眼）
- **導航列**：Logo + 「五金GOGO購」斜體粗字，hover 時古銅棕底色
- **按鈕**：「探索我們的品牌」（古銅棕底）+「線上選購」（透明框），不突顯 iOPEN
- **不顯示價格**：品牌官網不放價格
- **無數據列**：移除 45+、30+ 等數據展示（不適合品牌官網）
- **風格**：品牌質感、專業但不冰冷、去除 AI 感
- **響應式**：手機版優先
- **SEO 關鍵字**：KEIBA台中、BONDHUS台灣、專業工具台中、五金工具老店
- **GitHub Pages**：https://joejholi.github.io/hardware-gogo/
- **GitHub Repo**：https://github.com/joejholi/hardware-gogo

### 文案語氣

- 像「有經驗的老闆認真跟你講」，不是朋友閒聊也不是念公司簡介
- 不要太口語，但也不要 AI 感
- 要有店家的分寸，顯得有點專業
- 不使用 emoji

---

## 頁面結構

### 1. 首頁 Hero
- 全幅背景圖輪播（measuring tools.jpg + 新-3~新-7 品牌形象圖）
- 標語：「職人的工具箱 從這裡開始」
- 副標籤：SINCE 1980 ─ 台中在地老店
- 按鈕：「探索我們的品牌」+「線上選購」

### 2. 熱銷商品（橫向滾動）
- 10 個商品卡片，有圖片無價格
- 從 iOPEN 抓商品圖片，點擊導向 iOPEN 商品頁

### 3. 代理品牌（左右分欄）
- 左側品牌列表（目前 6 個，待擴充至 29 個）
- 右側預設顯示品牌總覽（品牌名 + 簡介 + MORE 連結）
- 點品牌切換為該品牌商品展示
- 點「代理品牌」標題可回到品牌總覽
- BONDHUS、EIGHT 商品資料待補

### 4. 關於我們
- 左文右圖（圖用 `hand tools.JPG`）
- 下方三個品牌價值（專業、熱忱、信任）

### 5. 聯絡我們
- 電話、LINE、Google 地圖導航連結
- 地址：台中市后里區三豐路三段1078號

---

## 品牌獨立頁面

### 已完成
| 頁面 | 商品卡數 | 說明 |
|------|---------|------|
| `keiba.html` | 多張 | KEIBA 馬牌，含系列標籤分組 |
| `bondhus.html` | 42張 | BONDHUS 六角板手，含型號 |
| `wera.html` | 35張 | WERA 起子，5大系列 |

### 品牌頁統一規範
1. 導覽列順序：代理品牌 → 熱銷商品 → 聯絡我們 → 關於我們 → 線上選購
2. 每頁都要有 meta description（含品牌名、產品類型、關鍵字）
3. 商品卡片必須有圖片，不用文字卡片
4. 品名格式：品名 + 規格 + 型號（型號放最後），例如「白金 球型 六角板手 英制 12支組 16936」
5. 品名加空白分隔，方便手機斷行閱讀
6. 首頁面板要加分類標籤（brand-series-tags）
7. 首頁 MORE 連結指向對應 .html 檔案
8. 完成後更新 sitemap.xml
9. iOPEN 分類頁用 `prod_display_num=50` 參數才能看到全部商品

### 待做品牌
3.PEAKS、WIHA、TOP 等（順序待決定）

---

## 關於我們文案（已確認）

1. 從民國69年起，我們專注在手工具這個領域已經超過45年。
2. 目前代理日本、德國、美國超過30個專業工具品牌，從鉗子、六角板手到量測儀器，每個品牌都是長期配合、品質確認過的。
3. 品牌舉例：KEIBA 鉗子 — 專業技師指定、BONDHUS 六角板手 — 科技業設備維護、WERA 起子組 — 人體工學設計
4. 協助客人選工具，歡迎聯繫

## 品牌價值（已確認）

- **專業**：45年銷售經驗，協助挑選最適合的工具
- **熱忱**：專業技師或DIY新手都歡迎詢問
- **信任**：全部正品公司貨，快速出貨、貼心服務

---

## 圖片資源

| 圖片 | 用途 |
|------|------|
| `shoplogo-1.png` | 導航列 Logo（裁掉上下白邊版本） |
| `measuring tools.jpg` | Hero 輪播第一張（工具照片） |
| 新-3 ~ 新-7 | Hero 輪播（品牌形象圖：EIGHT、KEIBA、WIHA、WERA、TOP） |
| `hand tools.JPG` | 關於我們配圖 |

---

## 代理品牌（29 個）

| 品牌 | 國家 | iOPEN 連結 |
|------|------|-----------|
| KEIBA 馬牌 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=67625 |
| 3.PEAKS 小山 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000034370 |
| EIGHT 六角棒 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=67704 |
| BONDHUS | 🇺🇸 美國 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=70259 |
| WERA | 🇩🇪 德國 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=70643 |
| WIHA | 🇩🇪 德國 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=72402 |
| Mitutoyo 三豐 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000018099 |
| KANON 中村製作所 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=67875 |
| KURITA 栗田製作所 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000019432 |
| MCC 松阪鉄工所 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000020226 |
| TOP トップ工業 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=67708 |
| NETSUREN | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000033182 |
| LOBSTER 蝦牌 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=67938 |
| LIGHT | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=69961 |
| SUPER TOOL | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=67903 |
| ANEX | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=70262 |
| H.T.D 早坂 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000035679 |
| SCHRODER | 🇩🇪 德國 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=73834 |
| IKEDA | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=73833 |
| PFERD | 🇩🇪 德國 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000034808 |
| IRWIN | 🇺🇸 美國 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000026784 |
| TAJIMA | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000021182 |
| TSUNODA | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=71570 |
| TSUBOSAN 壺三 | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000021932 |
| TOZE | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=69728 |
| INHAND | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000020430 |
| KDS | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000021183 |
| WISE | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000042062 |
| SUNFLAG | 🇯🇵 日本 | https://mall.iopenmall.tw/013114/index.php?action=product_sort&prod_sort_ou=1000042950 |

---

## 資料檔案

| 檔案 | 說明 |
|------|------|
| `sales_history.csv` | 完整銷售記錄（158,022筆，2001-2026） |
| `customers.csv` | 客戶資料（277筆） |
| `products.csv` | 產品資料（14,569筆） |
| `purchase_history.csv` | 進貨記錄（46,729筆） |
| `02S.csv` | 蝦皮出貨明細 |

## 熱銷商品邏輯

- 來源：`sales_history.csv`
- 篩選：客戶編號 = 02S（蝦皮）
- 時間：近 12 個月
- 排序：總銷售金額由高到低，取前 20 名
- 顯示：品名（不顯示價格，品牌官網不放價格）

## Schema 結構化資料現況

首頁（index.html）：`HardwareStore` 類型，含 29 個代理品牌、產品類別、郵遞區號、areaServed。
品牌頁（keiba / bondhus / wera）：`Brand` 類型，seller 為 `HardwareStore`，含國際電話格式與郵遞區號。
**`alternateName` 中不包含「后里機器五金行」**（見雙軌策略說明）。

## 重要提醒

- iOPEN 目前無手續費，是優先導流目標
- 蝦皮手續費 14.5%（2026/01/01起），盡量導流到 iOPEN
- 系統進價資料有部分錯誤，勿直接用於毛利計算
- **「后里機器五金行」與「五金GOGO購」永遠不能在官網任何地方被連結**（含 Schema、文案、meta）
