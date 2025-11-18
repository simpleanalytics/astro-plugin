<a href="https://simpleanalytics.com/?ref=github.com/ViorelMocanu/astro-simpleanalytics-plugin">
  <img src="https://assets.simpleanalytics.com/images/logos/logo-github-readme.png" alt="Simple Analytics logo" align="right" height="62" />
</a>

# Astro Simple Analytics Plugin

[![NPM Package Version](https://img.shields.io/npm/v/astro-simpleanalytics-plugin)](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/releases) [![GitHub contributors](https://img.shields.io/github/contributors/ViorelMocanu/astro-simpleanalytics-plugin.svg)](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/graphs/contributors) [![GitHub Sponsors](https://img.shields.io/github/sponsors/ViorelMocanu)](https://github.com/sponsors/ViorelMocanu/) [![ISC license](https://img.shields.io/badge/License-ISC-blue.svg?style=flat)](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/LICENSE) [![Downloads of NPM package](https://img.shields.io/npm/dt/astro-simpleanalytics-plugin)](https://www.npmjs.com/package/astro-simpleanalytics-plugin)

[Simple Analytics](https://simpleanalytics.com) is a clean, simple, and privacy friendly analytics tool. Actionable data in a beautiful dashboard. It does not use cookies and you can bypass ad blockers. Make sure to signup to get most value out of this plugin.

[Astro](https://astro.build/) is a website build tool for the modern web — powerful developer experience meets lightweight output.

This is a [Simple Analytics](https://github.com/simpleanalytics) plugin for [Astro](https://github.com/withastro/astro).

- Astro Simple Analytics Plugin
  - [🚀 Installation](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--installation)
  - [✨ Usage](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--usage)
    - [📃 Complete parameter configuration reference](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--complete-parameter-configuration-reference)
    - [✅ All features](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content-all-the-astro-simpleanalytics-plugin-features)
  - [🐞 Troubleshooting](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--troubleshooting)
  - [💡 Examples](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--examples)
  - [🙏 Contributing](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--contributing)
  - [📝 Other details](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin#user-content--other-details)

## 🚀 Installation

First, install the `astro-simpleanalytics-plugin` package using your package manager. Run this in the terminal:

```sh
# using PNPM
pnpm install astro-simpleanalytics-plugin
# Using Yarn
yarn add astro-simpleanalytics-plugin
# Using NPM
npm install astro-simpleanalytics-plugin
```

## ✨ Usage

You then need to import `astro-simpleanalytics-plugin` and then use the `<SimpleAnalytics />` component and add the desired properties to it. This will render out the tags in the location you place the `<SimpleAnalytics />` component in. We suggest using your layout from the `./layouts` folder (e.g. `./layouts/Layout.astro` and/or other equivalent layouts), just before the closing `</body>` tag.

```diff lang="Astro" "<SimpleAnalytics />"
  // Layout.astro
  ---
+ import { SimpleAnalytics } from 'astro-simpleanalytics-plugin';
  ---

  <!doctype html>
  <html>
    <head>...</head>
    <body>
      ...
+     <SimpleAnalytics />
    </body>
  </html>
```

Simple Analytics should be ready to go with zero config.

### 📃 Complete parameter configuration reference

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

Read more about the available features in the [dedicated features document](FEATURES.md).

## 🐞 Troubleshooting

If your Simple Analytics fails to render or load properly, or fails to send data into your dashboard, make sure you:

- [activate debugging mode](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-debugging-);
- deactivate your Ad Blocker or read about your options for [circumventing ad blocking](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/blob/main/FEATURES.md#user-content--option-bypass-ad-blockers-);
- read about [setting your CSP (Content Security Policy) correctly](https://docs.simpleanalytics.com/csp);
- if nothing works, [send us an issue](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/issues/new/choose) or [seek support from Simple Analytics directly](https://docs.simpleanalytics.com/support).

## 💡 Examples

- Check out the [embedded `./demo` project](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/tree/main/demo) (derived from the [Astro 3.0 `create-astro` starter scaffolding](https://www.npmjs.com/package/create-astro), using the blog template).
- [Browse projects with Astro Simple Analytics Plugin on GitHub](https://github.com/search?q=%22astro-simpleanalytics-plugin%22+path%3A**%2Fpackage.json&type=code) for more examples!

## 🙏 Contributing

Bug reports and pull requests [are always welcome on our GitHub](https://github.com/ViorelMocanu/astro-simpleanalytics-plugin/issues/new/choose).

If you'd like to contribute with code, please read our contribution guidelines in the [CONTRIBUTING.md](CONTRIBUTING.md) guide and see our [roadmap](ROADMAP.md).

Thank you!

## 📝 Other details

This package is available as open source under the terms of the [ISC License](https://opensource.org/license/isc-license-txt/).

See [CHANGELOG.md](CHANGELOG.md) for a history of changes to this integration.

---

This package has initially been used for building [Resurse.dev](https://resurse.dev/) - an online resource repository for people starting out in digital careers from Development to Design, from Marketing to Security, created for free by [Viorel](https://viorelmocanu.ro/) and his [YouTube](https://www.youtube.com/@ViorelMocanu) community. It was made by [Viorel Mocanu](https://github.com/ViorelMocanu) after [a challenge](https://github.com/simpleanalytics/roadmap/issues/708) from [Adriaan](https://github.com/adriaandotcom).
