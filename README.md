# BlizTik API

> **A fast, free TikTok downloader API for developers, with support for video, photos, audio, and metadata through a single request.**

[![MIT License](https://img.shields.io/github/license/BlizPS/bliztik-api?style=flat-square)](https://github.com/BlizPS/bliztik-api/blob/main/LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/BlizPS/bliztik-api?style=flat-square)](https://github.com/BlizPS/bliztik-api/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/BlizPS/bliztik-api?style=flat-square)](https://github.com/BlizPS/bliztik-api/network/members)
[![Version](https://img.shields.io/badge/version-1.0.0-blue?style=flat-square)](https://github.com/BlizPS/bliztik-api)
[![API Status](https://img.shields.io/badge/API%20Status-Online-brightgreen?style=flat-square)](https://api.bliztik.web.id/apitiktok?url=)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/BlizPS/bliztik-api?style=flat-square)](https://github.com/BlizPS/bliztik-api/commits/main)

**Website:** https://bliztik.web.id  
**Direct API Endpoint:** https://api.bliztik.web.id/apitiktok?url=  
**Test API:** https://bliztik-api.vercel.app/  
**Repository:** https://github.com/BlizPS/bliztik-api

[Website](https://bliztik.web.id) · [Documentation](https://github.com/BlizPS/bliztik-api#-documentation-endpoint) · [Report a Bug](https://github.com/BlizPS/bliztik-api/issues/new) · [Request a Feature](https://github.com/BlizPS/bliztik-api/issues/new)

---

## 📚 Table of Contents

- [About the Project](#-about-the-project)
- [Why BlizTik?](#-why-bliztik)
- [BlizTik Highlights](#-bliztik-highlights)
- [Quick Start](#-quick-start)
  - [cURL](#curl)
  - [JavaScript](#javascript-fetch)
  - [Python](#python-requests)
- [Documentation Endpoint](#-documentation-endpoint)
  - [Endpoint](#endpoint)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Response](#response)
- [Full Response Example](#-full-response-example)
- [Response Field Reference](#-response-field-reference)
- [Code Examples & Integrations](#-code-examples--integrations)
  - [Node.js](#nodejs-axios)
  - [Python](#python-aiohttp)
  - [PHP](#php-curl)
  - [HTML / Vanilla JavaScript](#html--vanilla-javascript-fetch)
- [Roadmap](#-roadmap)
- [FAQ](#-faq)
- [Contributing](#-contributing)
- [Disclaimer](#-disclaimer)
- [License](#-license)
- [Credits](#-credits)

---

## 🚀 About the Project

**BlizTik API** is an open-source REST API for extracting downloadable media and useful metadata from public TikTok URLs. It is built for developers who want a simple HTTP interface instead of maintaining the entire extraction workflow themselves.

The API supports **TikTok videos, no-watermark video URLs, photos and slideshows, audio, post metadata, author information, cover images, media dimensions, and duration**. The response is returned as structured JSON so it can be consumed by websites, backend services, bots, mobile applications, automation tools, and other developer projects. 🌐

BlizTik keeps the integration model intentionally simple: **one public endpoint, no API key, standard GET requests, and browser-friendly CORS support**.

> Built for developers, easy to integrate, and quick to get started.

---

## ✨ Why BlizTik?

- 🆓 **100% Free** — no subscription is required to use the public endpoint.
- 🔑 **No API Key** — send the TikTok URL directly without an authentication key or authorization header.
- 🚀 **Super Fast** — designed for low-latency processing with a target response time of **under 2 seconds** under normal conditions.
- ♾️ **No Fixed Public Quota** — no fixed per-user daily quota is published for the public endpoint.
- 🎬 **HD Video** — supports high-quality video output, including the `1024p` quality shown by the live API response.
- 🧼 **No-Watermark Video** — provides a dedicated `no_watermark_url` for video downloads.
- 📸 **Photo & Slideshow** — supports image-based TikTok posts through the `images` field.
- 🎵 **Audio** — provides direct audio information and a downloadable `music.url` value.
- 🖼️ **Cover Image** — returns a post cover through the `cover_url` field.
- 👤 **Author Metadata** — returns author name, identifier, and avatar information.
- 📝 **Post Metadata** — returns title, description, source URL, media type, quality, duration, and dimensions.
- 🌐 **CORS Support** — suitable for direct browser-side API requests.
- 🧩 **Simple REST API** — works with standard HTTP clients; no SDK is required.
- 📱 **Cross-Platform** — suitable for web apps, Node.js, Python, PHP, bots, mobile apps, and backend services.
- 🛠️ **Open Source** — the project is publicly available on GitHub.

## 📊 BlizTik Highlights

BlizTik focuses on a straightforward developer experience: use the public endpoint, provide a TikTok URL, and receive structured JSON containing the extracted media and metadata.

| Feature | BlizTik |
| :--- | :---: |
| **API Key** | ❌ Not required |
| **Fixed Public Quota** | ♾️ None published |
| **Speed Target** | ⚡ Under 2s* |
| **HD Video** | ✅ Supported |
| **No Watermark** | ✅ Supported |
| **Photo / Slideshow** | ✅ Supported |
| **Audio** | ✅ Supported |
| **Metadata** | ✅ Supported |
| **Cover Image** | ✅ Supported |
| **Author Information** | ✅ Supported |
| **CORS** | ✅ Supported |
| **Price** | 🆓 Free |
| **Open Source** | ✅ Yes |

> *Actual response time can vary with network conditions, TikTok availability, redirects, upstream extraction, and media complexity.

---

## ⚡ Quick Start

The public endpoint accepts a TikTok URL through the `url` query parameter.

```text
https://api.bliztik.web.id/apitiktok?url={TIKTOK_URL}
```

### cURL

```bash
curl "https://api.bliztik.web.id/apitiktok?url=https%3A%2F%2Fwww.tiktok.com%2F%40username%2Fvideo%2F1234567890123456789"
```

### JavaScript (fetch)

```js
const tiktokUrl = "https://www.tiktok.com/@username/video/1234567890123456789";
const endpoint =
  "https://api.bliztik.web.id/apitiktok?url=" +
  encodeURIComponent(tiktokUrl);

const response = await fetch(endpoint);
const result = await response.json();

console.log(result);
```

### Python (requests)

```py
import requests


tiktok_url = "https://www.tiktok.com/@username/video/1234567890123456789"

from urllib.parse import quote

endpoint = (
    "https://api.bliztik.web.id/apitiktok?url="
    + quote(tiktok_url, safe="")
)

response = requests.get(endpoint, timeout=15)

response.raise_for_status()
result = response.json()

print(result)
```

---

## 📖 Documentation Endpoint

### Endpoint

| Property | Value |
| :--- | :--- |
| **Method** | `GET` |
| **URL Template** | `https://api.bliztik.web.id/apitiktok?url={TIKTOK_URL}` |
| **Content-Type** | `application/json` |
| **Authentication** | None |
| **Required Parameter** | `url` |
| **Input** | Public TikTok URL |
| **Output** | JSON |
| **CORS** | Supported |

The endpoint supports common public TikTok URL formats, including:

- `https://www.tiktok.com/@username/video/...`
- `https://vt.tiktok.com/...`
- `https://vm.tiktok.com/...`

Short links are resolved before the TikTok content is processed.

### Parameters

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `url` | `string` | ✅ | A public TikTok video, photo, or slideshow URL. |

### Example Request

```bash
curl "https://api.bliztik.web.id/apitiktok?url=https%3A%2F%2Fwww.tiktok.com%2F%40username%2Fvideo%2F1234567890123456789"
```

Equivalent direct URL format:

```text
https://api.bliztik.web.id/apitiktok?url=https%3A%2F%2Fwww.tiktok.com%2F%40username%2Fvideo%2F1234567890123456789
```

### Response

A successful request returns an object with a numeric status code, a message, and a nested `data` object.

A typical response has the following structure:

```json
{
  "status_code": 200,
  "message": "Parsing successful - Bliz",
  "data": {
    "platform": "TikTok",
    "media_type": "video",
    "title": "...",
    "description": "...",
    "author": {
      "name": "...",
      "handle": "...",
      "avatar": "https://..."
    },
    "cover_url": "https://...",
    "preview_url": "https://api.bliztik.web.id/api/proxy?...",
    "no_watermark_url": "https://api.bliztik.web.id/api/proxy?...",
    "audio_url": "https://api.bliztik.web.id/api/proxy?...",
    "source_url": "https://www.tiktok.com/@username/video/...",
    "quality": "1024p",
    "duration": 11,
    "width": 576,
    "height": 1024,
    "alternative_videos": [],
    "images": [],
    "music": {
      "title": "",
      "author": "",
      "url": "https://api.bliztik.web.id/api/proxy?...",
      "cover": ""
    },
    "extra": {
      "video_id": "",
      "share_url": "https://www.tiktok.com/@username/video/..."
    }
  }
}
```

---

## 🧾 Full Response Example

The example below uses neutral sample values so the documentation is easy to read without exposing information from a real TikTok post. Media URLs are shortened for readability and may expire.

```json
{
  "status_code": 200,
  "message": "Parsing successful - Bliz",
  "data": {
    "platform": "TikTok",
    "media_type": "video",
    "title": "Example TikTok post",
    "description": "Example TikTok post description",
    "author": {
      "name": "Example Creator",
      "handle": "@example",
      "avatar": "https://example.com/avatar.jpg"
    },
    "cover_url": "https://example.com/cover.jpg",
    "preview_url": "https://api.bliztik.web.id/api/proxy?...",
    "no_watermark_url": "https://api.bliztik.web.id/api/proxy?...",
    "audio_url": "https://api.bliztik.web.id/api/proxy?...",
    "source_url": "https://www.tiktok.com/@example/video/...",
    "quality": "1024p",
    "duration": 11,
    "width": 576,
    "height": 1024,
    "alternative_videos": [],
    "images": [],
    "music": {
      "title": "",
      "author": "",
      "url": "https://api.bliztik.web.id/api/proxy?...",
      "cover": ""
    },
    "extra": {
      "video_id": "",
      "share_url": "https://www.tiktok.com/@example/video/..."
    }
  }
}
```

> **Privacy note:** No real creator username, post ID, title, or personal media URL is included in the documentation examples.

> **Media URL note:** URLs returned by TikTok and the BlizTik proxy may be temporary and can expire. Use the URLs from the latest API response rather than treating them as permanent links.

## 🧩 Response Field Reference

### Top-level fields

| Field | Type | Description |
| :--- | :--- | :--- |
| `status_code` | `number` | Numeric response status. `200` indicates a successful parse. |
| `message` | `string` | Response message returned by the service. |
| `data` | `object` | Parsed TikTok media and metadata. |

### Data fields

| Field | Type | Description |
| :--- | :--- | :--- |
| `platform` | `string` | Source platform name. |
| `media_type` | `string` | Parsed media type, such as `video` or `photo`. |
| `title` | `string` | Post title or caption. |
| `description` | `string` | Post description or caption text. |
| `author` | `object` | Creator information. |
| `cover_url` | `string` | Cover image URL. |
| `preview_url` | `string` | Preview media URL. |
| `no_watermark_url` | `string` | No-watermark video URL. |
| `audio_url` | `string` | Downloadable audio URL. |
| `source_url` | `string` | Original TikTok post URL. |
| `quality` | `string` | Reported media quality, such as `1024p`. |
| `duration` | `number` | Media duration in seconds. |
| `width` | `number` | Media width in pixels. |
| `height` | `number` | Media height in pixels. |
| `alternative_videos` | `array` | Additional video variants, when provided. |
| `images` | `array` | Image URLs for photo or slideshow posts. |
| `music` | `object` | Music metadata and download URL. |
| `extra` | `object` | Additional identifiers and share information. |

### Author fields

| Field | Type | Description |
| :--- | :--- | :--- |
| `author.name` | `string` | Creator display name. |
| `author.handle` | `string` | Creator username or handle, when available. |
| `author.avatar` | `string` | Creator avatar URL. |

### Music fields

| Field | Type | Description |
| :--- | :--- | :--- |
| `music.title` | `string` | Music title. |
| `music.artist` | `string` | Music artist or creator. |
| `music.url` | `string` | Downloadable music URL. |
| `music.cover` | `string` | Music cover information, when available. |

### Extra fields

| Field | Type | Description |
| :--- | :--- | :--- |
| `extra.video_id` | `string` | Video identifier, when available. |
| `extra.share_url` | `string` | Shareable TikTok URL. |


---

## 🔧 Code Examples & Integrations

### Node.js (axios)

Install Axios:

```bash
npm install axios
```

Then:

```js
const axios = require("axios");

async function getTikTokData(tiktokUrl) {
  const endpoint =
  "https://api.bliztik.web.id/apitiktok?url=" +
  encodeURIComponent(tiktokUrl);

  const response = await axios.get(endpoint, {
    timeout: 15000,
    headers: {
      Accept: "application/json"
    }
  });

  return response.data;
}

(async () => {
  try {
    const data = await getTikTokData(
      "https://www.tiktok.com/@username/video/1234567890123456789"
    );

    console.log(data);
  } catch (error) {
    console.error(
      "BlizTik API error:",
      error.response?.data || error.message
    );
  }
})();
```

### Python (aiohttp)

Install `aiohttp`:

```bash
pip install aiohttp
```

Then:

```py
import asyncio
from urllib.parse import quote

import aiohttp


async def get_tiktok_data(tiktok_url: str):
    endpoint = (
        "https://api.bliztik.web.id/apitiktok?url="
        + quote(tiktok_url, safe="")
    )

    timeout = aiohttp.ClientTimeout(total=15)

    async with aiohttp.ClientSession(timeout=timeout) as session:
        async with session.get(endpoint) as response:
            response.raise_for_status()
            return await response.json()


async def main():
    data = await get_tiktok_data(
        "https://www.tiktok.com/@username/video/1234567890123456789"
    )

    print(data)


if __name__ == "__main__":
    asyncio.run(main())
```

### PHP (cURL)

```php
<?php

$tiktokUrl = 'https://www.tiktok.com/@username/video/1234567890123456789';

$apiUrl = 'https://api.bliztik.web.id/apitiktok?url=' . rawurlencode($tiktokUrl);

$ch = curl_init($apiUrl);

curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_FOLLOWLOCATION => true,
    CURLOPT_TIMEOUT => 15,
    CURLOPT_HTTPHEADER => [
        'Accept: application/json',
    ],
]);

$response = curl_exec($ch);

if ($response === false) {
    throw new RuntimeException(curl_error($ch));
}

$statusCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);

curl_close($ch);

if ($statusCode < 200 || $statusCode >= 300) {
    throw new RuntimeException(
        "BlizTik API returned HTTP " . $statusCode
    );
}

$data = json_decode($response, true, 512, JSON_THROW_ON_ERROR);

print_r($data);
```

### HTML / Vanilla JavaScript (fetch)

Because the API supports CORS, it can be called directly from browser-based applications without requiring a custom backend proxy for the basic request flow.

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>BlizTik API Demo</title>
</head>
<body>
  <input
    id="tiktokUrl"
    type="url"
    placeholder="Paste TikTok URL"
  >

  <button id="downloadBtn" type="button">
    Fetch
  </button>

  <pre id="output"></pre>

  <script>
    const input = document.getElementById("tiktokUrl");
    const button = document.getElementById("downloadBtn");
    const output = document.getElementById("output");

    button.addEventListener("click", async () => {
      const tiktokUrl = input.value.trim();

      if (!tiktokUrl) {
        output.textContent = "Please enter a TikTok URL.";
        return;
      }

      button.disabled = true;
      output.textContent = "Loading...";

      try {
        const endpoint =
          "https://api.bliztik.web.id/apitiktok?url=" +
          encodeURIComponent(tiktokUrl);

        const response = await fetch(endpoint, {
          method: "GET",
          headers: {
            Accept: "application/json"
          },
          cache: "no-store"
        });

        const data = await response.json();

        if (!response.ok) {
          throw new Error(`HTTP ${response.status}`);
        }

        output.textContent = JSON.stringify(data, null, 2);
      } catch (error) {
        output.textContent = `Request failed: ${error.message}`;
      } finally {
        button.disabled = false;
      }
    });
  </script>
</body>
</html>
```

---

## 🗺️ Roadmap

BlizTik focuses on its core TikTok downloader API and the features documented above.

Future improvements will be announced in the repository as they are planned and implemented.

Have an idea for improving BlizTik? Open a feature request in the repository.

---

## ❓ FAQ

### Is BlizTik really unlimited?

The public endpoint has **no fixed daily quota published in this repository**. That does not mean unlimited traffic is guaranteed under every infrastructure or upstream condition.

Please use the service responsibly. Extremely high-volume or abusive traffic may still be affected by infrastructure protection, upstream availability, or operational changes.

### Why is the response so fast?

BlizTik is designed around a lightweight REST request flow and a direct media extraction pipeline. Under normal conditions, the project targets **sub-2-second responses**, but real latency can vary with network quality, redirects, TikTok availability, upstream extraction, and media complexity.

### Is BlizTik safe for production?

BlizTik can be integrated into production applications, but the public API should still be treated as an external service dependency.

For production workloads, handle HTTP errors, use reasonable timeouts, validate returned fields, monitor failures, and keep a fallback strategy for critical systems.

### What if the API is down?

Use standard HTTP failure handling and retry only when appropriate. For critical applications, consider a fallback architecture rather than relying on a single public endpoint.

Example:

```js
try {
  const response = await fetch(endpoint);

  if (!response.ok) {
    throw new Error(`HTTP ${response.status}`);
  }

  const data = await response.json();
  console.log(data);
} catch (error) {
  console.error("BlizTik unavailable:", error);
}
```

### Does BlizTik require an API key?

**No.** The public endpoint documented in this README does not require an API key or authentication header.

### Can I call BlizTik directly from a website?

**Yes.** CORS support allows browser-based applications to call the API directly using `fetch()`.

### Which TikTok URLs are supported?

The endpoint is designed for common public TikTok URLs, including standard video URLs and short links such as `vt.tiktok.com` and `vm.tiktok.com`.

### What does the API return?

A successful response uses the following top-level structure:

```json
{
  "status_code": 200,
  "message": "Parsing successful - Bliz",
  "data": {}
}
```

The `data` object contains media URLs, post metadata, author information, audio information, and additional fields depending on the TikTok post type.

### Does the API support photo posts?

**Yes.** Photo and slideshow results are represented through the `images` array, while video results include video and preview URLs.

### Does the API provide audio separately?

**Yes.** The response includes `audio_url` and a nested `music` object containing audio metadata and its downloadable `url`.

### Is there an SDK?

No SDK is required. Any language or framework capable of making an HTTPS GET request can integrate with the endpoint.

---

## 🤝 Contributing

Contributions are welcome! ❤️

If you find a bug, have an optimization idea, or want to add a feature, open an issue or pull request on the main repository.

### Contribution flow

```text
Fork → Create Branch → Make Changes → Test → Commit → Push → Pull Request
```

### 1. Fork the repository

https://github.com/BlizPS/bliztik-api/fork

### 2. Clone your fork

```bash
git clone https://github.com/BlizPS/bliztik-api.git
cd bliztik-api
```

### 3. Create a feature branch

```bash
git checkout -b feature/my-improvement
```

### 4. Make your changes

Keep changes focused, readable, and easy to review.

### 5. Test your changes

Verify that the API integration and affected files work as expected before opening a PR.

### 6. Commit your changes

```bash
git add .
git commit -m "feat: improve API integration"
```

### 7. Push your branch

```bash
git push origin feature/my-improvement
```

### 8. Open a Pull Request

Create a PR against the `main` branch and describe what changed, why it changed, and how it was tested.

For the latest project information and contribution discussion, use the repository home:

https://github.com/BlizPS/bliztik-api

---

## ⚠️ Disclaimer

**BlizTik API is an independent open-source project and is not affiliated with, endorsed by, sponsored by, or officially connected to TikTok or ByteDance.**

This project is provided for **educational, research, and developer integration purposes**.

You are responsible for how you use the API and any media or metadata returned by it. Make sure your use complies with applicable laws, platform rules, copyright requirements, privacy obligations, and the terms that apply to the content you access.

BlizTik does not grant you ownership or redistribution rights over third-party content.

---

## 📄 License

BlizTik API is released under the **MIT License**.

See the full license text in [`LICENSE`](LICENSE).

---

## ❤️ Credits

### Created by BlizPS

BlizTik API is developed and maintained by **BlizPS**.

- GitHub: https://github.com/BlizPS
- Repository: https://github.com/BlizPS/bliztik-api
- Website: https://bliztik.web.id
- Direct API Endpoint: https://api.bliztik.web.id/apitiktok?url=
- Test API: https://bliztik-api.vercel.app/

### Reporting Bugs

Found something broken?

Open an issue:

https://github.com/BlizPS/bliztik-api/issues/new

When reporting a bug, include the request format, HTTP status code, a sanitized response example, approximate time, and reproduction steps.

Never post private credentials, API tokens, cookies, or other sensitive information in an issue.

---

## ⭐ Support the Project

If BlizTik is useful to you, consider giving the repository a star:

https://github.com/BlizPS/bliztik-api

**Don't forget to ⭐ star this repo if you find it useful!**

---

<p align="center">
  <strong>BlizTik API</strong><br>
  Free · Fast · No API Key · Easy to Integrate
</p>
