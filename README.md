# BlizTik API

Simple HTTP API for extracting TikTok media information and downloadable media.

BlizTik API is designed for developers who want to process TikTok URLs without building the media extraction layer themselves.

> **Unofficial API:** BlizTik is not affiliated with, sponsored by, or endorsed by TikTok.

---

## Features

- 🎬 TikTok video extraction
- 🚫 No-watermark video when available
- ▶️ Video preview URL
- 📸 TikTok photos and slideshows
- 🎵 Music / audio when available
- 🖼️ Cover and author information
- 📊 Video metadata
- 🔗 Separate media URLs
- 🌐 CORS support
- 🛡️ Basic request protection and rate limiting
- ⚡ Simple HTTP GET requests

---

## API Endpoint

### Parse a TikTok URL

```http
GET https://api.bliztik.web.id/apitiktok?url=YOUR_TIKTOK_URL
```

The TikTok URL should be URL-encoded when used as a query parameter.

### Example

```text
https://api.bliztik.web.id/apitiktok?url=https%3A%2F%2Fwww.tiktok.com%2F%40username%2Fvideo%2F123456789
```

---

## JavaScript

```js
const tiktokUrl =
  "https://www.tiktok.com/@username/video/123456789";

const apiUrl =
  "https://api.bliztik.web.id/apitiktok?url=" +
  encodeURIComponent(tiktokUrl);

const response = await fetch(apiUrl);
const data = await response.json();

console.log(data);
```

---

## cURL

```bash
curl "https://api.bliztik.web.id/apitiktok?url=YOUR_TIKTOK_URL"
```

---

# Response

A successful request returns a JSON response.

## Video Response

```json
{
  "code": 200,
  "msg": "Parse successful - Bliz",
  "data": {
    "platform": "TikTok",
    "type": "video",
    "title": "Example TikTok video",
    "desc": "Example description",
    "author": {
      "name": "username",
      "id": "",
      "avatar": "https://..."
    },
    "cover": "https://...",
    "preview_url": "https://api.bliztik.web.id/api/proxy?...",
    "no_watermark_url": "https://api.bliztik.web.id/api/proxy?...",
    "audio_url": "https://api.bliztik.web.id/api/proxy?...",
    "link": "https://www.tiktok.com/@username/video/123456789",
    "quality": "1080p",
    "duration": 22,
    "width": 1080,
    "height": 1920,
    "images": [],
    "music": {
      "title": "Music title",
      "author": "Music author",
      "url": "https://...",
      "cover": "https://..."
    }
  }
}
```

### Video URL fields

| Field | Description |
| --- | --- |
| `preview_url` | URL intended for video preview/playback |
| `no_watermark_url` | No-watermark video download URL when available |
| `audio_url` | Audio/music URL when available |
| `link` | Original TikTok post URL |

Each media URL is returned separately so applications can use them independently.

---

# Photo / Slideshow Response

Photo and slideshow posts use:

```json
{
  "code": 200,
  "msg": "Parse successful - Bliz",
  "data": {
    "platform": "TikTok",
    "type": "photo",
    "title": "Example photo post",
    "desc": "Example description",
    "author": {
      "name": "username",
      "id": "",
      "avatar": "https://..."
    },
    "cover": "https://...",
    "link": "https://www.tiktok.com/@username/photo/123456789",
    "images": [
      "https://...",
      "https://...",
      "https://..."
    ],
    "music": {
      "title": "Music title",
      "author": "Music author",
      "url": "https://...",
      "cover": "https://..."
    }
  }
}
```

The `images` array contains the detected slideshow images in their original order.

---

# Live Photo

TikTok Live Photos are returned as:

```json
{
  "type": "video"
}
```

because a Live Photo contains a video component.

---

# Response Fields

## Main fields

| Field | Type | Description |
| --- | --- | --- |
| `code` | number | API status code |
| `msg` | string | Response message |
| `data.platform` | string | Platform name |
| `data.type` | string | `video` or `photo` |
| `data.title` | string | TikTok title |
| `data.desc` | string | TikTok description |
| `data.cover` | string | Cover image URL |
| `data.link` | string | Original TikTok URL |

## Author

```json
"author": {
  "name": "username",
  "id": "",
  "avatar": "https://..."
}
```

## Video metadata

| Field | Description |
| --- | --- |
| `quality` | Detected video quality |
| `duration` | Video duration in seconds |
| `width` | Video width |
| `height` | Video height |
| `preview_url` | Video preview endpoint |
| `no_watermark_url` | No-watermark video endpoint |
| `audio_url` | Audio endpoint when available |

Metadata availability can depend on the TikTok post and the data returned at request time.

## Music

When music information is available:

```json
"music": {
  "title": "Music title",
  "author": "Artist",
  "url": "https://...",
  "cover": "https://..."
}
```

