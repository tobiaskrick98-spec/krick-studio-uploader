# Scope-Justification — copy/paste into Google submission form

Google will ask "Why does your app need each scope?" for the three YouTube scopes.
Paste these answers verbatim into the corresponding field in the OAuth consent
screen verification form.

---

## Scope: `https://www.googleapis.com/auth/youtube.upload`

**Justification:**

Krick Studio Uploader publishes the creator's own short-form videos as YouTube Shorts to the creator's own YouTube channel. This scope is the minimum permission required to call `videos.insert` with a media body, which is the only documented API path for uploading video content to YouTube. Without this scope, the app cannot perform its single core function. Uploads are limited to one video per calendar day, and only to the channel owned by the authenticated user.

**Demonstration:** the linked demo video shows the app reading a local `.mp4` from the curated upload queue, attaching the pre-prepared metadata (title, description, tags), and calling `videos.insert` to publish it as a YouTube Short.

---

## Scope: `https://www.googleapis.com/auth/youtube`

**Justification:**

Krick Studio Uploader needs to set metadata on the videos it uploads — specifically the title, description, tag list, category, `privacyStatus`, and `madeForKids` flag — at the moment of upload. These fields are part of the `videos.insert` request body and require this scope (the upload-only scope is not sufficient for setting all required metadata). The app does not modify videos created by other apps and does not delete videos. All edits are limited to the upload performed in the same API call.

**Demonstration:** the linked demo video shows the app passing a full `snippet` and `status` object (title, description, tags, categoryId, privacyStatus="public", madeForKids=false) to `videos.insert` as part of the upload request.

---

## Scope: `https://www.googleapis.com/auth/youtube.readonly`

**Justification:**

Krick Studio Uploader enforces a hard cap of "maximum one upload per calendar day" to protect channel cadence and avoid algorithmic penalties from over-posting. To enforce this cap reliably across restarts, the app needs to read the channel's recent upload history (`playlistItems.list` against the channel's uploads playlist) and check the most recent upload's `publishedAt` timestamp. If a video has already been published today, the app skips the run. This scope is read-only and is used exclusively for this cadence check — no other read operations are performed.

**Demonstration:** the linked demo video shows the app calling `channels.list?part=contentDetails&mine=true` to resolve the uploads playlist, then `playlistItems.list` to retrieve the latest item, and printing the daily-cap decision before deciding whether to upload.

---

## App description (the main "what does your app do" field)

> Krick Studio Uploader is a single-user content-distribution tool used by
> professional volleyball player and content creator Tobias Krick to publish
> his own short-form videos as YouTube Shorts on a predictable daily cadence.
> The creator curates a local upload queue with one video per slot, each with
> its own pre-prepared title, description, and tags. Once per day, the next
> highest-ranked video in the queue is uploaded to the creator's own YouTube
> channel via the YouTube Data API v3 `videos.insert` endpoint. The tool
> authenticates to exactly one Google account, uploads to exactly one channel,
> stores all credentials and queue state locally on a single private server,
> and does not share or transmit any data to third parties. A hard "max one
> upload per calendar day" cap is enforced via `playlistItems.list` against
> the channel's own uploads history.

---

## Authorized domains (under "App information")

```
github.io
```

(GitHub Pages serves the homepage, privacy policy, and terms pages.)
