# video-prompt-schema

An open **JSON Schema** for structured AI video prompts — the fields that models like **Sora 2** and **Seedance 2.0** respond to most reliably: `subject`, `action`, `environment`, `camera`, `duration`, `look`, and `negative`.

Structured prompts beat one long run-on sentence because each attribute is unambiguous — the model doesn't have to guess whether "slow" describes the car or the camera.

> Don't want to write JSON by hand? Use the free builder — fill a form, copy the JSON: **[Sora 2 & Seedance JSON Prompt Builder](https://sora-json-prompt-builder.dolphinstudio101.workers.dev/)**

## The schema

See [`video-prompt.schema.json`](./video-prompt.schema.json) (JSON Schema draft-07).

### Example prompt

```json
{
  "model": "sora2",
  "subject": "a red vintage sports car",
  "action": "speeding along a coastal highway",
  "environment": "golden-hour, cliffs and ocean on the right",
  "camera": { "shot_size": "wide shot", "motion": "tracking shot following the subject" },
  "duration_seconds": 8,
  "aspect_ratio": "16:9",
  "look": { "style": "cinematic, 35mm film grain, shallow depth of field", "lighting": "warm backlight, long shadows" },
  "negative": "no text, no logos, no warping, no extra limbs"
}
```

## The 6-part formula behind it

| # | Slot | Why |
|---|---|---|
| 1 | subject | the one thing the model must get right — put it first |
| 2 | action | motion is what separates video from a still |
| 3 | environment | grounds the subject, stabilizes the background |
| 4 | camera | shot size + motion — where "cinematic" comes from |
| 5 | look | style, lens, lighting, mood |
| 6 | negative | fence off text, logos, warping, extra limbs |

## Validate a prompt

```bash
npx ajv-cli validate -s video-prompt.schema.json -d my-prompt.json
```

## Notes

Not affiliated with OpenAI (Sora) or ByteDance (Seedance); product and model names are trademarks of their respective owners. Models change their accepted inputs over time — treat this as a convention, not a guarantee.

## License

MIT © Dolphin Studio LLC
