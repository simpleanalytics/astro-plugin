# All the `astro-simpleanalytics-plugin` features

- [All the `astro-simpleanalytics-plugin` features](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content-all-the-astro-simpleanalytics-plugin-features)
  - [📃 Complete parameter configuration reference](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--complete-parameter-configuration-reference)
  - [✅ Option: Debugging 🚧](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-debugging-)
  - [✅ Option: Loading Analytics in all environments ♾️](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-loading-analytics-in-all-environments-️)
  - [✅ Option: Integrate with `@astrojs/partytown` 🎉](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-integrate-with-astrojspartytown-)
  - [✅ Option: Light version script 🪶](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-light-version-script-)
  - [✅ Option: Do Not Track (DNT) 🛑](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-do-not-track-dnt-)
  - [✅ Option: Group multiple domains 🥪](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-group-multiple-domains-)
  - [✅ Option: Bypass Ad Blockers 🪙](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-bypass-ad-blockers-)
  - [✅ Option: Ignore pages ➖](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-ignore-pages-)
  - [✅ Option: Non-unique hostnames 🔗](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-non-unique-hostnames-)
  - [✅ Option: Strict UTMs 🔒](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-strict-utms-)
  - [✅ Option: Allow URL parameters 🔓](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-allow-url-parameters-)
  - [✅ Option: Ignore metrics 🚫](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-ignore-metrics-)
  - [✅ Option: Custom alt text for tracking pixel 🏷️](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-custom-alt-text-for-tracking-pixel-️)
  - [💡 Feature: Embed chart on your site 📈](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--feature-embed-chart-on-your-site-)

