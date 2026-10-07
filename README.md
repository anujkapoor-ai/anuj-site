# Anuj Kapoor — personal site

Two files make the site:

- `profile.json` holds all the content: every section, tile, date, story and image.
- `index.html` is the design. It reads `profile.json` and draws the tiles and panels.

To update the site, change `profile.json` only. Cloudflare Pages republishes within a minute or two of each change.

## Adding a section

Add an entry to `sections` with an `id`, a `tile`, a `panel` and its `blocks`. Tiles appear in the order listed. Tile `size` is `w4` (a third), `w6` (half) or `w12` (full width). Add `"wideTablet": true` to make a tile full width on tablets, and `"dark": true` for the dark style.

## Block types

| type | use |
| --- | --- |
| `lede` | a large opening line |
| `p` | a paragraph (`"muted": true` for grey text) |
| `chain` | a row of items joined by arrows |
| `rows` | dated entries: `when`, `title`, `text`, optional `tags` |
| `cards` | small cards: optional `label`, `title`, `text` |
| `groups` | headed groups of tags |
| `tags` | a list of tags |
| `list` | publications: `title`, `source`, optional `url`, `featured` |
| `media` | images and video, see below |

## Images and video

Put image files in `media/`. Then add them to a section:

```json
{ "type": "media", "items": [
  { "type": "image", "src": "media/london-stall-2016.webp", "caption": "London, 2016", "alt": "Market stall with handwoven shawls" },
  { "type": "video", "src": "https://…/clip.mp4", "caption": "From loom to market" },
  { "type": "youtube", "id": "VIDEO_ID", "caption": "Talk at …" }
] }
```

A tile can also carry a cover photo: add `"cover": "media/photo.webp"` to its `tile`.

Keep images under about 400 KB each (WebP or JPEG). Keep large videos out of this repository: use YouTube, or Cloudflare R2 and link to them.

## Draft marker

`"draft": "Draft · your words here"` on a section shows a draft dot on its tile and a note in its panel. Remove the line when the section is final.
