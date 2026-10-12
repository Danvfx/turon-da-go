# Turon-Da-Go website: how to use it

Three files:

| File | What it is |
|---|---|
| `index.html` | **The website.** The only file you paste into Google Sites. |
| `embed-test.html` | A local test page. Never paste this. |
| `README.md` | This guide. |

## 1. Put it on Google Sites

1. Open `index.html` in Notepad (or any text editor). Select all (Ctrl+A) and copy (Ctrl+C).
2. In Google Sites, open your site in the editor.
3. Click **Insert** (right-hand panel) > **Embed** > **Embed code** tab.
4. Paste the whole file into the box, then click **Next** > **Insert**.
5. Drag the corners of the embed so it fills the page width, and make it tall (try 800 to 1000 px, or taller).
   Try the full-width / full-page option for the embed if your Sites version shows one (I am not sure of the exact wording).
6. Click **Publish**, then open the live link on your phone and your laptop.

If Sites says the code is too large, tell me. The file is about 250 KB, mostly three small embedded images.

## 2. Test it before pasting

Double-click `embed-test.html`. It loads the site inside a locked-down frame (like Google Sites does) at 360, 768, 1280 px and 600, 800, 1000 px heights.

For the closest match to Google Sites, click **Pasted code (srcdoc)** and choose `index.html`.

Check: menu links scroll, the Order form builds a message, Instagram and TikTok open in a new tab.

## 3. Change things (open `index.html`, search for the word in quotes)

All editable data is in the second `<script>` block, under **SITE CONFIG**.

- **Price:** search `const PRICE`. Change the number once and every place updates (hero sticker, pricing, FAQ, order total).
- **Flavors:** search `const FLAVORS`. Add a line to the `ice` list for a new ice cream flavor (copy a line, change `id`, `name`, `color`).
- **Team:** search `const TEAM`. Add a photo by pasting an image link into `photo`.
- **FAQ:** search `const FAQ`.
- **Social links:** search `const SOCIAL`.
- **Anything unfinished:** search `TODO` or `ASSUMPTION`.

## 4. Swap images

At the top of the last-but-one script (search `IMAGE CONFIG`) there is a list called `IMAGES`.

- Leave a value as `""` and a drawn placeholder shows.
- Paste a **public HTTPS image link** between the quotes to use a photo. Use a public image host. Google Drive share links often fail inside embeds.
- Small photos can also be pasted as base64 data (`data:image/webp;base64,...`). Keep each under about 100 KB.

Only use photos you took or have permission to use.

## 5. Order options

- **Default (no setup):** visitors fill the form, the site writes a ready-made message with the estimated total, they copy it and send it to your Instagram or TikTok.
- **Google Form upgrade:** make a Google Form, click Send > link, and paste the link into `const ORDER_FORM_URL = "";`. Every Order button then opens your form in a new tab, and answers land in a Google Sheet.

## 6. Good to know

- The page needs JavaScript for the menu lists, gallery, team, FAQ and photos. If JavaScript is blocked, visitors see a short note with the price and social handles.
- Nothing is saved or sent anywhere by the page. No cookies or storage.
- Click-test both social links yourself: `@turondagowch` (Instagram) and `@turondagoat` (TikTok) were used exactly as given.
