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

## 5b. Live orders into a Google Sheet (recommended for demos)

When this is on, tapping **Create my message** also sends the order to a Google Form in the background. Each order becomes a new row in a Google Sheet, and the visitor sees "Order sent". The copy-and-send message stays as a backup.

1. Make a Google Form. Add these questions **in this order**, all as **Short answer** (use Paragraph for the last two): Order type, Name, Grade and section, Turon flavor, Ice cream flavor, Sauce, Number of orders, Payment method, Preferred break time, Notes, Estimated total.
2. In the form's **Responses** tab, click **Link to Sheets**.
3. Send the form's share link to whoever maintains the site. They fill in `ORDER_SUBMIT` (search for it in `index.html`) with the form address and each question's id.
4. Leave `ORDER_FORM_URL` empty so visitors use this site's form instead of the Google Form page.
5. Send one test order, then check the Sheet.

Notes: Google does not tell the page whether the row was saved, so "Order sent" means the browser delivered it. Always check the Sheet during a demo. To turn live orders off, set `formResponseUrl` back to `""`.

## 6. Good to know

- The page needs JavaScript for the menu lists, gallery, team, FAQ and photos. If JavaScript is blocked, visitors see a short note with the price and social handles.
- The page uses no cookies or browser storage. The only thing it sends anywhere is a submitted order, to your Google Form (see section 5b).
- Click-test both social links yourself: `@turondagowch` (Instagram) and `@turondagoat` (TikTok) were used exactly as given.
