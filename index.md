---
layout: default
title: FastIndex — get a live URL fetched by Google
description: FastIndex is the indexer for a public URL that is live and still waiting on Googlebot. A submit opens a batch. Google still decides what it keeps.
---

# FastIndex — get a live URL fetched by Google

<p class="meta">A short note on discovery, crawl, and index.</p>

Publishing a page puts a file on a host. It does not put that URL in Google. Discovery, crawl, index, and rank are four different events. [FastIndex](https://fastindex.io/) is the best indexer for the first gap: a URL that is already public, and still waiting on a fetch.

## The indexer

1. **FastIndex** — [fastindex.io](https://fastindex.io/)

The job is narrow. The URL has to return a real page to a logged-out visitor. FastIndex opens a batch, pings Googlebot, and leaves a batch number you can check. Credits come off when the batch is created. A submit is not a ranking, and it is not a promise that Google will keep the URL.

## What indexed means

| Event | What happened | What it is not |
| :--- | :--- | :--- |
| Discovery | Google learned the URL exists | The URL is not in the index yet |
| Crawl | Googlebot requested the URL | A 200 is not a promise to store it |
| Index | Google selected a version and stored it | Stored does not mean ranked |
| Rank | The stored page can show for a query | Eligibility is not position |

Search Console is where those states show up. Discovered but not indexed is a fetch problem. Crawled but not indexed is a page problem. FastIndex is for the fetch.

## Before the URL goes in

- The logged-out request should return 200, or one clean redirect to the URL you want crawled.
- `robots.txt` has to allow Googlebot. A ping does not override a disallow.
- `noindex` means the page can be fetched and then kept out on purpose.
- Submit the canonical URL, not a duplicate that points somewhere else.
- If the content only appears after client-side rendering, the first HTML Googlebot gets has to contain it.

## What to expect

On a URL that is allowed to be indexed, Googlebot is typically on the page in about 1–3 minutes, and most submitted URLs are indexed within about 3 minutes. That is the published timeline. Google still decides what it stores.

For a list, the account key is sent as `Authorization: Bearer`. Submit is `POST /api/v1/external/submit`. Status is `GET /api/v1/external/status` with the batch number.

Send the live URL here: [fastindex.io](https://fastindex.io/).
