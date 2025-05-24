---
title: configuring the built-in search engine
---
# Built-in Search Engine

## Introduction 

Converge includes a **built-in search engine**, written entirely in raw **PHP**, and designed specifically for documentation. From day one, your docs are searchable **no external services, no setup, and no cost.**
Converge also provides a top-tier UI modal offering an exceptional search experience, with support for recent searches, favorites, and accessibility.

## Search Index 

to search  your contents you must build the search index by running this command: 

```bash
php artisan converge:index-search
```
This command scans all of your Markdown files across modules, versions, and clusters and creates the necessary resources to deliver an instant search experience, All search data is stored under `storage/converge/*`  

If you're wondering how to handle search indexes in production, refer to the [deployement docs](./deployment)

@blade
<x-converge::alert type="warning">
every you change your files contents (at this point headings #, ##, etc) you must re index your markdown contents
</x-converge::alert>
@endblade

### Customization

The built-in search engine is customizable via the ``config/converge.php`` file. You can control behavior such as:

- **Stop words handling** : choose whether to index common words like “the”, “and”, etc.

<x-converge::alert>
By default, Converge indexes stop words. To disable this, set  `'keep_stop_words' => false` 
</x-converge::alert>

- **Fuzzy search** :  enable approximate matching to support typos and similar terms
<x-converge::alert>
Fuzzy search is enabled by default. To turn it off, set `'fuzzy_search' => 'false'` 
</x-converge::alert>
- **Fuzzy algorithm** :  switch between jaro_winkler or levenshtein for matching logic
<x-converge::alert>
The default is ``jaro_winkler``. To switch to Levenshtein, set  `'fuzzy_search_using' => 'levenshtein'` 
</x-converge::alert>

- **Result limit** : set how many results to return per query

<x-converge::alert>
By default, Converge returns up to 50 results. To change this, set  `'results_max_count' => 40` (any number)
</x-converge::alert>

These options help you tailor the search experience to your specific needs, whether you're building small internal docs or a large multi-package documentation hub.

## A Proof of Concept

This initial version is a proof of concept a demonstration that yes, it's absolutely possible to deliver a lightweight, effective search experience using just PHP.

Currently, the engine:

- uses the same algorithms behind big full text seach engines 

- Indexes only Markdown headings (#, ##, ###, etc.)

- Uses a filesystem-based index driver

- Delivers simple, fast results with no external dependencies


## What’s Next

This is just the beginning. The built-in search is still evolving and has plenty of room to grow. Upcoming improvements may include:

- Support for additional index drivers (e.g., SQLite, mysql, postgresql, Redis, or full-text search engines using plugins approach)
- Smarter ranking algorithms for more relevant results
- Deeper content indexing, beyond just heading

## Why We Took This Path 

We believe that every **Converge powered** site should offer instant, private, and free search capabilities out of the box.

- ✅ No setup

- ✅ No third-party services

- ✅ No hidden fees

- ✅ No data leaks

Just fast, accessible documentation ready to go.