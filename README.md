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

## 🔄 API Flow

![BlizTik API Flow](assets/architecture.svg)

## 🧪 API Test Page

Want to quickly check whether the live API is responding?

Open the test page:

**https://bliztik-api.vercel.app/**

Paste a public TikTok URL and press **GET**. The page shows the HTTP status, real request timing, and the JSON returned by the API.

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

BlizTik API returns JSON containing media information and metadata from the requested TikTok post.

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
- **API Test:** https://bliztik-api.vercel.app/
- **Website:** https://bliztik.web.id
- **GitHub:** https://github.com/BlizPS/bliztik-api

## 📌 About

BlizTik API is an open-source project for developers who want a simple way to integrate TikTok media extraction into their applications.

Use the source code, explore the API, build integrations, and adapt the project to your own needs.