Once you [install it](README.md#🚀-installation), the Astro Simple Analytics Plugin should be ready to go with zero config.

It exposes some of the advanced tracking options you can find below as component props, and optionally stubs in a console logger + an inline HTML hidden div when analytics are disabled for easy debugging (if you [include the `debug={true}` prop](#-option-debugging-)).

By default, it will only run in non-`local` and non-`development` environments and start tracking the currently visible domain inside the visitor browsers' address bar. It honors [Do Not Track](https://en.wikipedia.org/wiki/Do_Not_Track) and it also does gets blocked by some ad blockers. It gets embedded wherever you put it (ideally on all website pages, at the bottom of all your layouts, just before the closing `</body>` tag).

## 📃 Complete parameter configuration reference

These are all the available parameter options for this plugin where you choose to embed it, alongside the default values for each parameter:

```Astro
<SimpleAnalytics
  debug={false}                  {/* (false | true) */}
  allEnvironments={false}        {/* (false | true) */}
  partytown={false}              {/* (false | true) */}
  light={false}                  {/* (false | true) */}
  collectDNT={false}             {/* (false | true) */}
  strictUTMs={false}             {/* (false | true) */}
  allowParams={undefined}        {/* (undefined | string) */}
  customHostname={undefined}     {/* (undefined | string) */}
  customDomain={undefined}       {/* (undefined | string) */}
  ignorePages={undefined}        {/* (undefined | string) */}
  nonUniqueHostnames={undefined} {/* (undefined | string) */}
  ignoreMetrics={undefined}      {/* (undefined | string) */}
  altText={undefined}            {/* (undefined | string) */}
/>
```

The rendered static HTML for the code above would be:

```html
<!-- Simple Analytics - 100% privacy-first analytics -->
<script
  async
  defer
  src="https://scripts.simpleanalyticscdn.com/latest.js"
  type="text/javascript"
></script>
<noscript
  ><img
    src="https://queue.simpleanalyticscdn.com/noscript.gif"
    alt=""
    referrerpolicy="no-referrer-when-downgrade"
/></noscript>
```

If you'd like to change the default behaviour, please browse through the various parameter configuration options below:

## ✅ Option: Debugging 🚧

By default, the Astro Simple Analytics Plugin does not pollute the console with any logs, nor does it load extraneous DOM elements. However, you can trigger both in a debugging mode to verify whether the scripts are working correctly or not by adding this parameter to the component:

```Astro
<SimpleAnalytics debug={true} />
```

If you have issues or can't seem to make the plugin work, please refer to the [Troubleshooting section](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--troubleshooting).

## ✅ Option: Loading Analytics in all environments ♾️

By default, the Astro Simple Analytics Plugin attempts to load its client script exclusively on non-`local` and non-`development` environments by using [Vite's](https://vitejs.dev/guide/env-and-mode.html) `import.meta.env.DEV` boolean (since Vite is automatically bundled with Astro). If it's true, it doesn't load the script, but stubs the options with a `console.log()` and a hidden `<div />` element in HTML for easy debugging if you also [include the `debug={true}` prop](#-option-debugging-). If `import.meta.env.DEV` is somehow unavailable or unset, it defaults to showing the script everywhere. If you'd like to force showing the script on all environments (including `local` / `development`, `staging` / `preview`, `production`, etc.), you need to add the following component property:

```Astro
<SimpleAnalytics allEnvironments={true} />
```

## ✅ Option: Integrate with `@astrojs/partytown` 🎉

[Partytown](https://partytown.builder.io/) is a lazy-loaded library to help relocate resource intensive scripts into a [web worker](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API), and off of the [main thread](https://developer.mozilla.org/en-US/docs/Glossary/Main_thread). If you're using third-party scripts for things like analytics or ads, Partytown is a great way to make sure that they don't slow down your site.

This plugin can optionally integrate with [@astrojs/partytown](https://github.com/withastro/astro/tree/main/packages/integrations/partytown). For more details about `@astrojs/partytown`, read the [official Astro integration documentation](https://docs.astro.build/en/guides/integrations-guide/partytown/).

In order for Partytown to expose debug features for implementation and forward window events from the service worker back to the main thread, make sure that, at a minimum, you set these configuration flags in your Partytown integration inside `astro.config.*` file:

```typescript
// astro.config.mjs
// ...
export default defineConfig({
  integrations: [
    partytown({
      config: {
        debug: true,
        forward: ["dataLayer.push"],
      },
    }),
  ],
});
```

If you want to enable this plugin integration, use this component property when rendering your Analytics in your `Layout.astro`:

```Astro
<SimpleAnalytics partytown={true} />
```

## ✅ Option: Light version script 🪶

The Simple Analytics script is already very light, but in exchange for some missing features, it can be made even **lighter** by using this component property:

```Astro
<SimpleAnalytics light={true} />
```

The features missing from the **lighter** script are:

- ❌ Time on page
- ❌ Hash navigation
- ❌ Scroll depth
- ❌ SPA
- ❌ Screen sizes
- ❌ Ignore pages
- ❌ Overwrite domain name
- ❌ Ignore DNT

Read more details about this feature in the [official documentation](https://docs.simpleanalytics.com/light).

## ✅ Option: Do Not Track (DNT) 🛑

By default, the Simple Analytics [supports the Do Not Track setting](https://docs.simpleanalytics.com/dnt) and supports the feature of not tracking users that have chosen this option in their browsers. If you would like to enable tracking devices irrespective of this option, you need to enable the following component property:

```Astro
<SimpleAnalytics collectDNT={true} />
```

## ✅ Option: Group multiple domains 🥪

By default, the Simple Analytics uses the domain shown to users in the browser's address bar. If you want to [link multiple domains into one domain](https://docs.simpleanalytics.com/overwrite-domain-name) in your dashboard, or you want to use a different domain than people see in their browser address bar, you need to enable the following component property:

```Astro
<SimpleAnalytics customHostname="example.com" />
```

## ✅ Option: Bypass Ad Blockers 🪙

By default, the Simple Analytics JavaScript file loads from the `scripts.simpleanalyticscdn.com` domain. You can also optionally specify a custom domain to **bypass ad blockers**:

```Astro
<SimpleAnalytics customDomain="custom.domain.com" />
```

Read more about this in [the Simple Analytics documentation](https://docs.simpleanalytics.com/bypass-ad-blockers).

## ✅ Option: Ignore pages ➖

By default, the Simple Analytics JavaScript file loads in the site footer on all your pages. If you'd like to [avoid loading the script on some pages](https://docs.simpleanalytics.com/ignore-pages) (and implicitly not tracking those pages) add this component property as a CSV string with optional wildcards:

```Astro
<SimpleAnalytics ignorePages="/search/*,/accounts/*,/vouchers" />
```

## ✅ Option: Non-unique hostnames 🔗

Suppose you redirect your visitors to a payment provider, and after they complete the payment, they return to your website. Because of the nature of not tracking visitors in Simple Analytics, we count those "returning" visitors as new visitors. To prevent this from happening, you can specify the hostname of that payment provider to tell us we should register this visit as non-unique.

You can [specify a list of hostnames](https://docs.simpleanalytics.com/non-unique-hostnames) as CSV values (without `https://`) in this component property:

```Astro
<SimpleAnalytics nonUniqueHostnames="checkout.stripe.com,checkout.adyen.com,checkout.mollie.com" />
```

## ✅ Option: Strict UTMs 🔒

By default, the Astro Simple Analytics Plugin allows tracking for all these combinations of UTM tags (and stripping them automatically from the tracked URLs):

- `utm_source` / `source` / `ref` (in the dashboard, all three of these equivalent params are stored as `utm_source`)
- `utm_medium` / `medium`
- `utm_campaign` / `campaign`
- `utm_content` / `content`
- `utm_term` / `term`

To give you control over which parameter Simple Analytics should store, you can [enable strict UTMs](https://docs.simpleanalytics.com/strict-utms):

```Astro
<SimpleAnalytics strictUTMs={true} />
```

This will exclusively allow for the following UTMs to be used and collected:

- `utm_source`
- `utm_medium`
- `utm_campaign`
- `utm_content`
- `utm_term`

The parameters `source`, `ref`, `medium`, `campaign`, and any other custom parameter will not be collected.

## ✅ Option: Allow URL parameters 🔓

By default, the Astro Simple Analytics Plugin allows tracking for all these combinations of UTM tags (and stripping them automatically from the tracked URLs):

- `utm_source` / `source` / `ref` (in the dashboard, all three of these equivalent params are stored as `utm_source`)
- `utm_medium` / `medium`
- `utm_campaign` / `campaign`
- `utm_content` / `content`
- `utm_term` / `term`

**WARNING:** If your use [strict UTMs](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-strict-utms-), you can only use the query parameters that start with `utm_`, so we recommend also setting that option to `false` or removing it from the settings altogether.

We don't store the rest of the query parameters. But some customers have non-personal data in their query parameters, for example: `product-id` or `article-slug`. We allow collecting those parameters as long as they are specified via our script settings.

If you want to capture `product-id` and `article-slug` from your website's URLs, you can specify the following setting:

```Astro
<SimpleAnalytics allowParams="product-id,article-slug" />
```

Read more about the [Allow Params setting in the official Simple Analytics documentation](https://docs.simpleanalytics.com/allow-params), and more on [how to use URL parameters can be found here](https://docs.simpleanalytics.com/how-to-use-url-parameters).

## ✅ Option: Ignore metrics 🚫

The Astro Simple Analytics Plugin only collects non-personal data. If you want to limit the collected metrics even more, you can reference the table below and add any of these to the list of [ignored metrics](https://docs.simpleanalytics.com/ignore-metrics):

| Metric              | Slug           | Inferrered metric                                                                               |
| :------------------ | :------------- | :---------------------------------------------------------------------------------------------- |
| Referrer            | `referrer`     |                                                                                                 |
| UTM codes           | `utm`          | [`ref` param](https://docs.simpleanalytics.com/how-to-use-url-parameters#using-a-url-parameter) |
| Country / time zone | `country`      |                                                                                                 |
| Session IDs         | `session`      |                                                                                                 |
| Time on page        | `timeonpage`   | Data point ID, Page ID                                                                          |
| Scrolled            | `scrolled`     | Data point ID, Page ID                                                                          |
| User Agent          | `useragent`    |                                                                                                 |
| Screen size         | `screensize`   |                                                                                                 |
| Viewport size       | `viewportsize` |                                                                                                 |
| Language            | `language`     |                                                                                                 |

See [page with metric explanations](https://docs.simpleanalytics.com/metrics).

So if, for example, you'd like to ignore `timeonpage` and `scrolled`, you should add the following parameter to the `<SimpleAnalytics />` component:

```Astro
<SimpleAnalytics ignoreMetrics="timeonpage,scrolled" />
```

You can add any number of metrics to this list if you want to ignore them.

## ✅ Option: Custom alt text for tracking pixel 🏷️

By default, the tracking pixel in the noscript fallback has an empty alt attribute (`alt=""`), which is appropriate for decorative images. However, you may want to provide custom alternative text for accessibility or other reasons.

You can customize the alt text by passing the `altText` parameter:

```Astro
<SimpleAnalytics altText="Simple Analytics tracking pixel" />
```

If you don't provide the `altText` parameter, it will default to an empty string, keeping the original behavior.

## 💡 Feature: Embed chart on your site 📈

The Astro Simple Analytics Plugin allows you to [embed a chart of your public website statistics](https://docs.simpleanalytics.com/embed-chart-on-your-site) on your website.

In order to do this, you need to use a secondary component in the file you want to get your embed working:

```diff lang="Astro" "<SimpleAnalyticsChart />"
  // page.astro
  ---
+ import { SimpleAnalyticsChart } from 'astro-simpleanalytics-plugin';
  ---

  <!doctype html>
  <html>
    <head>...</head>
    <body>
      ...
+     <SimpleAnalyticsChart />
    </body>
  </html>
```

Another use case with default parameters:

```Astro
<SimpleAnalyticsChart id="xyz" hostname="example.com" style="aspect-ratio: 2/1;" loadingText="Chart is loading..." />
```

We are passing all customization parameters through to the element rendering the graph via the component parameters. This is how a sample component looks like with all options declared:

```Astro
<SimpleAnalyticsChart
  id="chart"
  style="aspect-ratio: 2/1;"
  loadingText="Loading chart..."
  hostname="example.com"
  start="2023-09-06"
  end="2023-10-06"
  types="visitors"
  pageViewsSelector="#pageviews"
  visitorsSelector="#visitors"
  pages="/,/contact"
  yMax={10000}
  timezone="Europe/Amsterdam"
  borderWidth={1}
  textColor="#ff6600"
  pageViewsColor="#ff6600"
  visitorsColor="#cc2200"
  areaOpacity={10}
  showLogo={true}
/>
```

In order to make this feature work on public pages (where you shouldn't require [header authentication](https://docs.simpleanalytics.com/api/authenticate)), make sure your website has the [Stats API](https://docs.simpleanalytics.com/api/stats) exposed by setting the `Change visibility` option on your specific website settings into `Keep stats public`, inside your website settings page (which can be found by replacing `example.com` with your domain name in the URL: `https://simpleanalytics.com/example.com/settings#visibility`).
