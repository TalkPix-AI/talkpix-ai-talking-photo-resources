---
layout: default
title: "Lip Sync a Photo to a WAV File: Step by Step (Size, Length and Cost)"
description: "How to prepare a WAV recording so a portrait lip-syncs cleanly: sample rate and size math for the 25 MB limit, an ffmpeg one-liner, the upload steps and a credit table."
permalink: /lip-sync-a-photo-to-a-wav-file/
---

A WAV file is the best thing you can hand a lip-sync model: no compression artefacts, crisp consonants, exact timing. It is also the format most likely to be rejected, because an uncompressed recording gets big fast. This guide covers what to check in the file before you upload it, how to shrink it without losing quality, and what the finished video costs.

*Disclosure: TalkPix is our product. The numbers below were read from its live pricing and lip-sync pages on 9 November 2026.*

<img src="{{ '/photo-lip-sync-wav-demo.gif' | relative_url }}" alt="A portrait photo lip-syncing to an uploaded voice recording" width="320">

## Why WAV files fail more often than MP3s

The upload limit for one audio clip is 25 MB. An MP3 at 128 kbps uses about 1 MB per minute, so it almost never hits that ceiling. A WAV file stores every sample, and its size depends only on three settings: sample rate, bit depth and channel count.

Size per second = sample rate × (bit depth ÷ 8) × channels.

| WAV settings | Bytes per second | Longest clip under 25 MB |
|---|---|---|
| 48 kHz, 24-bit, stereo (typical recorder or DAW export) | 288,000 | about 1 min 27 s |
| 44.1 kHz, 16-bit, stereo (CD quality) | 176,400 | about 2 min 21 s |
| 48 kHz, 16-bit, mono | 96,000 | about 4 min 20 s |
| 44.1 kHz, 16-bit, mono | 88,200 | about 4 min 43 s |
| 22.05 kHz, 16-bit, mono | 44,100 | over 9 min (the 5-minute video limit applies first) |

Speech is one voice from one place, so stereo only doubles the file. Converting to mono 16-bit is the single biggest saving and you will not hear the difference in a talking-head video.

## Step 1: Check the file you have

On a Mac, select the file and press Cmd+I; on Windows, right-click, Properties, Details. Note the length, the sample rate, the bit depth and whether it is stereo. If you have ffmpeg installed, one command shows all of it:

```bash
ffprobe -hide_banner your-recording.wav
```

## Step 2: Make it mono, 16-bit, and trim the silence

This one line converts the file to 44.1 kHz mono 16-bit and cuts silence from the start and the end:

```bash
ffmpeg -i your-recording.wav -ac 1 -ar 44100 -sample_fmt s16 -af "silenceremove=start_periods=1:start_threshold=-45dB,areverse,silenceremove=start_periods=1:start_threshold=-45dB,areverse" clean.wav
```

Trimming matters for two reasons. The portrait sits with a closed mouth through any leading silence, which looks like a frozen frame. And the video is billed by its rendered length, so three seconds of room tone at each end are six seconds you pay for.

If you edit in Audacity instead: Tracks, Mix, Mix Stereo Down to Mono; select the silence at each end and delete it; then File, Export, Export as WAV, with encoding "Signed 16-bit PCM".

## Step 3: Check the recording itself

The model follows what it hears, so these matter more than the file format:

1. **One speaker per clip.** Two voices make the mouth move for both.
2. **No music bed under the speech.** Export the voice track on its own.
3. **Peaks around -6 dB.** A clipped, distorted recording gives a jittery mouth.
4. **Natural pace.** Very fast speech is harder to track than a normal speaking rate.

## Step 4: Upload the photo and the WAV

1. Open the Talking Photo studio in audio mode. The direct route is the TalkPix guide to [make a face talk from a WAV file](https://www.talkpix.ai/photo-lip-sync), which has the "Lip-sync my photo" button.
2. Upload one clear portrait: one face, looking at the camera, mouth fully visible.
3. Upload `clean.wav`, or record straight in the browser instead.
4. Pick 720p or 1080p and read the credit estimate before you generate.
5. Generate, then watch the mouth timing on the first few words before downloading the MP4.

Your recording supplies the words, the language and the timing, so there is no voice to pick and no text-to-speech language to set.

## What it costs

Talking Photo bills the real rendered length, rounded up to a whole second: 1 credit per second at 720p, 2 credits per second at 1080p. A video can run up to 5 minutes at 720p or 2 minutes at 1080p.

| Clip length | 720p credits | 1080p credits | 720p on the $5 Mini pack (50 credits) | 720p on the $10 Starter pack (120 credits) |
|---|---|---|---|---|
| 10 s | 10 | 20 | $1.00 | $0.83 |
| 30 s | 30 | 60 | $3.00 | $2.50 |
| 60 s | 60 | 120 | over the pack | $5.00 |
| 2 min | 120 | 240 | over the pack | $10.00 |

Packs are one-time purchases and the credits do not expire. Current packs and rates are on the [TalkPix pricing page](https://www.talkpix.ai/pricing).

## Quick checklist

- [ ] Under 25 MB (mono 16-bit gets you to about 4.5 minutes)
- [ ] Silence trimmed at both ends
- [ ] One voice, no music
- [ ] Under 5 minutes for 720p, under 2 minutes for 1080p
- [ ] You have permission to use both the photo and the voice

Other accepted formats are MP3, M4A, AAC, OGG, WebM and FLAC. If your WAV will not fit even as mono, FLAC keeps the same quality at roughly half the size.
