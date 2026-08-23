🚀 BlizTik API

«A simple REST API for retrieving TikTok media and metadata from public URLs.»

"BlizTik API" (assets/banner.png)

BlizTik API provides a simple way to extract media and basic metadata from public TikTok posts. It can handle videos, photos, slideshows, audio, and author information through a lightweight REST endpoint.

No SDK required. Just send a TikTok URL and receive a JSON response.

✨ Features

- 🎬 TikTok video extraction
- 🚫 No-watermark video URLs when available
- 📸 Photo and slideshow support
- 🎵 Audio and music extraction
- 👤 Author and post metadata
- 🌐 CORS support for browser-based applications
- ⚡ Simple HTTP-based API
- 🧩 Easy integration with websites, bots, apps, and backends

🔄 How It Works

The API follows a simple request flow:

TikTok URL
    ↓
BlizTik API
    ↓
Media extraction
    ↓
JSON response
    ↓
Your application

"BlizTik API Flow" (assets/architecture.svg)

Send a public TikTok URL to the API, and it will process the post and return the available media and metadata as JSON.

🧪 Try It

You can test the API directly using the BlizTik API test page:

https://bliztik-api.vercel.app/

Paste a public TikTok URL, click GET, and inspect the returned status, response time, and JSON data.

🚀 Quick Start

Endpoint

https://api.bliztik.web.id/apitiktok?url=YOUR_TIKTOK_URL

Replace "YOUR_TIKTOK_URL" with the TikTok URL you want to process.

When constructing the request programmatically, make sure the URL is properly URL-encoded.

JavaScript

const response = await fetch(
  "https://api.bliztik.web.id/apitiktok?url=" +
  encodeURIComponent(tiktokUrl)
);

const data = await response.json();

console.log(data);

cURL

curl "https://api.bliztik.web.id/apitiktok?url=YOUR_TIKTOK_URL"

📦 Response

The API returns JSON containing the media and metadata available for the requested post.

Common fields may include:

video
no_watermark_url
audio_url
images
author
title
quality
width
height

The returned fields can vary depending on the type of TikTok post.

For example, a video post may contain video and audio information, while a photo or slideshow post may primarily contain image URLs.

🧩 Integration

BlizTik API can be integrated into any application capable of making HTTP requests.

Common use cases include:

- 🌐 Web applications
- 📱 Mobile applications
- 🤖 Bots
- 🟢 Node.js applications
- ⚙️ Backend services
- 🔌 REST API clients
- 🛠️ Media utility projects

Example architecture:

Your Application
       │
       │ HTTP Request
       ▼
BlizTik API
       │
       │ JSON
       ▼
Your Application
       │
       ├── Display media
       ├── Process metadata
       └── Handle downloads

🛡️ Usage

BlizTik API is designed for publicly accessible TikTok content.

Private, deleted, restricted, or otherwise unavailable posts may return an error or incomplete information.

Please avoid excessive requests or usage patterns that place unnecessary load on the service.

You are responsible for ensuring that your application and use of retrieved content comply with applicable laws, platform rules, and content rights.

🌐 Links

- Live API: https://api.bliztik.web.id
- API Test: https://bliztik-api.vercel.app/
- Website: https://bliztik.web.id
- GitHub: https://github.com/BlizPS/bliztik-api

📄 License

This project is open source. See the repository for the applicable license and project files.

📌 About

BlizTik API is an open-source project focused on making TikTok media integration simple.

Instead of implementing the extraction process yourself, your application can send a public TikTok URL to the API and work with the resulting JSON data.

Built for simple integrations, experiments, and projects that need a lightweight TikTok media API.