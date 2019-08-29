# 開發現代化的靜態 PWA - 黃胤翔 (Ben)

{%hackmd yEJ_rTxzTWa2K450RqmT8w %}

## 大綱

- 推坑工具 [GatsbyJS](https://www.gatsbyjs.org/)
- Slide [開發現代化的靜態 PWA](http://slides.com/hinx/gatsby)

## 需求

- landing page
- SEO
- 最短時間開發
- 來點潮潮的工具

## GatsbyJ 介紹

- one of graphql
- static site generator
- based on 

### 現代化


### 兩種Pre-rendering
- On demand Traditional ==SSR==
- Static export 
    - 預先把內容輸出，不需要

### Official Starters

- 官方提供
    - starter-defalult: 設定及樣板
    - starter-blog
    - starter-hello-world
- [From Community](https://www.gatsbyjs.org/starters/)


### Data Layer
使用 GraphQL 定義每個 Component 所需要的資料
- Page query
- Static query

### Packages/Plugins

#### 根據用途區分
- Source
- Transformer
- Others

已經處理好圖片優化、預先加載，讓速度變快


#### 常用的
- gatsby-image
- gatsby-plugin-sharp
- gatsby-source-filesystem
- gatsby-plugin-offline
- gatsby-plugin-manifest
- gatsby-plugin-feed
- gatsby-plugin-react-helmet

#### 客製化你的Gatsby
- gatsby-config.js
- gatsby-node.js
- gatsby-browser.js
- gatsby-ssr.js



## Use case

#### Code Snippet
[Prism.js](https://prismjs.com)
> 搭配 transformer remark



#### Styling

- Global CSS
- Modular Stylesheets
- CSS-in-JS



Github + [Contentful](https://www.contentful.com/) + [Netlify](https://www.netlify.com/)


### Search
- 數量大: 考慮 [elestic search](https://www.elastic.co/cn/)
- 數量小做在前端


## Gatsby 適合你嗎？


### 有什麼其他選擇
- 自幹 SSR
- [React Static](https://github.com/react-static/react-static)
- [Next.js](https://nextjs.org/features/static-exporting)
- 其他


### Next.js vs Gatsby
- Next.js => 適合大型架構
- Gatsby => 適合快速開發靜態頁面

###### tags: `MW19`
