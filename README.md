# 🚀 BlizTik API

> Fast and simple TikTok media extraction API for developers.

![BlizTik API](assets/banner.png)

BlizTik API lets you process public TikTok URLs and retrieve video, photo, slideshow, audio, and media metadata as JSON.

## ✨ Features

- 🎬 TikTok video & no-watermark video
- 📸 Photo & slideshow extraction
- 🎵 Audio / music extraction
- 👤 Author & media metadata
- 🌐 CORS support
- ⚡ Simple HTTP requests
- 🧩 Easy integration

## 🎞️ See It in Action

![BlizTik API Demo](assets/demo.gif)

## 🔄 API Flow

![BlizTik API Flow](assets/architecture.svg)

## 🚀 Quick Start

### API Endpoint

```text
https://api.bliztik.web.id/apitiktok?url=YOUR_TIKTOK_URL
```

### JavaScript

```js
const response = await fetch(
  "https://api.bliztik.web.id/apitiktok?url=" +
  encodeURIComponent(tiktokUrl)
);

const data = await response.json();

console.log(data);
```

### cURL

```bash
curl "https://api.bliztik.web.id/apitiktok?url=YOUR_TIKTOK_URL"
```

## 📦 Response

BlizTik API returns JSON containing the media and metadata extracted from the TikTok post.

Common fields include:

```text
video
no_watermark_url
audio_url
images
author
title
quality
width
height
```

The response structure can vary depending on the type of TikTok post.

## 🧩 Integration

BlizTik API works with any application that can make HTTP requests, including:

- Websites
- Node.js applications
- Mobile applications
- Bots
- Backend services
- Other REST API clients

## 🛡️ Usage Notes

BlizTik API is designed for publicly accessible TikTok content.

Private, deleted, restricted, or unavailable posts may return an error or incomplete media data.

Please use the API responsibly and avoid excessive or abusive traffic.

## 🌐 Links

- **Live API:** https://api.bliztik.web.id
- **Website:** https://bliztik.web.id
- **GitHub:** https://github.com/BlizPS/bliztik-api

## 📄 License

Released under the MIT License.

See [`LICENSE`](LICENSE) for the full license text.
