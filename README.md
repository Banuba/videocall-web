# Banuba Web AR SDK and Agora Web SDK integration example  
  
**Important**  
Please use [v0.x](../../tree/v0.x) branch for SDK version 0.x (e.g. v0.38).  
  
## Requirements

- The [latest](#obtaining-banuba-sdk-web-ar) Banuba SDK Web AR release
- Banuba [client token](#obtaining-banuba-client-token)
- Agora [App ID](https://docs.agora.io/en/Agora%20Platform/term_appid)
- [Nodejs](https://nodejs.org/en/) installed
- Browser with support of [WebGL 2.0](https://caniuse.com/#feat=webgl2)

### Obtaining Banuba SDK Web AR

To get the latest Banuba SDK Web AR release please fill in the [form on banuba.com](https://www.banuba.com/face-filters-sdk) website, or contact us via [info@banuba.com](mailto:info@banuba.com).

### Obtaining Banuba Client token

Banuba Client token is required to get Banuba SDK Web AR working.

Generally it's delivered with Banuba SDK Web AR archive.

To receive a new **trial** client token please fill in the [form on banuba.com](https://www.banuba.com/face-filters-sdk) website, or contact us via [info@banuba.com](mailto:info@banuba.com).

## Environment setup and local run

Clone the repository

```sh
git clone https://github.com/Banuba/videocall-web
```

Put Banuba SDK Web AR [files](#obtaining-banuba-sdk-web-ar) into the cloned folder

```diff
videocall-web/
   effects/
   AgoraAppId.js
   BanubaClientToken.js
+  BanubaSDK.data
+  BanubaSDK.js
+  BanubaSDK.wasm
+  BanubaSDK.simd.wasm
   index.html
   LICENSE
   peer.html
   README.md
   styles.css
```

Insert Banuba [client token](#obtaining-banuba-client-token) into `BanubaClientToken.js`

```js
window.BANUBA_CLIENT_TOKEN = "PUT YOUR CLIENT TOKEN HERE"
```

Insert Agora [App ID](https://docs.agora.io/en/Agora%20Platform/term_appid) into `AgoraAppId.js`

```js
window.AGORA_APP_ID = "PUT YOUR APP ID HERE"
```

### Test by yourself

Run the live server in the cloned folder
```sh
npx live-server
```

Open [localhost:8080](http://localhost:8080) in two different browser windows.

### Testing with mate

Set up the project on mate's PC.

Run the live server in the cloned folders on both PCs.
```sh
npx live-server
```

Open [localhost:8080](http://localhost:8080) on both PCs.

## Adding a new effect

Zip the effect folder and put it under the `effects/` subfolder
```diff
videocall-web/
   effects/
     Background.zip
     Earring.zip
     glasses_Banuba.zip
     Hipster3.zip
+    NewEffect.zip
   AgoraAppId.js
   BanubaClientToken.js
   BanubaSDK.data
   BanubaSDK.js
   BanubaSDK.wasm
   index.html
   LICENSE
   README.md
   styles.css
```

Add the effect name into `effects` array at [index.html, line 38](/index.html#L38)

```diff
<script type="module">
  import { Effect, Webcam, Player, VideoRecorder, ImageCapture, Dom } from "./BanubaSDK.js"

  const effects = [
+   "NewEffect",
    "Background",
    "Earring",
    "glasses_Banuba",
    "Hipster3",
  ]
```