---

# Media Types

| Media | Availability |
| --- | --- |
| TikTok video | ✅ Available |
| No-watermark video | ✅ When available |
| Video preview | ✅ Available |
| Music / audio | ✅ When available |
| TikTok photo | ✅ Available |
| Slideshow | ✅ Available |
| Live Photo | ✅ Returned as video |
| Author information | ✅ Available when detected |
| Cover image | ✅ Available when detected |
| Video metadata | ✅ When available |

---

# Using the Media URLs

## Video Preview

Use:

```text
preview_url
```

This URL is intended for video playback or preview.

## No-Watermark Video

Use:

```text
no_watermark_url
```

When available, this endpoint provides the no-watermark video stream.

## Audio / Music

Use:

```text
audio_url
```

This provides the audio/music stream when available.

## Photos

Use:

```text
images[]
```

Each item represents one image from the TikTok slideshow.

---

# Node.js Example

```js
async function getTikTok(url) {
  const api =
    "https://api.bliztik.web.id/apitiktok?url=" +
    encodeURIComponent(url);

  const response = await fetch(api);

  if (!response.ok) {
    throw new Error(`HTTP ${response.status}`);
  }

  return await response.json();
}

const result = await getTikTok(
  "https://www.tiktok.com/@username/video/123456789"
);

if (result.code === 200) {
  const data = result.data;

  console.log("Type:", data.type);

  if (data.type === "video") {
    console.log("Preview:", data.preview_url);
    console.log("No watermark:", data.no_watermark_url);
    console.log("Audio:", data.audio_url);
  }

  if (data.type === "photo") {
    console.log("Photos:", data.images);
  }
}
```

---

# Error Response

If a request cannot be processed, the API may return an error.

### Invalid URL

```json
{
  "code": 400,
  "msg": "Invalid TikTok URL"
}
```

### Temporary media parsing error

```json
{
  "code": 502,
  "msg": "TikTok media could not be parsed right now"
}
```

Applications should check `code` before using media fields.

---

# How It Works

```text
TikTok URL
    ↓
BlizTik API
    ↓
TikTok media extraction
    ↓
Media processing
    ↓
JSON response
    ↓
Your application
```

For video posts, BlizTik can provide separate endpoints for preview, no-watermark video, and audio when those media are available.

---

# Supported Applications

BlizTik API can be used from almost anything that can make an HTTP request:

- 🌐 Websites
- 📱 Android applications
- 🟢 Node.js projects
- 🤖 Discord bots
- 💬 WhatsApp bots
- ⚙️ Backend services
- 🔧 Automation tools
- 📦 Other applications

---

# Project Structure

```text
BlizTik-API/
├── assets/
│   ├── blizTikApi-request.png
│   ├── blizTikApi-video.png
│   ├── blizTikApi-photo.png
│   └── blizTikApi-audio.png
├── README.md
└── ...
```

The `assets` folder contains images used only for the documentation.

---

# Preview

### API Request

![BlizTik API request](assets/blizTikApi-request.png)

### Video Result

![BlizTik API video result](assets/blizTikApi-video.png)

### Photo Result

![BlizTik API photo result](assets/blizTikApi-photo.png)

### Audio Result

![BlizTik API audio result](assets/blizTikApi-audio.png)

---

# Rate Limits & Request Protection

Basic request protection and rate limiting are enabled.

Please avoid:

- Sending excessive requests
- Repeatedly requesting the same URL at high speed
- Using the API for unnecessary continuous polling

For applications with repeated requests, cache results when appropriate.

---

# CORS

BlizTik API supports cross-origin requests.

This makes it possible to use the API from browser-based applications as well as backend services.

---

# Notes & Limitations

BlizTik API is a best-effort TikTok media extraction service.

Not every TikTok post is guaranteed to return every media field.

A post may fail or return incomplete data because of:

- Private posts
- Deleted posts
- Region restrictions
- Age or account restrictions
- TikTok changes
- Temporary TikTok CDN errors
- Anti-bot protection
- Rate limiting
- Media that is unavailable at request time

Media availability can change between requests.

---

# Example Use Cases

BlizTik API can be integrated into:

- TikTok downloader websites
- Media management tools
- Discord bots
- WhatsApp bots
- Android applications
- Web applications
- Backend services
- Automation projects

---

# Visit BlizTik

**Website:** https://bliztik.web.id

**API:** https://api.bliztik.web.id/apitiktok

---

# Disclaimer

BlizTik is an unofficial third-party project and is not affiliated with, sponsored by, or endorsed by TikTok.

Users are responsible for complying with TikTok's terms, applicable laws, and the rights associated with content they access or download.

---

# License

See the repository license for the terms applicable to this project.
