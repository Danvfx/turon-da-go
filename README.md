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

- **Prices:** search `const PRICE` (box), `BISCOFF_UPCHARGE`, `EXTRA_DRIZZLE`, `EXTRA_TOPPING`. Change a number once and every place updates (hero sticker, pricing, FAQ, builder and order totals).
- **Flavors:** search `const FLAVORS`. Add a line to the `turon`, `drizzle` or `topping` list (copy a line, change `id`, `name`, `color`; `form` must match the Google Form option).
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

## 5b. Live orders into a Google Sheet

Pressing **Create my order** also sends the order to your Google Form in the background. Each order becomes a new row in the form's Google Sheet, and the visitor sees "Order sent". The copy-and-send message stays as a backup. Inquiries are message-only and are not sent to the Sheet.

Rules for the Google Form (otherwise orders are silently lost):

1. **No file-upload question.** A file-upload question forces every respondent to sign in to Google, which blocks the site from posting. GCash customers type their receipt's reference number into a normal text question ("Reference No.") instead.
2. **Do not turn on "Limit to 1 response", "Collect email addresses", or "Restrict to users in your organization".** Each one needs a sign-in or extra data the site does not send.
3. **Option text must match exactly.** The drizzle, topping and flavor names in the form must match the `FLAVORS` list in `index.html` (for example `Biscoff ( +₱10.00 )`). If you rename an option in the form, rename it in `FLAVORS` too.
4. **Pages.** The form has 10 pages. The site tells Google which pages were visited (`ORDER_SUBMIT.pages`). If you add, remove or reorder pages or questions, update `ORDER_SUBMIT`.

To switch to a different form later: open its public link, read each question's `entry.NNN` id (Google Forms > pre-filled link shows them), and fill in `ORDER_SUBMIT` in `index.html`. Leave `ORDER_FORM_URL` empty so visitors use this site's form.

Google does not tell the page whether the row was saved, so "Order sent" means the browser delivered it. Always check the Sheet during a demo. To turn live orders off, set `formResponseUrl` back to `""`.

## 6. Good to know

- The page needs JavaScript for the menu lists, gallery, team, FAQ and photos. If JavaScript is blocked, visitors see a short note with the price and social handles.
- The page uses no cookies or browser storage. The only thing it sends anywhere is a submitted order, to your Google Form (see section 5b).
- Click-test both social links yourself: `@turondagowch` (Instagram) and `@turondagoat` (TikTok) were used exactly as given.
