---
sidebar_position: 9
---
# Pricing Section

The Pricing Section clearly outlines the cost of our product or service, presenting different pricing plans and options to cater to various user needs and budgets. This section is designed to be transparent and informative, helping potential customers understand the value they will receive at each price point. By showcasing the pricing structure effectively, this section aims to guide users toward the plan that best fits their requirements.

## Pricing Section 1
![Pricing Section 1](/img/pricing-section.jpeg)

## Usage
The component utilizes data from site-config.ts, specifically the plans array. You can add multiple plans to the plans array to create additional boxes within the component. However, for optimal user experience and clarity, it is recommended to keep the number of plans minimal, ideally under three.

**site-config.ts:**
```typescript
  stripe: {
    plans: [
      {
        priceId: process.env.NODE_ENV === "production" ? "price_1234" : "price_5678",
        mode: 'payment', //subscription | payment
        name: "Basic Package",
        successRedirect: `${process.env.NEXT_PUBLIC_PRIMARY_DOMAIN}/order-complete`,
        isFeatured: false, // Adds a featured flag and border around the card
        description: "Perfect for small teams",
        price: 49,
        priceAnchor: 99,
        features: [
          {
            name: "Feature 1 here",
            included: true
          },
          {
            name: "Feature 2 Here",
            included: true
          },
          {
            name: "Feature 3 Here",
            included: true
          },
          {
            name: "Feature 4 Here",
            included: true
          },
          {
            name: "Feature 5 Here",
            included: true
          },
          {
            name: "Feature 6 Here",
            included: false
          },
          {
            name: "Feature 7 Here",
            included: false
          },
          {
            name: "Feature 8 Here",
            included: false
          },
          {
            name: "Feature 9 Here",
            included: false
          },
        ],
      },
      {
        priceId: process.env.NODE_ENV === "production" ? "price_1234" : "price_1PHV1iGVfP1i6nIpMpZJiXOo",
        mode: 'payment', //subscription | payment
        name: "Pro Package",
        successRedirect: `${process.env.NEXT_PUBLIC_PRIMARY_DOMAIN}/order-complete`,
        isFeatured: true,
        description: "You need more power",
        price: 99,
        priceAnchor: 299,

        features: [
          {
            name: "Feature 1 here",
            included: true
          },
          {
            name: "Feature 2 Here",
            included: true
          },
          {
            name: "Feature 3 Here",
            included: true
          },
          {
            name: "Feature 4 Here",
            included: true
          },
          {
            name: "Feature 5 Here",
            included: true
          },
          {
            name: "Feature 6 Here",
            included: true
          },
          {
            name: "Feature 7 Here",
            included: true
          },
          {
            name: "Feature 8 Here",
            included: true
          },
          {
            name: "Feature 9 Here",
            included: true
          },
        ],
      },
    ],
  },
```

**page.tsx**
```typescript
import { PricingSection1 } from "@/components/marketing/pricing-section1";
```
```typescript
<PricingSection1 />
```

## Tips:
- **Clear and Transparent Pricing**: Display pricing plans and costs in a straightforward and transparent manner, avoiding hidden fees or complex structures.
- **Highlight Key Features**: For each pricing plan, list the key features and benefits included, making it easy for users to compare options.
- **Money-Back Guarantee**: If applicable, mention any money-back guarantees or trial periods to reduce perceived risk and encourage sign-ups.

