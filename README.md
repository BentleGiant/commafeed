# CommaFeed - BongoFeed

A fork of [CommaFeed](https://github.com/Athou/commafeed) with additional features for improved reading experience and content management.

## What's Different in This Fork

### Article Truncation
Truncate long articles to a configurable character limit for faster page loads and better readability.

- **Toggle**: Enable/disable article truncation in Display settings
- **Configurable length**: Set truncation limit (100-10,000 characters, default 1,000)
- **HTML-safe**: Preserves formatting and media content when truncating
- **Smart handling**: Articles shorter than the limit are displayed in full

### Global Content Filter
Apply filtering expressions to **all feeds** from one central location, with per-feed overrides.

- **Global filter**: Set a single JEXL filter expression that applies to all feeds
- **Per-feed override**: Individual feeds can use their own custom filter instead
- **Automatic marking**: Filtered entries are automatically marked as read
- **Flexible expressions**: Use JEXL syntax to filter by title, content, URL, author, or categories
  - Example: `url.contains('youtube') or (author eq 'john' and title.contains('update'))`

## License

Licensed under the Apache License 2.0. See the original CommaFeed repository for full license details.
