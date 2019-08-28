# 請在網頁中使用 3D - 郝稼力 (HiWebGL)

{%hackmd yEJ_rTxzTWa2K450RqmT8w %}

## 用途
1. 3D 模型展示
    - Nike 鞋展示
    - 3D 醫療模型
3. (VR, AR, MR) => WebXR(XR)
    - AR 化學教材
    - Looking Glass
    - Magic Leaps(MICA)
3. 用 3D 技術提升網頁的視覺和創意體驗
    - [模擬液體晃動](https://liquid.lab.lorenzocadamuro.com)
    - Sky Net 東京飛機軌道圖
4. 平行運算 - WebGL 2.0 Compute Shader
    - 支援 GPU 運算 (CPU sort v.s GPU sort)

## 性能問題
- [offscreencanvas](https://developer.mozilla.org/en-US/docs/Web/API/OffscreenCanvas)
    支援 [Web Workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API) 
處理好再丟回主執行緒渲染 -> 可避免主執行緒阻塞
- [ComLink](https://github.com/GoogleChromeLabs/comlink)
- [Web Assembly](https://zh.wikipedia.org/wiki/WebAssembly)
(強推 [AssemblyScript](https://docs.assemblyscript.org/))
> 私心推 [Rust](https://rustwasm.github.io/docs/book/) [name=DanSnow]

### 3D 模型渲染
- 紋理壓縮 [Universal Basis](https://github.com/binomialLLC/basis_universal)
[.jpeg vs .basis](https://www.khronos.org/blog/google-and-binomial-contribute-basis-universal-texture-format-to-khronos-gltf-3d-transmission-open-standard)
- 幾何體壓縮 [Draco](https://google.github.io/draco/)

## 易用性

- Web Component


[GoogleWebComponent/model-viewer](https://developers.google.com/web/updates/2019/02/model-viewer)

## 流行的 3D 框架
- [Babylon.js](https://www.babylonjs.com/)
  流程化 3D 引擎、微軟出品 (照著流程做就行了，體積較大)
- [Three.js](https://threejs.org/)
  工具箱、社群生態豐富(只提供工具 體積較小 透過開源社區貢獻開發)
- [PlayCanvas](https://playcanvas.com/)
  以 web 遊戲為主要目標的遊戲引擎框架，被 [snapchat](https://www.snapchat.com/) 收購

## 組件化開發庫
- A-Frame
    開發VR based on three.js
- Vue-Babylon
- React Three Fiber 
- @sveltejs/gl





###### tags: `MW19`
