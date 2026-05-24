# Demo-Video — Script + Drehanleitung

**Länge:** ~2-3 Minuten
**Upload:** auf @tobiaskrick als **Unlisted**, danach URL in Google-Submission einfügen
**Sprache:** Englisch (Google-Reviewer)
**Tonalität:** ruhig, technisch, kein Marketing-Spruch

---

## Was Google sehen will (das ist der ganze Reviewer-Filter)

1. Welche App ist das? (Name + Use-Case in 1 Satz)
2. OAuth-Consent-Screen mit App-Name, Scopes sichtbar
3. User klickt Allow → App führt die Action aus, die zu jedem Scope passt
4. Wo werden die Daten gespeichert (Stichwort „Limited Use")

---

## Screen-Recording-Setup (Mac):

- QuickTime → File → New Screen Recording → only record the terminal window + browser
- Audio: dein USB-Mic, kein Background-Musik
- Mauszeiger groß (System Settings → Accessibility → Display → Pointer size: medium)

---

## Voiceover-Script (englisch, sprich's so wie's hier steht)

> **[0:00 — screen shows the landing page https://tobiaskrick98-spec.github.io/krick-studio-uploader/]**
>
> Hi, this is the verification demo for Krick Studio Uploader.
>
> Krick Studio Uploader is a single-user content distribution tool I built
> for myself. I'm a professional volleyball player, and I publish short-form
> clips to my YouTube channel every day. This tool reads videos from a local
> upload queue on my server and posts one of them per day as a YouTube Short
> to my own channel.
>
> **[0:20 — scroll down the landing page to "Google account access" section]**
>
> The app needs three YouTube scopes. Let me show you each one being used.
>
> **[0:35 — switch to terminal, show `cat ~/obsidian-wiki/bin/tt2yt/queue.json | head` to display the local queue]**
>
> Here's my local upload queue on my private server. Each entry has a video
> file, a title, a description, and tags I prepared in advance.
>
> **[0:50 — show terminal running `python upload_next.py --dry-run`]**
>
> Now I'll trigger a dry run. The app first uses the youtube.readonly scope
> to check if I already uploaded something today.
>
> **[1:05 — show the dry-run output that lists "Would upload" + the title]**
>
> The cap is one upload per day. Today the queue is clean, so it would proceed.
>
> **[1:15 — clear screen, run the actual upload (or just continue the dry-run narration)]**
>
> When this runs for real at 6 PM UTC, it uses the youtube.upload scope to
> push the mp4 file, and the youtube scope to set the title, description,
> tags, category, and privacy status — all in the same videos.insert call.
>
> **[1:35 — switch to browser, show the OAuth consent screen from a fresh re-auth (use the headless setup_oauth.py URL)]**
>
> Here's the consent screen the user — me — sees when authorizing the app.
> The app name "Krick Studio Uploader" is shown, and the three scopes are
> listed explicitly: upload, manage account, and read-only metadata access.
>
> **[1:55 — click through, show the redirect URL gets written back, terminal confirms token.json was written]**
>
> After I approve, the token is stored locally in token.json on my own
> private server. No data leaves that server — there's no shared backend,
> no analytics, no third party. The privacy policy at the URL you can see
> in your verification form spells this out.
>
> **[2:15 — switch back to browser, show the channel page https://www.youtube.com/@tobiaskrick]**
>
> And here is the channel where the uploads land — my own channel,
> @tobiaskrick on YouTube. The same channel I'm uploading to is the same
> account that authorized the app. Single-user, single-channel, single-purpose.
>
> **[2:30 — end screen, show landing page again briefly]**
>
> That's the entire scope of the app. Thanks for reviewing.

---

## Screens-Reihenfolge (Bullet-Liste fürs Schneiden):

1. Landing page (full)
2. Landing page (scrolled to scopes section)
3. Terminal — `cat queue.json | head` oder `ls queue/`
4. Terminal — `python upload_next.py --dry-run`
5. Terminal — dry-run output highlight
6. Browser — OAuth consent screen (Google's confirmation dialog)
7. Terminal — token written
8. Browser — YT channel page
9. Landing page (closing shot)

---

## Pro-Tipp:

Mach das Video in **einem Take** wenn möglich. Reviewer hassen Schnitt-Wirrwarr und Zoom-Effekte. Cleaner Cursor-Move + ruhige Stimme = approve in <2 Tagen. Plus „Verification" rate ist deutlich höher wenn das Video schlicht und ehrlich wirkt.

Wenn du nervös bist: schreib das Script als Karteikarten neben den Monitor und lies's ab. Hört man eh nicht raus weil's technisch ist.
