﻿# GetRSSAction

Get data from RSS/ATOM feed using regex on `title` node and xPath to select the value element

# Usage

```yaml
steps:
- id: fetch-rss
  uses: FaustVX/GetRSSAction@v3
  with:
    url: "# RSS/ATOM url"
    title-regex: "# regex on the title element"
    xpath-out-selector: "# the element to select inside the selected node"
```

## Example

```rss
<rss version="2.0">
  <channel>
  <title>RSS Title</title>
  <description>This is an example of an RSS feed</description>
  <link>http://www.example.com/main.html</link>
  <copyright>2020 Example.com All rights reserved</copyright>
  <lastBuildDate>Mon, 6 September 2010 00:01:00 +0000</lastBuildDate>
  <pubDate>Sun, 6 September 2009 16:20:00 +0000</pubDate>
  <ttl>1800</ttl>

  <item>
    <title>First entry </title>
    <description>Here is some text containing an interesting description.</description>
    <link>http://www.example.com/blog/post/1</link>
    <guid isPermaLink="false">7bd204c6-1655-4c27-aeee-53f933c5395f</guid>
    <pubDate>Sun, 6 September 2009 16:20:00 +0000</pubDate>
  </item>

  <item>
    <title>Second entry</title>
    <description>Here is some text containing an interesting description.</description>
    <link>http://www.example.com/blog/post/1</link>
    <guid isPermaLink="true">7bd204c6-1655-4c27-aeee-53f933c5395f</guid>
    <pubDate>Sun, 6 September 2019 16:20:00 +0000</pubDate>
  </item>

  </channel>
</rss>
```

```yaml
steps:
- id: fetch-rss
  uses: FaustVX/GetRSSAction@v3
  with:
    url: "# url of the RSS feed"
    title-regex: "^First \\w+$"
    xpath-out-selector: "guid/@isPermaLink"
```

Using this RSS feed and this action, on the `${{ steps.fetch-rss.outputs.selection }}`, you will get `false`

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)

# ChangeLog

| Version | Date | Information |
| ----- | ---------- | ---------- |
| 3.0 | 21/01/2023 | Proper return code propagation |
| 2.0 | 03/01/2023 | <ul><li>Proper support for ATOM feed</li><li>Correct return code</li></ul> |
| 1.0 | 03/01/2023 | Initial commit |
