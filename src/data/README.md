# Credit Cards Data Structure

This directory contains the JSON data for credit cards used in the comparison page.

## File Structure

- `credit-cards.json` - Main data file containing all credit card information

## JSON Schema

Each credit card object in the `cards` array should follow this structure:

```json
{
  "id": "unique-card-id",
  "cardImage": "/images/cards/card-image.svg",
  "cardName": "Card Display Name",
  "bankName": "Bank Name",
  "provider": "provider-slug",
  "cardAssociation": ["visa", "mastercard", "amex", "unionpay"],
  "category": "rewards|cashback|travel",
  "promotions": ["moneysmart-exclusive", "online-promotion", "apple-gifts", "vouchers-points", "miles-rewards", "cash-offer"],
  "badges": ["Badge Text 1", "Badge Text 2"],
  "primaryReward": {
    "rate": "S$1 = 10X Points",
    "description": "Description of primary reward"
  },
  "secondaryReward": {
    "rate": "S$1 = 1X Point",
    "description": "Description of secondary reward"
  },
  "tertiaryReward": {
    "rate": "Earn 4 Miles",
    "description": "Description of tertiary reward"
  },
  "offers": [
    {
      "title": "Offer Title",
      "badge": "Badge Label",
      "image": "/images/offers/image.svg",
      "icon": "lucide-icon-name",
      "points": "Points description"
    }
  ],
  "promotionDetails": "HTML content for promotion details",
  "promotionExpiry": "DD MMM YYYY",
  "applyUrl": "https://bank-apply-url.com",
  "annualFee": 0,
  "rating": 4.5,
  "featured": true
}
```

## Field Descriptions

### Required Fields

- **id**: Unique identifier for the card (string, kebab-case)
- **cardImage**: Path to card image (string, relative to public folder)
- **cardName**: Display name of the card (string)
- **bankName**: Name of the issuing bank (string)
- **provider**: Slug for filtering by provider (string, must match FilterSidebar options)
- **category**: Card category for filtering (string: "rewards", "cashback", "travel")

### Filter-Related Fields

- **cardAssociation**: Array of card networks (array of strings)
  - Possible values: "visa", "mastercard", "amex", "unionpay", "diners"

- **promotions**: Array of promotion types (array of strings)
  - Possible values: "moneysmart-exclusive", "online-promotion", "apple-gifts", "vouchers-points", "miles-rewards", "cash-offer"

### Display Fields

- **badges**: Array of badge texts to display at the top of the card (array of strings)
- **primaryReward**: Main reward information (object with rate and description)
- **secondaryReward**: Secondary reward information (optional object)
- **tertiaryReward**: Tertiary reward information (optional object)
- **offers**: Array of promotional offers (optional array of objects)
- **promotionDetails**: HTML string describing the promotion (optional string)
- **promotionExpiry**: Expiry date of promotion (optional string)
- **applyUrl**: URL to bank's application page (string)

### Sorting Fields

- **annualFee**: Annual fee amount in SGD (number)
- **rating**: Card rating out of 5 (number)
- **featured**: Whether card should appear first in featured sort (boolean)

## Available Filters

### Promotions (Checkboxes)
- moneysmart-exclusive
- online-promotion
- apple-gifts
- vouchers-points
- miles-rewards
- cash-offer

### Card Association (Checkboxes)
- mastercard
- visa
- amex
- unionpay
- diners

### Providers (Radio Buttons)
- all-providers (default)
- hsbc
- citibank
- ocbc
- airwallex

### Categories (Top Filter Buttons)
- all (default)
- promo
- cashback
- travel
- rewards

## Available Sort Options

1. **Featured** - Shows featured cards first
2. **Highest Rating** - Sorts by rating descending
3. **Lowest Rating** - Sorts by rating ascending
4. **Annual Fee: Low to High** - Sorts by fee ascending
5. **Annual Fee: High to Low** - Sorts by fee descending
6. **Name: A to Z** - Alphabetical ascending
7. **Name: Z to A** - Alphabetical descending

## Adding New Cards

To add a new credit card:

1. Create a card image SVG in `/public/images/cards/`
2. Create offer images (if any) in `/public/images/offers/`
3. Add a new card object to the `cards` array in `credit-cards.json`
4. Ensure all required fields are filled
5. Set appropriate filter values for category, promotions, cardAssociation, and provider

## Modifying Filters

To add new filter options:

1. **New Promotion Type**: Add to `promotions` array in card data, then update FilterSidebar component
2. **New Card Association**: Add to `cardAssociation` array in card data, then update FilterSidebar component
3. **New Provider**: Add to `provider` field in card data, then update FilterSidebar component
4. **New Category**: Add to `category` field in card data, then update CreditCardHero component filter buttons

## Icons

All offer icons use Lucide icons. Available icons include:
- banknote
- wallet
- gift
- plane
- sparkles
- badge-dollar-sign
- tag

View full icon list at: https://lucide.dev/icons/
