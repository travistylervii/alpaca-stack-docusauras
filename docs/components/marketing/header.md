---
sidebar_position: 1
---
# Header Section

The Header Component is designed for the marketing side of our Next.js application, featuring the company logo, navigation menu, and sign-in buttons. On mobile devices, it includes a responsive hamburger menu that reveals a sidebar mobile menu for intuitive navigation.

## How to change the dashboard navigation
The routes are handled in the /constants/nav-routes.ts file. Here, you will find all the navigation routes for various menus, including the header menu, footer menu, dashboard menu, admin menu, and sidebar menus.

## Header Section 1
![Header Section 1](/img/header-section.jpeg)

## Usage
```typescript
import { MarketingHeader } from "@/components/marketing/header-section";
```
```typescript
<MarketingHeader />
```

## Tips
- **Consistent Branding:** Use colors, fonts, and styles consistent with your overall branding to create a cohesive look.





