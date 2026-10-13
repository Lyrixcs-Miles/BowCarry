# BowCarry

Product page for The Complete Set: a 1200ml insulated flask with a daisy strap, pom-pom charm and straw lid, R299.

It's one HTML file with the CSS and JS inline. No build step, no dependencies. Open `index.html` in a browser to preview it.

**Not ready to launch.** The page still has placeholder text and claims I haven't confirmed. Everything that needs sorting is listed under [To do before launch](#to-do-before-launch).

## What's here

- `index.html` - the page
- `resources/imgs/` - product images as WebP, named `colour-view.webp` with a `-thumb` version of each
- `CNAME` - custom domain for GitHub Pages, `bowcarry.azhyre.co.za`

## Notes on the page

Things that aren't obvious from reading the markup:

**Stock count is manual.** The number lives in `#stock-count` in the buy box, and again in the "Only 10 sets left" sticker on the image. Change both after every sale. They don't update themselves.

**Gallery.** The swatches pick the colour (pink or black) and the three thumbnails pick the view: the set on the flask, every piece laid out, and the flask alone. The image path is built from those two, so adding a colour means adding `colour-set`, `colour-set-contents` and `colour-flask` images plus a swatch button. The images are renders, not photos, and the caption under the main image says so.

**Buy button.** The Shopify Buy Button renders into `#product-component-1791693860750`. Until it loads, a plain "Buy now" link (`#buy-fallback`) shows instead, and it gets hidden about 3 seconds in if the Shopify button is there. The button won't render at all until there's a real product ID.

**Tracking waits for consent.** GA4 and Meta Pixel only load after someone clicks Accept on the cookie banner. The answer is saved in `localStorage` as `tracking-consent`. Only a page view and a product view are sent. Checkout and purchase events aren't set up yet and will need Shopify's order events.

**Signup form.** It validates the email and the consent tick box. While the form action is still a placeholder it shows "Sign-up is not connected yet." rather than pretending the signup worked.

**Reviews.** The slider works but every quote in it is a placeholder.

## Placeholders

Anything in `[SQUARE BRACKETS]` in `index.html` is a placeholder. Search for `[` to find them all.

Links and contact:

- `[PAGE URL]` - final page address, used in the product structured data
- `[EMAIL]`, `[TERMS URL]`, `[PRIVACY URL]`, `[FULL POLICY URL]`
- `[TIKTOK HANDLE]`, `[INSTAGRAM HANDLE]`, `[FACEBOOK PAGE]`, `[PINTEREST HANDLE]`

Shop and tracking:

- `[NEW PRODUCT ID]` - Shopify product ID for the Buy Button
- `[CHECKOUT LINK]` - fallback link, point it at the Shopify product page
- `G-XXXXXXXXXX` - GA4 measurement ID
- `PIXEL_ID` - Meta Pixel ID
- `[GOOGLE VERIFICATION CODE]`, `[META VERIFICATION CODE]`
- `[MAILING LIST FORM URL]` - where the signup form posts to

Product facts, to get from the supplier in writing:

- `[AMOUNT]` - free delivery threshold
- `[X]` - working days to ship
- `[LOCATION]` - where orders ship from
- `[CONFIRM]`, `[CONFIRM WITH SUPPLIER]` - material, insulation, dimensions, return postage, what photos a return needs
- `[CONFIRM AFTER SHOP TEST]` - hold time and leak-proof. Test these myself before saying them.
- `[CONFIRM REAL COLOURWAYS BEFORE LAUNCH]`

Claims that have to be true or come out:

- `[RATING]`, `[N]`, `[Real review quote]`, `[Customer first name]`, `[city]` - take the whole reviews section out until there are real reviews. No made-up quotes or names.
- `[TRENDING: keep only if true]`
- `[ORIGINAL PRICE]`, `[%]` - the crossed-out price and saving. Only keep them if there's a genuine discount.
- `[PAYFLEX / PROVIDER]` - the pay-later line. Only keep it once a provider is signed up.
- The "10 of 10 sets left" stock line has to match what's actually on the shelf.

## To do before launch

1. Trademark check on the BowCarry name (CIPC search, cipc.gov.za).
2. Count stock: complete sets per colour, and whether I'm holding flasks or just the accessories.
3. Create the Shopify product with colour variants, add the Buy Button channel, and put the product ID in the page.
4. Get delivery time, free delivery threshold, return postage and insulation claims from the supplier in writing.
5. Replace the renders with real photos of the stock, and make sure the pieces shown match what's actually in the box. Then drop the "Product render" caption.
6. Add the GA4 ID, Meta Pixel ID and both verification codes.
7. Connect a mailing list with double opt-in and set the form URL.
8. Get the cookie wording and returns policy checked against the CPA and POPIA.
9. Test on a phone and a desktop, Chrome and Safari.

## Hosting

The site is set up for GitHub Pages on `bowcarry.azhyre.co.za`.

- Pages: Settings > Pages > deploy from `main`, folder `/`.
- Pages on a private repo needs a paid GitHub plan. On the free plan the repo has to be public, or the page has to be hosted somewhere else.
- DNS: a CNAME record at GoDaddy with name `bowcarry` and value `lyrixcs-miles.github.io`.
- Add the TXT record GitHub provides to verify the domain, then turn on Enforce HTTPS.
