# TalkPix — AI talking photo resources

[TalkPix](https://www.talkpix.ai) turns one portrait and a short script (or an audio clip) into a lip-synced MP4 video in the browser. This repository collects the practical material we point people to: a photo checklist, copy-and-edit scripts, a developer API quick start and the current product facts.

![A portrait photo lip-syncing to a voice recording, made with TalkPix](photo-lip-sync-wav-demo.gif)

## Contents

- [Product facts](#product-facts)
- [Photo checklist for clean lip sync](#photo-checklist-for-clean-lip-sync)
- [Script templates](#script-templates)
- [Guides by use case](#guides-by-use-case)
- [AI video trend guides](#ai-video-trend-guides)
- [Developer API quick start](#developer-api-quick-start)
- [Responsible use](#responsible-use)

## Product facts

| | |
|---|---|
| Input | A portrait photo plus typed text, an uploaded audio file or a recording |
| Output | Downloadable MP4, 720p or 1080p |
| Length | Up to 5 minutes per talking photo |
| Voices | 30 voices across 10 languages |
| First video | $1.99 one-time for new customers — typed script, up to 20 seconds, 720p |
| After that | One-time credit packs from $5; purchased credits never expire; no subscription required |
| Platform | Web app in the browser; iPhone and iPad app on the App Store |

Current packs and rates: [talkpix.ai/pricing](https://www.talkpix.ai/pricing)

## Photo checklist for clean lip sync

The model animates the mouth it can see, so most weak results trace back to the photo rather than the script.

1. **One face, facing the camera.** A slight angle is fine; a side profile is not.
2. **The whole mouth is visible.** No hand, microphone, scarf or paw over the lips.
3. **The face fills a good part of the frame.** A small face in a group or landscape shot gives a stiff, barely moving mouth.
4. **Even light on the face.** A hard shadow across the mouth reads as a closed mouth.
5. **Old photos:** crop to the person, straighten the scan and use the sharpest copy you have. Scratches away from the face don't matter.
6. **Pets:** a close-up with the muzzle pointed at the lens, head upright, mouth slightly open. Lying poses with the chin on the paws barely move.

## Script templates

People speak roughly 2 to 2.5 words per second, so a 20-second video fits about 45–50 words. Write the way the person would actually talk: short sentences, contractions, one idea per line.

**Birthday**

```text
Happy birthday, [name]! I can't believe another year went by already.
I hope today is loud, messy and full of cake. I'm so proud of you. See you soon!
```

**Old family photo**

```text
Hello, [name]. This picture was taken in [year], in [place].
I'd love for you to know how much this family meant to me. Keep the stories going.
```

**Pet**

```text
Listen, human. The bowl is half empty, which means it is completely empty.
Also, I love you. But mostly the bowl.
```

**Small shop**

```text
Hi, I'm [name] from [shop]. Every [product] is made by hand in [city].
Order before Friday and it ships the same week.
```

For another language, type the script in that language and choose a voice for it.

## Guides by use case

- Bring an old family portrait to life: [make old photos talk](https://www.talkpix.ai/make-old-photos-talk)
- Give your dog or cat a voice: [talking pet videos](https://www.talkpix.ai/talking-pet-video)
- A birthday message from a photo: [AI birthday video maker](https://www.talkpix.ai/ai-birthday-video-maker)
- A tribute for a funeral or anniversary: [memorial tribute videos](https://www.talkpix.ai/memorial-tribute-video)
- Sync a photo to audio you already have: [photo lip sync](https://www.talkpix.ai/photo-lip-sync)
- One face, several languages: [multilingual avatar videos](https://www.talkpix.ai/multilingual-avatar)
- Speak in your own cloned voice: [AI voice cloning](https://www.talkpix.ai/ai-voice-cloning)
- See real renders first: [example videos](https://www.talkpix.ai/ai-video-examples)

## AI video trend guides

Trend templates turn one or two photos into a ready-made scene: a dance, a movie moment, a trip to space. Each guide below shows real renders and what every template needs and costs.

- [AI couple video ideas from two photos](https://talkpix-ai.github.io/talkpix-ai-talking-photo-resources/ai-couple-video-ideas/): a slow dance in the rain, a rain kiss, a tap duet, a dance lift, Christmas cue cards and a pottery wheel.
- [All AI video trend templates](https://www.talkpix.ai/trends), each with its own example and price.

## Developer API quick start

Renders can also be started from your server with the REST API. Create a key in your TalkPix account; API renders use the same credit wallet and rates as the web app, and credits are reserved before each render.

```bash
curl https://www.talkpix.ai/api/v1/videos \
  -H "Authorization: Bearer tpx_live_..." \
  -H "Content-Type: application/json" \
  -d '{
    "image_url": "https://example.com/portrait.jpg",
    "script": "Hi! This video was made with one API call.",
    "voice": "zephyr",
    "language": "en-US",
    "webhook_url": "https://example.com/hooks/talkpix"
  }'
```

Poll `GET /api/v1/videos/{id}` or wait for the webhook, then download `video_url`. Keep the key on your server, never in a browser or mobile app. Full reference: [talkpix.ai/developers](https://www.talkpix.ai/developers)

## Responsible use

Only animate photos you have the right to use, with consent from the people in them (or their family, for someone who has passed away). Don't pass a generated clip off as a real recording of someone. Full rules: [Terms](https://www.talkpix.ai/terms)

## Further reading

- [How to write a funny talking-pet script](https://talkpixaiweb.substack.com/p/how-to-write-a-funny-talking-pet)
- [5 short birthday video message scripts](https://talkpixaiweb.substack.com/p/5-short-birthday-video-message-scripts)
- [What a memorial video should cost](https://talkpixaiweb.substack.com/p/what-a-memorial-video-should-cost)


## Links

- Website: https://www.talkpix.ai
- FAQ: https://www.talkpix.ai/faq
- Wikidata: https://www.wikidata.org/wiki/Q141254701
- Support: support@talkpix.ai
