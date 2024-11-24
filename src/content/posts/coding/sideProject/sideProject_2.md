---
title: 網頁練習作品 2 - 購物網站 Step 0
published: 2024-11-24
description: '專案規格 & 功能規劃'
image: '/posts/coding/sword_girl.jpg'
tags: [SideProject]
category: '程式設計'
draft: true
lang: ''
---
<!-- 1. 專案架構 -->
# 專案架構
## 開發框架
- **Next.js**
  - 用於實現伺服器端渲染和動態路由。
  - 提升頁面渲染速度，適合產品列表和商品詳情頁。

## 样式和 UI
- **Tailwind CSS**
  - 快速設計響應式界面。
  - 支持商品卡片、導航欄、購物車按鈕等功能。

## 資料狀態管理
- **React Context API** 或 **Redux Toolkit**
  - Context API：適合處理中小型應用的購物車狀態。
  - Redux Toolkit：適合未來需要多步驟結帳流程的項目。

## 後端 API
- **Next.js API Routes**
  - 模擬後端功能，處理資料讀取和提交，例如：
    - 商品資料讀取（GET）。
    - 新增訂單（POST）。

## 模擬數據庫
- **Fake REST API** 或 **JSON Server**
  - 假數據模擬：
    - 商品列表：ID、名稱、價格、庫存。
    - 用戶資料：ID、姓名、地址。
    - 訂單資料：ID、商品、數量、總額。

## 認證和登錄
- **NextAuth.js**
  - 支持 Email 密碼登錄和第三方登錄（如 Google、Facebook）。

## 支付功能
- **Stripe（模擬支付）**
  - 支持生成假支付界面，使用沙盒模式進行測試。

## 部署
- **Vercel**
  - 與 Next.js 完美兼容，免費提供 SSL 支持。

---
<!-- 2. 基礎功能規劃 -->
# 功能規劃
## 基礎功能
1. **商品展示頁**
   - 動態渲染商品清單。
   - 支持篩選（價格、類別）和排序。

2. **商品詳情頁**
   - 顯示商品圖片、描述、價格、庫存。
   - 加入購物車按鈕。

3. **購物車功能**
   - 添加、刪除商品。
   - 計算總價和數量。

4. **用戶登錄和註冊**
   - Email 密碼認證。
   - 記住用戶購物車狀態。

5. **結帳頁面**
   - 填寫地址和支付方式（模擬 Stripe 支付）。

6. **訂單確認頁**
   - 顯示訂單編號、商品詳情和預計送達日期。

## 進階功能
1. **SEO 優化**
   - 使用 Next.js 的 `getServerSideProps` 或 `getStaticProps`。
   - 添加產品頁的動態 meta tags。

2. **模擬庫存管理**
   - 購買後減少商品庫存。
   - 庫存不足禁用購買按鈕。

3. **物流追蹤（假數據）**
   - 顯示訂單進度（待出貨、配送中、已完成）。

4. **社交分享**
   - 添加 Facebook 和 Twitter 的商品分享按鈕。

---
# 安裝和起步指令

## 安裝指令
```bash
# 創建 Next.js 專案
npx create-next-app@latest shopping-site --typescript

# 安裝 SCSS
npm install sass

# 安裝 Stripe 支付
npm install @stripe/stripe-js
npm install stripe

# 安裝認證
npm install next-auth

# 啟動開發伺服器
npm run dev
```

## 安裝選項介紹

> √ Would you like to use `ESLint`? ... No / Yes `(recommended) `

- **選擇：Yes（建議）**
- **解釋：**
  - ESLint 是一個 **語法檢查工具**，專注於代碼品質與風格統一。
  - **使用它的好處：**
    - 幫助你發現常見錯誤（如未使用的變量、未定義的函數等）。
    - 強制統一代碼風格，讓代碼更易讀，特別是團隊開發時。
    - 減少潛在 Bug，提升代碼穩定性。
  - 選擇 **Yes** 時，Next.js 會自動安裝 ESLint 並設置預設配置，與 React 和 TypeScript 高度兼容。
  - 如果選擇 **No**，則不會安裝，但可以隨時手動加回。

> √ Would you like to use `Tailwind CSS`? ... No / Yes

- **選擇：Yes**
- **解釋：**
  - Tailwind CSS 是一個功能強大的 **實用工具優先（Utility-First）CSS 框架**。
  - **使用它的好處：**
    - 提供豐富的預設樣式（如 `bg-blue-500`、`p-4`），免去繁瑣的 CSS 編寫。
    - 支援響應式設計，通過簡單的類名實現不同屏幕大小的樣式。
    - 可高度客製化，通過修改配置文件來定義自己的設計系統。
  - 選擇 **Yes** 時，Next.js 會自動安裝 Tailwind CSS 並完成基礎配置。

> √ Would you like your code inside a `src/` directory? ... No / Yes

- **選擇：Yes**
- **解釋：**
  - **`src/` 目錄** 是一種常見的專案結構，用於集中存放應用的代碼（例如組件、頁面、樣式等）。
  - **使用它的好處：**
    - 提升代碼的組織性，讓專案結構更加清晰。
    - 在大型專案中，方便區分應用代碼與配置文件（如 `package.json`、環境文件）。
  - 選擇 **Yes** 時，Next.js 會自動將代碼放置於 `src/` 目錄下，否則代碼會位於專案根目錄中。

> √ Would you like to use `App Router`? (recommended) ... No / Yes

- **選擇：Yes（建議）**
- **解釋：**
  - **App Router** 是 Next.js 13 引入的新路由系統，基於 React Server Components (RSC) 架構設計。
  - **使用它的好處：**
    - 支援更靈活的路由定義，使用 `app/` 文件夾替代傳統的 `pages/` 文件夾。
    - 提供更多功能，如 `layout.tsx`（共享佈局）、`loading.tsx`（載入狀態）、`error.tsx`（錯誤處理）。
    - 提升性能，充分利用伺服器端渲染（SSR）和 React Server Components。
  - 選擇 **Yes** 時，Next.js 專案會採用新的路由系統（基於 `app/` 文件夾）。
  - 如果選擇 **No**，則會使用傳統的路由系統（基於 `pages/` 文件夾）。

> √ Would you like to use `Turbopack` for next dev? ... No / Yes

- **選擇：Yes（建議）**
- **解釋：**
  - **Turbopack** 是 Vercel 推出的新一代超高速打包工具，專為 Next.js 開發而設。
  - **使用它的好處：**
    - 編譯速度極快，特別是在大型專案中，能顯著提升開發效率。
    - 支援增量更新，代碼修改後只重新編譯受影響的部分。
    - 將成為 Next.js 的默認工具，學習它能走在技術前沿。
  - 選擇 **Yes** 時，開發模式（`npm run dev`）下會使用 Turbopack。
  - 如果選擇 **No**，則繼續使用 Webpack 作為打包工具。

> √ Would you like to customize the `import alias` ( `@/*` by default)? ... No / Yes

- **選擇：No（建議保持預設）**
- **解釋：**
  - **Import alias** 是為了讓代碼中的模組引用更簡潔。預設使用 `@/` 表示專案根目錄。
  - **使用它的好處：**
    - 避免相對路徑的混亂，例如從 `../../components` 簡化為 `@/components`。
    - 提升代碼可讀性和維護性。
  - 選擇 **No** 時，保持預設 `@/` 別名。
  - 選擇 **Yes** 時，可以自定義別名，例如 `~/` 或其他你喜歡的符號。
  - 如果後續需要更改，可以修改 `tsconfig.json` 或 `jsconfig.json`。
