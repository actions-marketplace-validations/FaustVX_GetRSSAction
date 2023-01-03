# TestAction

Get data from RSS/ATOM feed using regex on `title` node and xPath to select the value element

# Usage

```yaml
steps:
- id: fetch-rss
  uses: FaustVX/TestAction@rss-v2
  with:
    url: "# RSS/ATOM url"
    title-regex: "# regex on the title element"
    xpath-out-selector: "# the element to select inside the selected node"
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)
