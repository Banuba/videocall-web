# Banuba Web AR SDK and Agora Web SDK integration example  
  
**Important**  
Please use [v0.x](../../tree/v0.x) branch for SDK version 0.x (e.g. v0.38).  
  
## Requirements

- Banuba [client token](#obtaining-banuba-client-token)
- Agora [App ID](https://docs.agora.io/en/Agora%20Platform/term_appid), [Token](https://docs.agora.io/en/video-calling/reference/glossary?platform=ios#token) and [Channel](https://docs.agora.io/en/video-calling/reference/glossary?platform=ios#channel) name
- [Nodejs](https://nodejs.org/en/) installed
- Browser with support of [WebGL 2.0](https://caniuse.com/#feat=webgl2)

### Obtaining Banuba SDK Web AR

The example uses CDN version of the [@banuba/webar](https://www.npmjs.com/package/@banuba/webar) npm package for simplicity. Please use the npm package mentioned above for real world projects. Check out the [Integration tutorials](https://docs.banuba.com/face-ar-sdk-v1/web/web_tutorials_integrations) for more ways of consuming [@banuba/webar](https://www.npmjs.com/package/@banuba/webar) package.

### Obtaining Banuba Client token

Banuba Client token is required to get Banuba SDK Web AR working.

Generally it's delivered with Banuba SDK Web AR archive.

To receive a new **trial** client token please fill in the [form on banuba.com](https://www.banuba.com/face-filters-sdk) website, or contact us via [info@banuba.com](mailto:info@banuba.com).

## Environment setup and local run

Clone the repository

```sh
git clone https://github.com/Banuba/videocall-web
```

Insert Banuba [client token](#obtaining-banuba-client-token) into `BanubaClientToken.js`

```js
window.BANUBA_CLIENT_TOKEN = "PUT YOUR CLIENT TOKEN HERE"
```

Insert Agora [App ID](https://docs.agora.io/en/Agora%20Platform/term_appid), [Token](https://docs.agora.io/en/video-calling/reference/glossary?platform=ios#token) and [Channel](https://docs.agora.io/en/video-calling/reference/glossary?platform=ios#channel) name into `AgoraAppId.js`

```js
window.AGORA_APP_ID = "PUT YOUR APP ID HERE"
window.AGORA_TOKEN = "PUT YOUR TOKEN HERE"
window.AGORA_CHANNEL_NAME = "PUT YOUR CHANNEL NAME HERE"
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
      Glasses.zip
      Hipster3.zip
      MonsterFactory.zip
      test_BG.zip
+     new_effect.zip
   AgoraAppId.js
   BanubaClientToken.js
   index.html
   LICENSE
   README.md
   styles.css
```

Add the effect name into `effects` array at [index.html, line 50](/index.html#L50)

```diff
<script type="module">
  const effects = [
+   "new_effect",
    "Glasses",
    "Hipster3",
    "MonsterFactory",
    "test_BG",
  ]
```