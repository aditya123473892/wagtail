We use [Algolia DocSearch](https://docsearch.algolia.com/) for the documentation search on [docs.wagtail.org](https://docs.wagtail.org/). DocSearch is made of three components: the search UI widget, the crawler, and the search index. All three can be configured extensively.

## Search widget

[Widget documentation (v3)](https://docsearch.algolia.com/docs/DocSearch-v3)

## Crawler configuration

[Crawler admin & configuration](https://crawler.algolia.com/admin/crawlers/b183d2d0-c453-4b3b-bac5-c703871d0124/overview) | [Legacy configuration](https://github.com/algolia/docsearch-configs/blob/master/configs/wagtail.json)

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

Faceted search by version relies on the [`docsearch:version` meta tag](https://docsearch.algolia.com/docs/required-configuration#introduce-global-information-as-meta-tags).

## Search index

[Search index admin](https://www.algolia.com/apps/XSYGEO7KMJ/explorer/browse/wagtail)

## Sample problematic searches

- Settings potentially only appearing in code snippets: `WAGTAILIMAGES_INDEX_PAGE_SIZE`
- https://github.com/wagtail/wagtail/issues/10139