We use [Algolia DocSearch](https://docsearch.algolia.com/) for the documentation search on [docs.wagtail.org](https://docs.wagtail.org/). DocSearch is made of three components: the search UI widget, the crawler, and the search index. All three can be configured extensively.

## Search widget

[Widget documentation (v3)](https://docsearch.algolia.com/docs/DocSearch-v3) | [Widget documentation (v2, legacy)](https://docsearch.algolia.com/docs/legacy/dropdown)

We currently use the v2 widget, which is no longer maintained but still API-compatible with a recently set up index.

## Crawler configuration

[Crawler admin & configuration](https://crawler.algolia.com/admin/crawlers/b183d2d0-c453-4b3b-bac5-c703871d0124/overview) | [Legacy configuration](https://github.com/algolia/docsearch-configs/blob/master/configs/wagtail.json)

We track a copy of the configuration and history of changes here, in addition to what is visible in the Algolia UI, for transparency / ease of troubleshooting.

<details>

<summary>Current crawler configuration (last updated 2023-03-13)</summary>

```js
new Crawler({
  rateLimit: 8,
  maxDepth: 10,
  startUrls: ["https://docs.wagtail.org/"],
  renderJavaScript: false,
  sitemaps: ["https://docs.wagtail.org/sitemap.xml"],
  ignoreCanonicalTo: false,
  discoveryPatterns: ["https://docs.wagtail.org/**"],
  exclusionPatterns: [
    "https://docs.wagtail.org/en/v4.2/**",
    "https://docs.wagtail.org/en/v4.1.2/**",
    "https://docs.wagtail.org/en/v4.1.1/**",
    "https://docs.wagtail.org/en/v4.1/**",
    "https://docs.wagtail.org/en/v4.0**",
    "https://docs.wagtail.org/en/v3**",
    "https://docs.wagtail.org/en/v2**",
    "https://docs.wagtail.org/en/v1**",
    "https://docs.wagtail.org/en/v0**",
  ],
  schedule: "at 11:26 AM on Monday",
  actions: [
    {
      indexName: "wagtail",
      pathsToMatch: ["https://docs.wagtail.org/**"],
      recordExtractor: ({ helpers }) => {
        return helpers.docsearch({
          recordProps: {
            lvl1: ["header h1", "article h1", "main h1", "h1", "head > title"],
            content: ["article p, article li", "main p, main li", "p, li"],
            lvl0: {
              selectors: "",
              defaultValue: "Documentation",
            },
            lvl2: ["article h2", "main h2", "h2"],
            lvl3: ["article h3", "main h3", "h3"],
            lvl4: ["article h4", "main h4", "h4"],
            lvl5: ["article h5", "main h5", "h5"],
            lvl6: ["article h6", "main h6", "h6"],
          },
          aggregateContent: true,
          recordVersion: "v3",
        });
      },
    },
  ],
  initialIndexSettings: {
    wagtail: {
      attributesForFaceting: ["type", "lang", "version"],
      attributesToRetrieve: [
        "hierarchy",
        "content",
        "anchor",
        "url",
        "url_without_anchor",
        "type",
      ],
      attributesToHighlight: ["hierarchy", "content"],
      attributesToSnippet: ["content:10"],
      camelCaseAttributes: ["hierarchy", "content"],
      searchableAttributes: [
        "unordered(hierarchy.lvl0)",
        "unordered(hierarchy.lvl1)",
        "unordered(hierarchy.lvl2)",
        "unordered(hierarchy.lvl3)",
        "unordered(hierarchy.lvl4)",
        "unordered(hierarchy.lvl5)",
        "unordered(hierarchy.lvl6)",
        "content",
      ],
      distinct: true,
      attributeForDistinct: "url",
      customRanking: [
        "desc(weight.pageRank)",
        "desc(weight.level)",
        "asc(weight.position)",
      ],
      ranking: [
        "words",
        "filters",
        "typo",
        "attribute",
        "proximity",
        "exact",
        "custom",
      ],
      highlightPreTag: '<span class="algolia-docsearch-suggestion--highlight">',
      highlightPostTag: "</span>",
      minWordSizefor1Typo: 3,
      minWordSizefor2Typos: 7,
      allowTyposOnNumericTokens: false,
      minProximity: 1,
      ignorePlurals: true,
      advancedSyntax: true,
      attributeCriteriaComputedByMinProximity: true,
      removeWordsIfNoResults: "allOptional",
    },
  },
  appId: "XSYGEO7KMJ",
  apiKey: "c8556131d460c9e7cd8a218407329e94",
});
```

</details>

### Crawler configuration CHANGELOG

- 2023-03-13: Add `exclusionPatterns` for past Wagtail releases using different search infrastructure, so the crawls are faster (Thibaud Colas)
- 2023-03-09: Remove `release` from `attributesForFaceting`. This was added by mistake to match erroneous configuration ([sphinx_wagtail_theme#251](https://github.com/wagtail/sphinx_wagtail_theme/pull/251) (Thibaud Colas)
- 2023-01-16: Add sitemap to `sitemaps` and `version`, `release` to `attributesForFaceting` (Thibaud Colas)

<details>

<summary>Original crawler configuration from Algolia</summary>

```js
new Crawler({
  rateLimit: 8,
  maxDepth: 10,
  startUrls: ["https://docs.wagtail.org/"],
  renderJavaScript: false,
  sitemaps: [],
  ignoreCanonicalTo: false,
  discoveryPatterns: ["https://docs.wagtail.org/**"],
  schedule: "at 11:26 AM on Monday",
  actions: [
    {
      indexName: "wagtail",
      pathsToMatch: ["https://docs.wagtail.org/**"],
      recordExtractor: ({ helpers }) => {
        return helpers.docsearch({
          recordProps: {
            lvl1: ["header h1", "article h1", "main h1", "h1", "head > title"],
            content: ["article p, article li", "main p, main li", "p, li"],
            lvl0: {
              selectors: "",
              defaultValue: "Documentation",
            },
            lvl2: ["article h2", "main h2", "h2"],
            lvl3: ["article h3", "main h3", "h3"],
            lvl4: ["article h4", "main h4", "h4"],
            lvl5: ["article h5", "main h5", "h5"],
            lvl6: ["article h6", "main h6", "h6"],
          },
          aggregateContent: true,
          recordVersion: "v3",
        });
      },
    },
  ],
  initialIndexSettings: {
    wagtail: {
      attributesForFaceting: ["type", "lang"],
      attributesToRetrieve: [
        "hierarchy",
        "content",
        "anchor",
        "url",
        "url_without_anchor",
        "type",
      ],
      attributesToHighlight: ["hierarchy", "content"],
      attributesToSnippet: ["content:10"],
      camelCaseAttributes: ["hierarchy", "content"],
      searchableAttributes: [
        "unordered(hierarchy.lvl0)",
        "unordered(hierarchy.lvl1)",
        "unordered(hierarchy.lvl2)",
        "unordered(hierarchy.lvl3)",
        "unordered(hierarchy.lvl4)",
        "unordered(hierarchy.lvl5)",
        "unordered(hierarchy.lvl6)",
        "content",
      ],
      distinct: true,
      attributeForDistinct: "url",
      customRanking: [
        "desc(weight.pageRank)",
        "desc(weight.level)",
        "asc(weight.position)",
      ],
      ranking: [
        "words",
        "filters",
        "typo",
        "attribute",
        "proximity",
        "exact",
        "custom",
      ],
      highlightPreTag: '<span class="algolia-docsearch-suggestion--highlight">',
      highlightPostTag: "</span>",
      minWordSizefor1Typo: 3,
      minWordSizefor2Typos: 7,
      allowTyposOnNumericTokens: false,
      minProximity: 1,
      ignorePlurals: true,
      advancedSyntax: true,
      attributeCriteriaComputedByMinProximity: true,
      removeWordsIfNoResults: "allOptional",
    },
  },
  appId: "XSYGEO7KMJ",
  apiKey: "c8556131d460c9e7cd8a218407329e94",
});
```

</details>

Faceted search by version relies on the [`docsearch:version` meta tag](https://docsearch.algolia.com/docs/required-configuration#introduce-global-information-as-meta-tags). We set this tag to match the version _slug_ in URLs (`current_version` context variable from Read the Docs in documentation site templates), so aliases like `stable` and `latest` are indexed separately from numbered releases.

## Search index

[Search index admin](https://www.algolia.com/apps/XSYGEO7KMJ/explorer/browse/wagtail)

## Sample problematic searches

- Settings potentially only appearing in code snippets: `WAGTAILIMAGES_INDEX_PAGE_SIZE`
- https://github.com/wagtail/wagtail/issues/10139