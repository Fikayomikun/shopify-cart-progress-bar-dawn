# Shopify Cart Free Shipping Progress Bar — Dawn Theme

A dynamic free shipping progress bar for the cart drawer, built for the Shopify Dawn theme. The bar fills based on the current cart value and switches to a completed colour and message once the free shipping threshold is reached.

## What it does

When a shopper opens the cart drawer, the progress bar shows how close their order is to qualifying for free shipping. The fill width is calculated from the cart total against a configurable threshold. Once the threshold is met, the bar moves into a completed state with a different colour and message.

For the UK cart drawer, subscription orders get a dedicated variant that displays a fully completed bar with a subscription-specific message — connecting directly to the free shipping Function built for subscription products.

## Files

| File | Purpose |
|------|---------|
| `snippets/cart-progress-bar.liquid` | Main progress bar component. Calculates fill percentage in Liquid and applies completed state when threshold is met. |
| `snippets/cart-subscription-progress-bar-uk.liquid` | UK subscription variant. Detects subscription items and renders the bar as complete with a dedicated message. |
| `snippets/shipping-progress-icon.liquid` | Reusable SVG truck icon inside the progress bar. |
| `assets/cart-progress-bar.css` | Styling for the bar track, progress fill, and icon wrapper. Works alongside inline styles in the snippets. |
| `config/settings_schema.json` | Theme schema exposing threshold, colour, and message settings in the Shopify theme editor. |

## Theme settings

All configurable directly in the Shopify theme editor — no code required.

| Setting | Controls |
|---------|---------|
| `minimum_free_shipping_amount` | Free shipping threshold used to calculate progress |
| `shipping_progress_bar_text` | Message shown below the bar in the default state |
| `subscription_free_shipping_text` | Message shown for UK subscription orders |
| `background_bar_color` | Colour of the inactive progress track |
| `progress_bar_color` | Fill colour before free shipping threshold is reached |
| `completed_bar_color` | Fill colour and message colour when threshold is met |
| `progress_message_color` | Text colour in the default state |

## How it works

Liquid handles the full render at page load:

- Reads `cart.total_price` for the current cart value
- Uses `settings.minimum_free_shipping_amount` as the threshold
- Calculates fill percentage and caps it at 100%
- Toggles an `is-complete` CSS class when the threshold is reached

No JavaScript required. The UK subscription variant bypasses the calculation entirely and renders a full bar for subscription orders.

## Architectural decision

Built as a theme-configurable section with schema settings rather than hardcoded markup. This means the threshold, colours, and messaging can all be adjusted in the theme editor by non-technical team members — no code changes needed.

## Links

- GitHub repo: github.com/Fikayomikun/shopify-cart-progress-bar-dawn
- Dev store: dev-store-kijimea.myshopify.com (password on request)
