# microbiome-report

個人化腸生態健康管理報告模板（Precision Nutrition Report）。

此專案為 **中天生物科技** 腸道微生態健康評估報告的靜態 HTML 模板，使用 Gulp + EJS 建構，產出可列印的 A4 格式 PDF 報告。

---

## 技術棧

| 類別 | 技術 |
|------|------|
| 模板引擎 | EJS |
| 樣式 | SCSS / Sass + Bootstrap 5.1.3 |
| 字型 | Google Fonts（Noto Sans TC、Passion One）、Font Awesome Pro 5.10.0 |
| JavaScript | jQuery 3.6.0 + Babel（@babel/preset-env）|
| 建構工具 | Gulp 4 + BrowserSync |
| CSS 後處理 | PostCSS + Autoprefixer |

---

## 專案結構

```
microbiome-report/
├── app/                        # 原始碼
│   ├── index.html              # 主入口（front-matter 指定 layout）
│   ├── layout.ejs              # 全域 HTML 框架，依序 include 所有頁面
│   └── assets/
│       ├── ejs/                # 共用元件（logo、footer、title-logo）
│       ├── views/              # 報告頁面（p1.ejs ~ p37.ejs）
│       ├── style/              # SCSS 來源
│       │   ├── style.scss      # 主入口，匯入所有分檔
│       │   ├── helpers/        # 變數、mixin、reset、base
│       │   ├── layout/         # 頁面容器（A4 page）
│       │   ├── components/     # 共用元件（table、title）
│       │   └── pages/          # 各頁面專屬樣式（_p1.scss ~ _p37.scss）
│       ├── js/
│       │   └── all.js          # 主要 JavaScript
│       └── images/             # 報告所需圖片資源
│           └── images_v2/      # V2 版本圖片資源（開發中）
├── gulpfile.js/
│   ├── index.js                # Gulp 任務定義
│   └── envOptions.js           # 來源 / 輸出路徑設定
├── dist/                       # 建構輸出（git 忽略）
├── package.json
└── depoly.sh                   # 手動部署腳本（gh-pages）
```

---

## 報告頁面結構（共 37 頁）

| 頁面 | 章節 | 內容 |
|------|------|------|
| p1 | 封面 | 個人化腸生態健康管理 / Precision Nutrition |
| p2 | 前言 | 中天生技介紹、獨家技術說明 |
| p3 | 客戶訊息 | 個人資料、檢測資料、致顧客的話 |
| p4 | 目錄 | 五大章節目錄 |
| p5 | 章節分隔 | 腸道健康分析 |
| p6 | 總覽摘要 | 六大核心指數 + 身體功能評估摘要 |
| p7 | 1.1 | 腸道分析總覽 |
| p8 | 1.2 | 腸道健康指引 |
| p9 | 1.3 | 菌相數量分布圖（華人資料庫比對）|
| p10 | 1.4 | 健康分析指標（F/B 比值、B/E 比值）|
| p11 | 1.5 | 短鏈脂肪酸合成能力 |
| p12 | 1.6 | 腸型分析 |
| p13 | 1.7 | 腸道菌相總覽（關鍵好菌 / 壞菌）|
| p14 | 章節分隔 | 六大核心指數 |
| p15 | 2. | 六大核心指數（指數說明）|
| p16 | 2. | 六大核心指數（檢測結果）|
| p17 | 章節分隔 | 血液生化檢驗 |
| p18 | 3. | 血液生化檢驗（菌相分析 v.s. 生化指數）|
| p19 | 章節分隔 | 身體功能評估 |
| p20 | 4.1 | 腦功能健康指數 |
| p21 | 4.2 | 心血管功能健康指數 |
| p22 | 4.3 | 肺功能健康指數 |
| p23 | 4.4 | 肝功能健康指數 |
| p24 | 4.5 | 腎功能健康指數 |
| p25 | 4.6 | 胃功能健康指數 |
| p26 | 4.7 | 腸功能健康指數 |
| p27 | 4.8 | 免疫功能健康指數 |
| p28 | 4.9 | 肥胖健康指數 |
| p29 | 4.10 | 代謝功能健康指數 |
| p30 | 章節分隔 | 附錄 |
| p31 | 5.1 | 腸道微生態 |
| p32 | 5.2 | 如何檢測您的腸生態 |
| p33 | 5.3 | 血液生化檢驗臨床意義 |
| p34–p36 | 5.4 | 引用文獻 |
| p37 | 附錄 | 免責聲明暨評估說明 |

---

## 快速開始

### 安裝依賴

```bash
npm install
```

### 開發模式

啟動 BrowserSync 本地伺服器（`http://localhost:8080`），監聽 EJS / SCSS / JS 變更並自動重載：

```bash
npx gulp
```

### 正式建構

輸出到 `dist/` 目錄（env=prod）：

```bash
npm run build
# 等同於 npx gulp build --env prod
```

### 清除建構輸出

```bash
npx gulp clean
```

### 部署到 GitHub Pages

```bash
npx gulp deploy
```

或使用手動腳本：

```bash
sh depoly.sh
```

---

## Gulp 任務說明

| 任務 | 說明 |
|------|------|
| `gulp`（default）| clean → 複製靜態檔 → 編譯 HTML/SCSS/JS → 啟動開發伺服器並 watch |
| `gulp build` | clean → 複製靜態檔 → 編譯 HTML/SCSS/JS（不啟動伺服器）|
| `gulp clean` | 刪除 `dist/` |
| `gulp deploy` | 將 `dist/` 推送至 gh-pages 分支 |

---

## 開發分支

| 分支 | 說明 |
|------|------|
| `main` | 穩定版本 |
| `feature/v2-new-report` | V2 新版報告開發中（新版圖片與排版）|

---

## 作者

Chris Chiang — [GitHub](https://github.com/chris1085)
