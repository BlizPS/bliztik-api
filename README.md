# BlizTik API

BlizTik API is a small HTTP API for getting TikTok media data in a format that is easy to use in other projects.

It is built for developers who want to handle TikTok links without writing the media-processing part themselves.

## What it supports

- TikTok video downloads
- No-watermark video when available
- TikTok photo and slideshow media
- Audio extraction when available
- Media metadata in JSON
- Simple HTTP requests
- CORS support
- Basic rate limiting and request protection

Media returned by the API can vary depending on the TikTok post and the result available at the time of the request.

## Quick example

Send a TikTok URL directly to the API:

```text
https://api.bliztik.web.id/apitiktok?url=YOUR_TIKTOK_URL
```

Using JavaScript:

```js
const url = "https://api.bliztik.web.id/apitiktok?url=" +
  encodeURIComponent(tiktokUrl);

const response = await fetch(url);
const data = await response.json();

console.log(data);
```

## Preview

These are individual examples of the API interface and returned media. They are kept separate so the README stays easy to read.

### API Request

![BlizTik API request](assets/blizTikApi-request.png)

### Video Result

![BlizTik API video result](assets/blizTikApi-video.png)

### TikTok Photo

![BlizTik API photo result](assets/blizTikApi-photo.png)

### Audio Result

![BlizTik API audio result](assets/blizTikApi-audio.png)

## Project Structure

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

The `assets` folder only contains images used by the documentation.

## Using the API

The API can be used from pretty much anything that can make an HTTP request:

- Websites
- Node.js projects
- Android apps
- Discord bots
- WhatsApp bots
- Other backend services

The basic flow is simple:

```text
TikTok URL
    ↓
BlizTik API
    ↓
Media processing
    ↓
JSON response
    ↓
Your application
```

## Supported Media

| Media | Availability |
| --- | --- |
| TikTok video | Available |
| No-watermark video | When available |
| TikTok photo / slideshow | Available |
| Audio / music | When available |

## Notes

The API does not guarantee that every TikTok post will return every media type. Private, removed, restricted, or otherwise unavailable posts may return an error or incomplete media data.

Keep requests reasonable and avoid repeatedly sending the same URL at high speed.

## Visit BlizTik

[Visit bliztik.web.id](https://bliztik.web.id)
