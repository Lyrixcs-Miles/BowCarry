# BowCarry

This is the product page for my first product, The Complete Set: a 1200ml insulated flask that comes with its carry accessories, for R299.

Live at https://bowcarry.azhyre.co.za

I kept it as simple as I could. It's one HTML file with the CSS and JavaScript inside it, plus a folder of images. There's nothing to install and nothing to build.

**The page is up but it isn't finished.** I'm still waiting on details from my supplier, so some of the text is placeholder and a few claims aren't confirmed yet. My list of what's left is under [Before I launch](#before-i-launch).

## Running it

Open `index.html` in a browser. That's it.

The Buy Button, fonts and tracking load from the internet, so those parts need a connection. Everything else works offline.

## What's in the repo

| Path | What it is |
|---|---|
| `index.html` | The whole page |
| `resources/imgs/` | Product images |
| `CNAME` | Tells GitHub Pages to serve the site on my domain |

## How I change things

### Stock count

I update this by hand after every sale. The number is in two places in `index.html` and they have to match:

- `#stock-count` in the buy box ("10 of 10 sets left in batch 1")
- the "Only 10 sets left" sticker on the main image

### Images

Each colour has three images, and each image has a small version for the thumbnail:

```
pink-set.webp            pink-set-thumb.webp
pink-set-contents.webp   pink-set-contents-thumb.webp
pink-flask.webp          pink-flask-thumb.webp
```

`set` is everything fitted on the flask, `set-contents` is each piece laid out, and `flask` is the flask by itself. I save them as WebP so the page stays light on mobile data. The thumbnails are 200px wide.

The images I'm using now are renders, not photos, which is why the caption under the main image says "Product render". I'll take that caption off when I replace them with real photos.

### Adding a colour

The page builds the image path from the colour and the view, so a new colour needs two things:

1. Six images named like the ones above, starting with the colour name (`lilac-set.webp` and so on).
2. One more swatch button in the buy box, copied from an existing one, with `data-colour="lilac"`, the display name in `data-name` and the swatch colour in `data-hex`.

No JavaScript changes needed.

### Prices and text

All of it is plain text in `index.html`. The price appears in seven places (the page description and product data at the top, the buy box, the backup buy link, the closing banner, the sticky bar and the tracking code at the bottom), so I search for `299` and change them together.

## How the page behaves

A few things I'd forget if I didn't write them down.

**Buy button.** The Shopify Buy Button loads into the buy box. Until it does, a plain "Buy now" link shows in its place, and that link is hidden a few seconds later if the Shopify button turned up. The Shopify button won't appear until I put a real product ID in.

**Cookies and tracking.** Google Analytics and the Meta Pixel don't load until a visitor clicks Accept on the cookie banner. If they click Decline, nothing loads and the banner doesn't come back. Right now I only record a page view and a product view. I still need to add checkout and purchase tracking from the Shopify side.

**Newsletter form.** It checks the email address and makes sure the consent box is ticked. I haven't connected a mailing list yet, so for now it tells people "Sign-up is not connected yet." I didn't want it saying thanks for signing up when nothing was saved.

**Reviews.** The slider works, but the quotes in it are placeholders. I'm taking the section out until I have real reviews.

**Sticky bar.** The buy bar at the bottom of the screen shows up once the main buy box has scrolled out of view.

## Placeholders

Anything in `[SQUARE BRACKETS]` in `index.html` is something I still need to fill in. Searching for `[` finds them all.

**Links and contact details**

- `[PAGE URL]` in the product data at the top of the file
- `[EMAIL]`, `[TERMS URL]`, `[PRIVACY URL]`, `[FULL POLICY URL]`
- `[TIKTOK HANDLE]`, `[INSTAGRAM HANDLE]`, `[FACEBOOK PAGE]`, `[PINTEREST HANDLE]`

**Shop and tracking**

- `[NEW PRODUCT ID]` is the Shopify product ID for the Buy Button
- `[CHECKOUT LINK]` is the backup link, which should go to the Shopify product page
- `G-XXXXXXXXXX` is my Google Analytics ID
- `PIXEL_ID` is my Meta Pixel ID
- `[GOOGLE VERIFICATION CODE]` and `[META VERIFICATION CODE]`
- `[MAILING LIST FORM URL]` is where the newsletter form sends to

**Product details I need from my supplier in writing**

- `[AMOUNT]` free delivery threshold
- `[X]` working days to ship
- `[LOCATION]` where orders ship from
- `[CONFIRM]` and `[CONFIRM WITH SUPPLIER]` cover the material, insulation, dimensions, who pays return postage and what photos I need for a return
- `[CONFIRM AFTER SHOP TEST]` covers how long drinks stay cold and whether it's leak-proof. I'm testing both myself before I claim them.
- `[CONFIRM REAL COLOURWAYS BEFORE LAUNCH]`

**Things that have to be true or they come off the page**

- `[RATING]`, `[N]`, `[Real review quote]`, `[Customer first name]`, `[city]`. I won't publish reviews I made up.
- `[TRENDING: keep only if true]`
- `[ORIGINAL PRICE]` and `[%]`, the crossed-out price and the saving. These only stay if there's a real discount.
- `[PAYFLEX / PROVIDER]`, the pay-later line. This only stays once I've signed up with a provider.
- The stock line has to match what I actually have on the shelf.

## Before I launch

- [ ] Trademark check on the BowCarry name (CIPC search at cipc.gov.za)
- [ ] Count my stock: complete sets per colour
- [ ] Create the product in Shopify with the colour options, add the Buy Button channel, and put the product ID in the page
- [ ] Get delivery time, free delivery threshold, return postage and insulation details from the supplier in writing
- [ ] Rewrite the product description and the "In the box" section so they list exactly the pieces that ship
- [ ] Replace the renders with real photos
- [ ] Add my Google Analytics ID, Meta Pixel ID and both verification codes
- [ ] Connect a mailing list with double opt-in
- [ ] Have the cookie wording and returns policy checked against the Consumer Protection Act and POPIA
- [ ] Test on a phone and a laptop, in Chrome and Safari

## Hosting

The site runs on GitHub Pages from the `main` branch, so anything I push to `main` goes live a minute or two later.

The domain is `bowcarry.azhyre.co.za`. It's a CNAME record at GoDaddy with the name `bowcarry` pointing to `lyrixcs-miles.github.io`, and HTTPS is switched on in the Pages settings.
