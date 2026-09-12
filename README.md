# BlizTik API

> **A fast, free, no-API-key TikTok downloader API for developers — video, photo, audio, and metadata in one simple request.**

[![MIT License](https://img.shields.io/github/license/BlizPS/bliztik-api?style=flat-square)](https://github.com/BlizPS/bliztik-api/blob/main/LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/BlizPS/bliztik-api?style=flat-square)](https://github.com/BlizPS/bliztik-api/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/BlizPS/bliztik-api?style=flat-square)](https://github.com/BlizPS/bliztik-api/network/members)
[![Version](https://img.shields.io/badge/version-1.0.0-blue?style=flat-square)](https://github.com/BlizPS/bliztik-api)
[![API Status](https://img.shields.io/website?url=https%3A%2F%2Fapi.bliztik.web.id&style=flat-square)](https://api.bliztik.web.id)
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

**BlizTik API** is an open-source REST API for extracting useful media data from public TikTok URLs. It is designed for developers who want a straightforward way to turn a TikTok link into structured JSON without building the entire extraction pipeline themselves.

The API can handle common TikTok media types, including **videos, no-watermark video URLs, photos/slideshows, audio, and post metadata**. The service is intended to be easy to integrate into websites, backend services, bots, mobile applications, and other developer tools. 🌐

BlizTik was created around a simple idea: **developers should be able to test and build quickly without unnecessary API-key setup, complicated SDKs, or platform-specific integration overhead.**

> Built for developers. Simple for users. Fast to integrate.

---

## ✨ Why BlizTik?

Here are the main reasons developers choose BlizTik API:

- 🆓 **100% Free** — no subscription is required to make requests.
- 🔑 **No API Key** — call the endpoint directly; no account key or authentication header is required for the public endpoint.
- 🚀 **Super Fast** — designed for low-latency processing, with typical responses targeting **under 2 seconds** depending on TikTok availability, network conditions, and media complexity.
- ♾️ **No Imposed Rate Limit** — the public API is designed without a documented per-user request quota. Please still use reasonable traffic and avoid abusive request patterns.
- 🎬 **HD Video Support** — retrieve high-quality HD video media.
- 🧼 **No-Watermark Video** — supports no-watermark video URLs.
- 📸 **Photo & Slideshow Support** — works with TikTok photo posts and multi-image slideshows.
- 🎵 **Audio Support** — retrieve audio/music information and media URLs.
- 👤 **Metadata Support** — access useful post and author metadata returned by the extractor.
- 🌐 **CORS Support** — suitable for direct browser-side requests from web apps.
- 🧩 **REST API** — no official SDK is required; use standard HTTP clients.
- 📱 **Cross-Platform** — works with frontend apps, Node.js, Python, PHP, bots, Android apps, and backend services.
- 🛠️ **Open Source** — inspect, fork, improve, and build on top of the project.

## 📊 BlizTik Highlights

BlizTik is focused on keeping the developer experience simple: one endpoint, no API key, and a response designed for easy integration.

| Feature | BlizTik |
| :--- | :---: |
| **API Key** | ❌ Not required |
| **Rate Limit** | ♾️ No fixed public quota published |
| **Speed** | ⚡ Target response under 2s* |
| **HD Video** | ✅ Supported |
| **No Watermark** | ✅ Supported |
| **Photo / Slideshow** | ✅ Supported |
| **Audio** | ✅ Supported |
| **Metadata** | ✅ Supported |
| **CORS** | ✅ Supported |
| **Price** | 🆓 Free |
| **Open Source** | ✅ Yes |

> *Actual response time can vary depending on TikTok availability, network conditions, redirects, upstream extraction, and media complexity.

---

## ⚡ Quick Start

The public endpoint accepts a TikTok URL through the `url` query parameter.

### cURL

```bash
curl "https://api.bliztik.web.id/apitiktok?url=https%3A%2F%2Fwww.tiktok.com%2F%40username%2Fvideo%2F1234567890123456789"
```

You can also let your shell handle a URL with `--get` and `--data-urlencode`:

```bash
curl --get "https://api.bliztik.web.id/apitiktok" \
  --data-urlencode "url=https://www.tiktok.com/@username/video/1234567890123456789"
```

### JavaScript (fetch)

```js
const tiktokUrl = "https://www.tiktok.com/@username/video/1234567890123456789";

const response = await fetch(
  "https://api.bliztik.web.id/apitiktok?url=" +
  encodeURIComponent(tiktokUrl)
);

const data = await response.json();

console.log(data);
```

### Python (requests)

```py
import requests

tiktok_url = "https://www.tiktok.com/@username/video/1234567890123456789"

response = requests.get(
    "https://api.bliztik.web.id/apitiktok",
    params={"url": tiktok_url},
    timeout=15,
)

response.raise_for_status()
data = response.json()

print(data)
```

---

## 📖 Documentation Endpoint

### Endpoint

| Property | Value |
| :--- | :--- |
| **Method** | `GET` |
| **URL** | `https://api.bliztik.web.id/apitiktok?url={TIKTOK_URL}` |
| **Content-Type** | `application/json` |
| **Authentication** | None |
| **Parameter** | `url` (required) |
| **Input** | Public TikTok URL |
| **Output** | JSON |
| **CORS** | Supported for browser-based integrations |

The endpoint is intended to accept common public TikTok URL formats, including:

- `https://www.tiktok.com/@username/video/...`
- `https://vt.tiktok.com/...`
- `https://vm.tiktok.com/...`

Short links may redirect before the media is resolved.

### Parameters

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `url` | `string` | ✅ | A public TikTok video, photo, or slideshow URL. |

### Example Request

```bash
curl --get "https://api.bliztik.web.id/apitiktok" \
  --data-urlencode "url=https://www.tiktok.com/@username/video/1234567890123456789"
```

### Response

A successful request returns a JSON object containing media URLs and metadata relevant to the TikTok post.

The exact field set can vary by post type. A **video post**, **photo slideshow**, and **audio-only result** do not necessarily return identical media fields.

Conceptually, a successful response may look like this:

```json
{
  "video": "https://example.com/video.mp4",
  "no_watermark_url": "https://example.com/video-no-watermark.mp4",
  "audio_url": "https://example.com/audio.mp3",
  "images": [],
  "author": {
    "username": "example"
  },
  "title": "Example TikTok post",
  "quality": "HD",
  "width": 1080,
  "height": 1920
}
```

> The example above is **illustrative**. Field presence, nesting, naming, and media URLs may vary depending on the TikTok post and the upstream extractor.

---

## 🧾 Full Response Example

This example shows the kinds of values an application can consume after a successful video response.

```json
{
  "video": "https://cdn.example.com/video.mp4",
  "no_watermark_url": "https://cdn.example.com/video-no-watermark.mp4",
  "audio_url": "https://cdn.example.com/audio.mp3",
  "images": [],
  "author": {
    "username": "example_user",
    "nickname": "Example User"
  },
  "title": "Example TikTok caption",
  "quality": "HD",
  "width": 1080,
  "height": 1920
}
```

### Field reference

| Field | Type | Description |
| :--- | :--- | :--- |
| `video` | `string \| null` | Video media URL. |
| `no_watermark_url` | `string \| null` | No-watermark video URL. |
| `audio_url` | `string \| null` | Audio/music media URL. |
| `images` | `array` | Image URLs for photo/slideshow posts. May be empty for video posts. |
| `author` | `object \| null` | Author metadata returned by the extractor. |
| `author.username` | `string \| null` | TikTok username/handle. |
| `author.nickname` | `string \| null` | Display name. |
| `title` | `string \| null` | Post caption/title text. |
| `quality` | `string \| null` | Reported media quality. |
| `width` | `number \| null` | Media width in pixels. |
| `height` | `number \| null` | Media height in pixels. |

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
  const response = await axios.get(
    "https://api.bliztik.web.id/apitiktok",
    {
      params: {
        url: tiktokUrl
      },
      timeout: 15000
    }
  );

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
import aiohttp


API_URL = "https://api.bliztik.web.id/apitiktok"


async def get_tiktok_data(tiktok_url: str):
    params = {"url": tiktok_url}

    timeout = aiohttp.ClientTimeout(total=15)

    async with aiohttp.ClientSession(timeout=timeout) as session:
        async with session.get(API_URL, params=params) as response:
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

$apiUrl = 'https://api.bliztik.web.id/apitiktok?' . http_build_query([
    'url' => $tiktokUrl,
]);

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

Because the API supports CORS, it can be called directly from browser-based applications without requiring your own backend proxy for the basic request flow.

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
        const requestUrl =
          "https://api.bliztik.web.id/apitiktok?url=" +
          encodeURIComponent(tiktokUrl);

        const response = await fetch(requestUrl, {
          method: "GET",
          headers: {
            "Accept": "application/json"
          },
          cache: "no-store"
        });

        const data = await response.json();

        if (!response.ok) {
          throw new Error(
            `HTTP ${response.status}`
          );
        }

        output.textContent = JSON.stringify(data, null, 2);
      } catch (error) {
        output.textContent =
          `Request failed: ${error.message}`;
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

The roadmap may evolve as the project grows.

- [x] Public TikTok downloader endpoint
- [x] No API key for the public endpoint
- [x] Video support
- [x] No-watermark video support
- [x] Photo / slideshow support
- [x] Audio support
- [x] Metadata support
- [x] CORS support
- [ ] 🔎 TikTok search
- [ ] 📈 Trending content endpoint
- [ ] 👤 User profile / user info endpoint
- [ ] 🎞️ More media quality metadata
- [ ] 🧰 More developer utilities
- [ ] 📘 Expanded API documentation
- [ ] 🧪 Automated integration tests
- [ ] 📊 Public service health / metrics page

Have an idea that would make the API better? Open a feature request in the repository.

---

## ❓ FAQ

### Is BlizTik really unlimited?

The public API does **not publish a fixed daily quota or per-user rate limit** in this project. That is different from promising that unlimited traffic is guaranteed under every circumstance.

Normal and responsible use is expected. Very high-volume, abusive, automated, or infrastructure-heavy traffic may still be affected by upstream provider limits, infrastructure protection, or operational changes.

### Why is the response so fast?

BlizTik is designed around a lightweight REST request flow and a small integration surface. In normal conditions, the project targets **sub-2-second response times**, but actual latency depends on DNS, network quality, TikTok availability, redirects, upstream extraction, and media complexity.

A sub-2-second figure should therefore be understood as a **performance target**, not a universal SLA.

### Is BlizTik safe for production?

It can be used as part of a production application, but treat the public API as an external dependency.

For production workloads, you should:

- Handle non-200 HTTP responses.
- Add request timeouts.
- Validate the JSON response before using a field.
- Cache repeated requests when appropriate.
- Monitor failures and latency.
- Keep a fallback strategy for critical applications.
- Respect applicable third-party platform policies and content rights.

Do not build a business-critical system around the assumption that any free public endpoint will provide an unconditional SLA.

### What if the API is down?

Use normal HTTP failure handling in your application.

Recommended production behavior:

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

For higher availability requirements, consider adding a fallback provider or your own extraction service.

### Does BlizTik have a Terms of Service?

Use of the API should be responsible and lawful. You are responsible for ensuring that your application, your use of returned media, and your handling of third-party content comply with applicable laws, TikTok's terms, and any other policies relevant to your project.

Because policies can change, review the current policies before deploying a commercial or high-volume integration.

### Does the API require an API key?

**No.**

The public endpoint documented in this README is designed to be called without an API key.

### Can I use BlizTik directly from a website?

**Yes.**

CORS support is intended to make browser-based `fetch()` requests possible without requiring a custom backend proxy for the basic integration.

### Does it support `vt.tiktok.com` and `vm.tiktok.com` links?

The endpoint accepts common public TikTok share URLs, including short-link formats such as `vt.tiktok.com` and `vm.tiktok.com`.

Short links may redirect before the media is resolved.

### Is there an SDK?

There is no SDK requirement.

Any language or framework capable of making an HTTPS `GET` request can integrate with the endpoint.

### Can I use it for a bot?

Yes. BlizTik can be integrated into:

- Telegram bots
- WhatsApp bots
- Discord bots
- Webhook systems
- CLI tools
- Backend services
- Mobile applications

Always account for your own platform's bot rules and the volume of requests generated by your users.

---

## 🤝 Contributing

Contributions are welcome! ❤️

If you find a bug, have an optimization idea, or want to add a feature, please open an issue or pull request.

### Contribution flow

```text
Fork → Create Branch → Make Changes → Test → Commit → Push → Pull Request
```

### 1. Fork the repository

Open the GitHub repository and create your own fork:

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

Verify that the API integration or affected files work as expected before opening a PR.

### 6. Commit

```bash
git add .
git commit -m "feat: improve API integration"
```

### 7. Push

```bash
git push origin feature/my-improvement
```

### 8. Open a Pull Request

Create a PR against the `main` branch and describe:

- What changed
- Why it changed
- How it was tested
- Any limitations or follow-up work

For the latest project context and contribution discussion, visit the repository home:

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

In short, the MIT License permits use, modification, distribution, and private or commercial use, subject to the license conditions.

---

## ❤️ Credits

### Created by BlizPS

BlizTik API is developed and maintained by **BlizPS**.

- GitHub: https://github.com/BlizPS
- Repository: https://github.com/BlizPS/bliztik-api
- Website: https://bliztik.web.id
- Direct API Endpoint: https://api.bliztik.web.id/apitiktok?url=
- Test API: https://bliztik-api.vercel.app/

### Reporting bugs

Found something broken?

Open an issue:

https://github.com/BlizPS/bliztik-api/issues/new

Useful bug reports should include:

- The endpoint you called
- The request format
- The HTTP status code
- A sanitized response example
- The approximate time of the problem
- Steps to reproduce

Never post private credentials, API tokens, cookies, or other sensitive information in an issue.

---

## ⭐ Support the Project

BlizTik is built for developers who want a simple API that just gets the job done.

If this project is useful to you, consider giving the repository a star:

https://github.com/BlizPS/bliztik-api

**Don't forget to ⭐ star this repo if you find it useful!**

---

<p align="center">
  <strong>BlizTik API</strong><br>
  Free · Fast · No API Key · Developer Friendly
</p>
