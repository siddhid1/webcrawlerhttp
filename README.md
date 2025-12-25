# webcrawlerhttp

A small HTTP web crawler implemented in Node.js. This project provides
functions to crawl pages on the same host, extract links from HTML, and
normalize URLs. It's a compact learning example for building a simple
recursive crawler using modern Node.js APIs and jsdom for HTML parsing.

## Features

- Recursively crawl pages within the same hostname
- Extract absolute and relative links from HTML
- Basic URL normalization
- Unit tests for core utilities (`normalizeURL`, `getURLsFromHTML`)

## Prerequisites

- Node.js 18 or newer (the code uses the global `fetch` API available in Node 18+)
- npm (bundled with Node.js)

## Install

Clone the repo and install dependencies:

```bash
git clone https://github.com/siddhid1/webcrawlerhttp.git
cd webcrawlerhttp
npm install
```

## Usage

Start the crawler against a base URL. The crawler only follows links that
share the same hostname as the provided base URL.

Run with npm:

```bash
npm start -- https://example.com
```

Or with node directly:

```bash
node main.js https://example.com
```

Example output (truncated):

```
Starting Crawl of https://blog.boot.dev
actively crawling : https://blog.boot.dev/
[ 'blog.boot.dev', 1 ]
...
```

## Tests

This project uses Jest for unit tests. Run tests with:

```bash
npm test
```

## Project structure

- `main.js` — CLI entry; accepts the base URL and starts crawling
- `crawl.js` — crawler logic and helpers: `crawlPage`, `getURLsFromHTML`, `normalizeURL`
- `crawl.test.js` — Jest tests for the helper functions
- `package.json` — scripts and dependencies

## Notes & limitations

- The crawler only follows links on the same hostname (no cross-domain crawling).
- It does not currently check Content-Type to ensure the response is HTML — non-HTML responses may be skipped but are not fully handled.
- There is no rate-limiting, concurrency control, or politeness (robots.txt) handling. Use responsibly and avoid crawling sites without permission.
- The implementation is intentionally minimal for learning and demonstration purposes.

## Contributing

Contributions and improvements are welcome. For non-trivial changes please open an issue or a pull request. Suggested enhancements:

- add concurrency/queue management
- respect `robots.txt`
- add content-type checks and binary response handling

## License

This project is published under the ISC license (see `package.json`).

## Author / Contact

Project by @siddhid1. Open issues or pull requests on the GitHub repository.
