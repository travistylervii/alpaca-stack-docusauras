---
sidebar_position: 3
---

# SEO

The `getSEOMetadata` function is designed to generate SEO metadata for a Next.js application. This metadata includes various properties such as title, description, keywords, Open Graph data, and Twitter card data. It also provides structured data for rich results on Google.

We are leveraging the Next.js metadata API and `generateMetadata` functions. You can learn more about them [here](https://nextjs.org/docs/app/building-your-application/optimizing/metadata) for a more in-depth understanding.

# Config
The default global configuration settings for the `getSEOMetadata` function can be found in the `/site-config.ts` file in the application root.

The primary SEO values are:

- `appName` (string): The name of the app.
- `appDescription` (string): The description of the app.
- `keywords` ([string]): Default SEO keywords for the app.
- `primaryDomain` (string): Default production domain for the app.

## Usage

By default, only the public routes, primarily the Marketing route, render SEO metadata. The function below can be found in the `/app/(marketing)/layout.tsx` file.

```typescript
import { getSEOMetadata } from "@/lib/seo";

export const metadata = getSEOMetadata();
```

## Customize

If you want to customize SEO metadata for a specific page, you can add the `getSEOMetadata` function to a specific page and add props.

- `title` (string): The title of the webpage.
- `description` (string): A brief description of the webpage.
- `keywords` (string): Keywords associated with the webpage.
- `canonicalUrlRelative` (string, optional): The relative canonical URL of the webpage.
- `openGraph` (object, optional): Open Graph data for the webpage.
  - `title` (string): The Open Graph title.
  - `description` (string): The Open Graph description.
  - `url` (string): The Open Graph URL.
  - `siteName` (string): The name of the site.
  - `ogImageUrl` (string, optional): The URL of the Open Graph image.

### Example

Here is an example of the blog page (`/app/blog/page.tsx`) with the `getSEOMetadata` custom props. Apply this function to any page you want to override the default layout `getSEOMetadata` function in the layout page.

```typescript
import { getSEOMetadata } from './path/to/your/function';

const metadata = getSEOMetadata({
    title: 'My Awesome Page',
    description: 'This is a description of my awesome page.',
    keywords: 'awesome, page, example',
    canonicalUrlRelative: '/my-awesome-page',
    openGraph: {
        title: 'Open Graph Title',
        description: 'Open Graph Description',
        url: 'https://example.com/my-awesome-page',
        siteName: 'Example Site',
    },
    ogImageUrl: 'https://example.com/og-image.png',
});
```

- The `ogImage` defaults to `https://${siteConfig.primaryDomain}/openGraph-image.png` if `ogImageUrl` is not specified.
- The `metadataBase` URL is set based on the environment (production or development).

# Testing

- Test Open Graph here: [opengraph.xyz/](https://www.opengraph.xyz)

## Tips for SEO

- **Keyword Optimization**: Perform thorough keyword research to find the terms your target audience is searching for. Use these keywords strategically in your content, titles, headers, and meta descriptions.
- **High-Quality Content**: Create valuable, engaging, and informative content that addresses the needs and interests of your audience. High-quality content is more likely to be shared and linked to, improving your search rankings.
- **Mobile-Friendliness**: Ensure your website is mobile-friendly. Google uses mobile-first indexing, meaning it predominantly uses the mobile version of the content for indexing and ranking.
- **Page Speed**: Optimize your website’s loading speed. Faster websites provide a better user experience and are favored by search engines. Use tools like Google PageSpeed Insights to identify and fix speed issues.
- **On-Page SEO**: Use proper heading tags (H1, H2, H3) to structure your content. Include relevant keywords in the first 100 words, and make sure your meta tags are optimized.
- **Internal Linking**: Use internal links to help search engines understand the structure of your website and to guide visitors to related content. This can improve the user experience and increase time spent on your site.
- **Backlinks**: Acquire high-quality backlinks from reputable websites. Backlinks are a strong indicator of authority and relevance, which can boost your search rankings.
- **User Experience (UX)**: Improve the overall user experience of your website. A well-designed, easy-to-navigate site encourages visitors to stay longer and reduces bounce rates, positively affecting your SEO.
- **Local SEO**: Optimize for local search if you have a physical location or serve a specific geographic area. Claim your Google My Business listing and ensure your name, address, and phone number (NAP) are consistent across all platforms.
- **Regular Updates**: Keep your content fresh and updated. Regularly updating your website with new content signals to search engines that your site is active and relevant.
- **Technical SEO**: Ensure your website is technically sound. This includes having a clear site structure, using SSL, creating a sitemap, and ensuring your site is crawlable by search engines.
- **Engage on Social Media**: Promote your content on social media platforms to increase visibility and attract more visitors to your site. Social signals can indirectly influence your search rankings.


