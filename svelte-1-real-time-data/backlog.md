# Foundation Backlog — Prerequisites for Svelte Coursework

## How This Works

- Each item has an ID (e.g. `[F-01]`) that maps to a block in `coursework.md`
- Items must be marked `[x]` (cleared) before you can start the block that requires them
- To clear an item: study it, then pass an interview/quiz with the AI agent
- Items are grouped by the block that first requires them, but knowledge carries forward
- **Related Topics** are adjacent knowledge to explore — not gated, but strongly recommended for holistic understanding

---

## Gate: Block 1 — Svelte Fundamentals

> These must be cleared before starting Block 1 in `coursework.md`

### `[F-01]` CSS Flexbox
- [ ] **Cleared**
- **What to learn:** `display: flex`, `flex-direction`, `justify-content`, `align-items`, `flex-wrap`, `gap`, `flex-grow`/`shrink`/`basis`, nested flex containers
- **Why it matters:** Every Svelte component layout uses flexbox. You'll use it for navbars, card layouts, centering, spacing — it's the primary layout tool.
- **Resources:** [Flexbox Froggy](https://flexboxfroggy.com/), MDN Flexbox Guide
- **Related Topics:**
  - `float` layout — the pre-flexbox era, why it existed, clearing floats, why it's legacy now
  - `display: table` layout — another pre-flexbox hack, table-cell vertical centering
  - CSS Container Queries — newer alternative to media queries, sizing based on parent not viewport
  - CSS `aspect-ratio` — maintaining proportions without padding hacks
  - Logical properties — `margin-inline`, `padding-block` (for internationalization/RTL support)
  - CSS `writing-mode` — vertical text, RTL languages, how it affects flex axes
  - Flexbox vs Grid — when to use which, one-dimensional vs two-dimensional thinking

### `[F-02]` CSS Grid
- [ ] **Cleared**
- **What to learn:** `display: grid`, `grid-template-columns`/`rows`, `grid-area`, `gap`, `fr` units, `auto-fill`/`auto-fit`, `minmax()`, implicit vs explicit grids
- **Why it matters:** Dashboard layouts, data tables, responsive card grids. The transit tracker will have a grid-based dashboard layout.
- **Resources:** [Grid Garden](https://cssgridgarden.com/), MDN CSS Grid Guide
- **Related Topics:**
  - Subgrid — `grid-template-columns: subgrid`, aligning nested grids to parent tracks
  - CSS Masonry layout — Pinterest-style layouts, the proposal for native CSS masonry
  - CSS `@container` queries with grid — responsive grid items based on container size
  - Named grid lines and areas — `grid-template-areas` for readable dashboard layouts
  - CSS `clamp()`, `min()`, `max()` — fluid sizing without media queries
  - Responsive design history — fixed → fluid → adaptive → responsive → intrinsic design
  - CSS custom properties (variables) with grid — dynamic grid systems

### `[F-03]` Semantic HTML
- [ ] **Cleared**
- **What to learn:** `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<figure>`, `<time>`, when to use `<div>` vs semantic tags
- **Why it matters:** Svelte components output HTML. Semantic markup improves accessibility, SEO, and code readability. SvelteKit's SSR means your HTML is what search engines and screen readers see.
- **Resources:** MDN HTML elements reference
- **Related Topics:**
  - ARIA roles and attributes — `role="button"`, `aria-label`, `aria-live`, `aria-hidden`, landmark roles
  - Accessibility tree — how browsers build it from the DOM, how screen readers traverse it
  - WAI-ARIA Authoring Practices — official patterns for common widgets (tabs, modals, menus)
  - HTML `<dialog>` element — native modal/non-modal dialogs, `showModal()`, backdrop
  - HTML `<details>`/`<summary>` — native collapsible content without JavaScript
  - `<template>` and `<slot>` — native web component primitives (compare with Svelte's approach)
  - Microdata and Schema.org — structured data for search engines, JSON-LD
  - Document outline algorithm — heading levels, sectioning content, screen reader navigation
  - Web Content Accessibility Guidelines (WCAG) — levels A, AA, AAA, compliance basics

### `[F-04]` HTML Forms & Inputs
- [ ] **Cleared**
- **What to learn:** `<form>`, `<input>` types (text, number, checkbox, radio, select), `<label>`, form submission, `FormData`, validation attributes (`required`, `pattern`, `min`/`max`)
- **Why it matters:** SvelteKit form actions are a core data mutation pattern. Svelte's `bind:value` and `bind:checked` work directly with form elements. The transit app will have route filters, search inputs, and settings forms.
- **Resources:** MDN Forms Guide
- **Related Topics:**
  - Constraint Validation API — `checkValidity()`, `setCustomValidity()`, `validity` state object
  - `<datalist>` — native autocomplete/typeahead without JavaScript libraries
  - `<output>` — associating calculated results with form inputs
  - `<fieldset>` and `<legend>` — grouping related controls, disabled fieldsets
  - `<input type="date/time/datetime-local">` — native date pickers, browser inconsistencies
  - `contenteditable` — making any element editable, building rich text editors
  - Form encoding types — `application/x-www-form-urlencoded` vs `multipart/form-data` vs `application/json`
  - Progressive enhancement — forms that work without JavaScript, then enhance with JS
  - `FormData` API deep dive — `append()`, `entries()`, `get()`, file uploads, serialization
  - `fetch()` with forms — sending FormData via fetch vs traditional form submission

---

## Gate: Block 2 — SvelteKit & Routing

> These must be cleared before starting Block 2 in `coursework.md`

### `[F-05]` DNS & HTTP End-to-End
- [ ] **Cleared**
- **What to learn:** Full request lifecycle — DNS resolution, TCP handshake, TLS/SSL negotiation, HTTP request/response structure, headers, body, status line. How a browser goes from URL to rendered page.
- **Why it matters:** SvelteKit runs on both server and client. Understanding the full HTTP cycle helps you reason about SSR, hydration, and when code runs where.
- **Resources:** MDN HTTP overview, "How DNS Works" comic (howdns.works)
- **Related Topics:**
  - DNS record types — A, AAAA, CNAME, MX, TXT, NS, SOA, SRV records and what each does
  - DNS caching layers — browser cache, OS cache, router cache, ISP resolver, TTL
  - CDNs (Content Delivery Networks) — how Cloudflare/Akamai/Fastly work, edge nodes, cache invalidation
  - HTTP/1.1 vs HTTP/2 vs HTTP/3 — multiplexing, header compression (HPACK), server push, QUIC protocol
  - TLS certificate chain — root CA, intermediate CA, leaf certificate, certificate transparency
  - TCP vs UDP — reliable vs unreliable, when each is used, TCP congestion control basics
  - QUIC protocol — UDP-based, built-in TLS, connection migration, why HTTP/3 uses it
  - `traceroute` and network debugging — how packets traverse the internet, hops, BGP routing basics
  - Service Workers — intercepting network requests, offline capabilities, cache strategies
  - Brotli vs gzip compression — content encoding, how servers compress responses

### `[F-06]` Browser Rendering Pipeline
- [ ] **Cleared**
- **What to learn:** HTML parsing -> DOM tree, CSS parsing -> CSSOM, render tree, layout (reflow), paint, composite. Critical rendering path. How JavaScript blocks rendering.
- **Why it matters:** Svelte compiles to DOM operations. Understanding the rendering pipeline helps you write performant components and understand why SSR improves perceived load time.
- **Resources:** web.dev "How browsers work", Chrome DevTools Performance tab
- **Related Topics:**
  - Virtual DOM vs real DOM — how React's approach differs from Svelte's compilation approach
  - `requestAnimationFrame` — frame timing, 60fps target, avoiding layout thrashing
  - Reflow triggers — which CSS properties cause layout recalculation, how to batch DOM reads/writes
  - Compositor layers — `will-change`, `transform`, `opacity`, GPU-accelerated rendering
  - Web Vitals — LCP (Largest Contentful Paint), FID/INP (Interaction to Next Paint), CLS (Cumulative Layout Shift)
  - `<script>` loading — `defer` vs `async`, module scripts, blocking vs non-blocking
  - Preloading and prefetching — `<link rel="preload">`, `<link rel="prefetch">`, `<link rel="preconnect">`
  - Hydration — what it is, why SSR apps need it, partial hydration, islands architecture
  - Paint flashing in DevTools — visualizing what the browser re-renders, diagnosing performance
  - CSS containment — `contain: layout`, `contain: paint`, isolating rendering work
  - `IntersectionObserver` — lazy loading, infinite scroll, visibility detection without scroll events

### `[F-07]` CSS Positioning & Layout
- [ ] **Cleared**
- **What to learn:** `position: static`/`relative`/`absolute`/`fixed`/`sticky`, stacking context (`z-index`), `display: none` vs `visibility: hidden`, `overflow`, box model (`margin`/`padding`/`border`), `box-sizing`
- **Why it matters:** Map overlays, tooltips, sticky headers, modal dialogs — the transit tracker UI needs precise positioning. Absolute/fixed positioning is critical for map marker popups.
- **Resources:** MDN CSS Layout Guide, CSS Tricks "A Complete Guide to CSS Layout"
- **Related Topics:**
  - Stacking context deep dive — what creates a new stacking context (opacity, transform, filter, isolation)
  - `position: sticky` gotchas — overflow containers, threshold values, nested sticky elements
  - CSS `anchor()` positioning — the new anchor positioning spec for tooltips/popovers
  - `<popover>` API — native popovers without JavaScript positioning libraries
  - Margin collapsing — when/why margins collapse, how to prevent it, BFC (Block Formatting Context)
  - `display: contents` — removing a box from layout while keeping its children
  - CSS `inset` shorthand — `inset: 0` vs `top:0; right:0; bottom:0; left:0`
  - Scroll snap — `scroll-snap-type`, `scroll-snap-align`, carousel-like behavior without JS
  - `overflow-anchor` — scroll anchoring, preventing layout shift during content loading

---

## Gate: Block 3 — Data Loading & Server-Side

> These must be cleared before starting Block 3 in `coursework.md`

### `[F-08]` HTTP Methods Deep Dive
- [ ] **Cleared**
- **What to learn:** `GET`, `POST`, `PUT`, `PATCH`, `DELETE` — semantics, idempotency, safe methods, when to use each. `HEAD`, `OPTIONS` for completeness. Request body conventions per method.
- **Why it matters:** SvelteKit API routes (`+server.ts`) export functions named by HTTP method. Form actions use POST. Understanding method semantics is essential for correct API design.
- **Resources:** MDN HTTP Methods, REST API Tutorial
- **Related Topics:**
  - Idempotency deep dive — why PUT is idempotent but POST isn't, retry safety, idempotency keys
  - `PATCH` formats — JSON Merge Patch (RFC 7396) vs JSON Patch (RFC 6902), partial updates
  - Content negotiation — `Accept` header, `Content-Type`, `406 Not Acceptable`, serving JSON vs HTML
  - GraphQL — query language alternative to REST, single endpoint, typed schema, over/under-fetching
  - gRPC — binary protocol (protobuf), HTTP/2 based, streaming, when to use over REST
  - tRPC — type-safe APIs without schema definition, popular in TypeScript/full-stack apps
  - WebDAV — extended HTTP methods (`PROPFIND`, `MKCOL`, `COPY`, `MOVE`) for file management
  - HTTP caching — `ETag`, `If-None-Match`, `Last-Modified`, `If-Modified-Since`, `304 Not Modified`

### `[F-09]` REST API Design Principles
- [ ] **Cleared**
- **What to learn:** Resource-based URLs, plural nouns (`/users`, not `/getUsers`), CRUD mapping to methods, nested resources (`/users/:id/orders`), query params for filtering/sorting/pagination, versioning, HATEOAS basics
- **Why it matters:** You'll design API routes in SvelteKit and consume the MBTA API (which follows JSON:API spec, a REST variant). Good REST understanding helps you design clean endpoints.
- **Resources:** restfulapi.net, JSON:API specification
- **Related Topics:**
  - JSON:API specification — compound documents, relationships, includes, sparse fieldsets (MBTA uses this)
  - HAL (Hypertext Application Language) — another hypermedia format, `_links`, `_embedded`
  - OpenAPI / Swagger — API specification format, auto-generated docs, code generation
  - API pagination patterns — offset-based, cursor-based, keyset pagination, trade-offs
  - API rate limiting strategies — token bucket, sliding window, leaky bucket, `429` + `Retry-After`
  - API versioning strategies — URL versioning (`/v2/`), header versioning, no versioning (evolution)
  - REST maturity model (Richardson) — Level 0 (RPC) through Level 3 (HATEOAS)
  - Backend-for-Frontend (BFF) pattern — API tailored for specific clients, SvelteKit as a BFF
  - API Gateway pattern — aggregation, auth, rate limiting, routing in microservices

### `[F-10]` Status Codes & Headers
- [ ] **Cleared**
- **What to learn:** 1xx informational, 2xx success (200, 201, 204), 3xx redirect (301, 302, 304), 4xx client error (400, 401, 403, 404, 409, 429), 5xx server error (500, 502, 503). Common headers: `Content-Type`, `Authorization`, `Cache-Control`, `Accept`, `Set-Cookie`
- **Why it matters:** SvelteKit load functions and API routes return status codes. The MBTA API uses rate limiting (429). Error handling depends on understanding what status codes mean.
- **Resources:** MDN HTTP Status Codes, HTTP Cats (http.cat)
- **Related Topics:**
  - `Cache-Control` deep dive — `no-cache` vs `no-store`, `max-age`, `stale-while-revalidate`, `s-maxage`
  - Authentication headers — `Authorization: Bearer`, `Authorization: Basic`, API key patterns
  - Security headers — `Content-Security-Policy`, `X-Frame-Options`, `Strict-Transport-Security`, `X-Content-Type-Options`
  - Cookie attributes — `HttpOnly`, `Secure`, `SameSite`, `Path`, `Domain`, `Max-Age`, `__Host-` prefix
  - `103 Early Hints` — new status code for preloading hints before the full response
  - `Content-Disposition` — file downloads (`attachment`), inline display, filename encoding
  - Conditional requests — `If-Match`, `If-None-Match`, `If-Modified-Since`, optimistic concurrency
  - `Vary` header — cache key variation, why `Vary: Accept-Encoding` matters for CDNs
  - `Link` header — preloading, pagination links, rel types

### `[F-11]` CORS
- [ ] **Cleared**
- **What to learn:** Same-origin policy, what CORS is and why browsers enforce it, preflight requests (`OPTIONS`), `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, simple vs preflighted requests. How to handle CORS in SvelteKit.
- **Why it matters:** Calling the MBTA API from the browser will hit CORS restrictions. SvelteKit's server-side load functions bypass CORS (server-to-server). Understanding this shapes where you make API calls.
- **Resources:** MDN CORS guide, web.dev CORS article
- **Related Topics:**
  - Same-origin policy deep dive — what defines an "origin" (scheme + host + port), `document.domain`
  - CORS credentials — `credentials: 'include'`, `Access-Control-Allow-Credentials`, cookie sending rules
  - CSRF (Cross-Site Request Forgery) — why same-origin policy exists, CSRF tokens, `SameSite` cookies
  - CSP (Content Security Policy) — blocking inline scripts, trusted sources, `nonce`, `strict-dynamic`
  - Subresource Integrity (SRI) — `integrity` attribute on `<script>` and `<link>`, hash verification
  - `crossorigin` attribute — on `<script>`, `<img>`, `<link>`, CORS mode for resources
  - JSONP — the pre-CORS hack, `<script>` tag injection, why it's a security risk
  - Proxy patterns — server-side API proxy to avoid CORS, SvelteKit as a proxy layer
  - `postMessage` API — cross-origin communication between windows/iframes

---

## Gate: Block 4 — MBTA API & Real-Time Data

> These must be cleared before starting Block 4 in `coursework.md`

### `[F-12]` SSE vs WebSocket vs Polling
- [ ] **Cleared**
- **What to learn:** Polling (simple, long), Server-Sent Events (SSE), WebSockets — how each works at the protocol level. One-way vs bidirectional. Connection lifecycle. When to use which. Resource costs and scalability trade-offs.
- **Why it matters:** The MBTA API uses SSE for real-time data. Understanding the alternatives helps you appreciate why SSE is chosen and when you might need WebSockets instead (e.g., adding more cities later).
- **Resources:** MDN EventSource, MDN WebSocket, web.dev "Streams" article
- **Related Topics:**
  - HTTP/2 Server Push — how it differs from SSE, why it was mostly deprecated
  - WebTransport API — next-gen bidirectional transport over HTTP/3, unreliable datagrams, ordered streams
  - gRPC streaming — server streaming, client streaming, bidirectional streaming over HTTP/2
  - MQTT protocol — lightweight pub/sub for IoT, QoS levels, retained messages, used in transit systems
  - Socket.IO — WebSocket library with fallbacks, rooms, namespaces, auto-reconnection, why it's not raw WS
  - Long polling mechanics — `comet` pattern, hanging GET, connection recycling, Bayeux protocol
  - Server resource costs — connection limits, memory per connection, kernel tuning (`ulimit`), C10K problem
  - Scaling WebSockets — sticky sessions, Redis pub/sub for multi-server, connection migration
  - Web Push API — push notifications, service workers, notification permission, VAPID keys
  - `ReadableStream` API — browser streaming, `TransformStream`, piping, backpressure

### `[F-13]` EventSource API
- [ ] **Cleared**
- **What to learn:** `new EventSource(url)`, `onmessage`, `onerror`, `onopen`, named events with `addEventListener`, automatic reconnection, `Last-Event-ID` header, closing connections, browser support.
- **Why it matters:** This is the browser API you'll use to connect to MBTA's SSE streams. It handles reconnection automatically, but you need to understand its behavior to build robust real-time features.
- **Resources:** MDN EventSource API, HTML spec SSE section
- **Related Topics:**
  - `fetch()` with `ReadableStream` — alternative to EventSource for SSE, more control over parsing
  - EventSource polyfills — `eventsource` npm package for Node.js, custom headers (EventSource can't set headers)
  - Reconnection strategies — exponential backoff, jitter, max retries, circuit breaker pattern
  - Connection lifecycle management — memory leaks from unclosed connections, cleanup in Svelte `$effect`
  - `AbortController` — cancelling fetch requests, aborting streams, timeout patterns
  - Heartbeat/keepalive — detecting dead connections, server-side ping events, timeout detection
  - Browser connection limits — 6 connections per origin (HTTP/1.1), multiplexing in HTTP/2
  - `BroadcastChannel` API — sharing real-time data between browser tabs without duplicate connections
  - `SharedWorker` — single worker shared across tabs, single SSE connection for all tabs

### `[F-14]` Streaming Protocols & Data Formats
- [ ] **Cleared**
- **What to learn:** SSE text format (`data:`, `event:`, `id:`, `retry:`), JSON streaming, newline-delimited JSON (NDJSON), GTFS-realtime protobuf basics (what it is, why transit uses it), JSON:API format (MBTA uses this).
- **Why it matters:** MBTA sends SSE events containing JSON:API formatted data. Understanding both the transport (SSE) and the payload format (JSON:API) is necessary to parse and use the data correctly.
- **Resources:** JSON:API spec (jsonapi.org), GTFS-realtime reference (Google)
- **Related Topics:**
  - Protocol Buffers (protobuf) — binary serialization, `.proto` files, schema evolution, vs JSON size/speed
  - MessagePack — binary JSON alternative, smaller payloads, used in some real-time systems
  - Apache Avro — schema-based serialization, schema registry, used in event streaming (Kafka)
  - GTFS static vs GTFS-realtime — schedule data vs live updates, how agencies publish both
  - SIRI (Service Interface for Real Time Information) — European transit standard, XML-based, used by MTA buses
  - JSON:API compound documents — sideloading related resources, `include` parameter, reducing API calls
  - GraphQL subscriptions — real-time data via GraphQL, uses WebSocket under the hood
  - Apache Kafka / event streaming — log-based messaging, topics, partitions, consumer groups, how transit agencies use it internally
  - CBOR (Concise Binary Object Representation) — binary data format, IoT usage, RFC 8949
  - Newline-delimited formats — NDJSON, JSON Lines, CSV streaming, log file formats

---

## Gate: Block 5 — Maps & Geospatial Visualization

> These must be cleared before starting Block 5 in `coursework.md`

### `[F-15]` GeoJSON Format
- [ ] **Cleared**
- **What to learn:** GeoJSON structure — `Feature`, `FeatureCollection`, geometry types (`Point`, `LineString`, `Polygon`, `MultiPoint`), `properties` object, coordinate order (`[lng, lat]` not `[lat, lng]`).
- **Why it matters:** Transit route shapes and stop locations come as geographic coordinates. Map libraries consume GeoJSON natively. You'll convert MBTA data to GeoJSON for route overlays.
- **Resources:** geojson.org, RFC 7946, geojson.io (interactive editor)
- **Related Topics:**
  - TopoJSON — topology-encoded GeoJSON, shared arcs, ~80% smaller files, used for country/state boundaries
  - KML / KMZ — Google Earth format, XML-based, styling built-in, historical significance
  - Shapefile (.shp) — legacy GIS format, multi-file, still widely used by government agencies
  - GeoPackage (.gpkg) — SQLite-based geospatial format, replacing shapefiles, OGC standard
  - WKT (Well-Known Text) — text representation of geometry (`POINT(0 0)`), used in PostGIS/SQL
  - Mapbox Vector Tiles (MVT) — binary vector tile format, protobuf-based, efficient map rendering
  - GeoJSON-LD — linked data extension, semantic web integration
  - Turf.js — geospatial analysis in JavaScript, buffer, intersect, distance, area calculations
  - Right-hand rule — polygon winding order in GeoJSON, exterior vs interior rings
  - Simplification algorithms — Douglas-Peucker, Visvalingam, reducing geometry complexity for web

### `[F-16]` Coordinate Systems
- [ ] **Cleared**
- **What to learn:** Latitude/longitude (WGS84), degrees vs radians, map projections (Mercator, Web Mercator/EPSG:3857), why maps distort at high latitudes, tile coordinate systems (z/x/y), bounding boxes.
- **Why it matters:** Every vehicle position from MBTA is a lat/lng pair. Understanding coordinate systems prevents bugs (like swapping lat/lng) and helps you work with map zoom levels and bounding boxes for queries.
- **Resources:** MapSchool (mapschool.io), Leaflet documentation
- **Related Topics:**
  - EPSG codes — coordinate reference system registry, EPSG:4326 (GPS), EPSG:3857 (web maps)
  - Map projections gallery — Mercator, Robinson, Albers, Lambert, equal-area vs conformal vs equidistant
  - Haversine formula — calculating distance between two lat/lng points on a sphere
  - Vincenty's formulae — more accurate distance on an ellipsoid, geodesic calculations
  - Geohashing — encoding lat/lng into a single string, spatial indexing, proximity search
  - H3 (Uber's hexagonal grid) — hierarchical spatial index, hex-based tiling, aggregation
  - S2 Geometry (Google) — sphere-based spatial indexing, cells, used in Google Maps
  - UTM (Universal Transverse Mercator) — meter-based coordinates, zone system, surveying
  - Slippy map tiles — z/x/y convention, tile servers, OpenStreetMap tile URLs, tile math
  - Datum vs projection — WGS84 is a datum (shape of Earth), Mercator is a projection (flat map)

### `[F-17]` Canvas vs SVG Rendering
- [ ] **Cleared**
- **What to learn:** SVG — vector, DOM-based, CSS-stylable, event handling per element, good for <1000 elements. Canvas — raster, pixel-based, no DOM, better for many elements, needs manual hit detection. WebGL for 3D/heavy rendering.
- **Why it matters:** Map libraries use canvas (Leaflet) or WebGL (MapLibre GL). Choosing markers vs canvas rendering affects performance when tracking hundreds of vehicles. Charts use SVG (D3) or canvas (Chart.js).
- **Resources:** MDN Canvas tutorial, MDN SVG tutorial
- **Related Topics:**
  - WebGL fundamentals — shaders (vertex, fragment), GPU pipeline, GLSL, buffers, textures
  - WebGPU — next-gen GPU API, compute shaders, replacing WebGL, more powerful
  - Three.js — 3D rendering library, scenes, cameras, meshes, lights, 3D transit visualization
  - D3.js — data-driven DOM manipulation, scales, axes, force simulations, SVG-based charts
  - `OffscreenCanvas` — canvas rendering in Web Workers, non-blocking heavy rendering
  - SVG filters — `<filter>`, blur, drop shadow, color matrix, compositing
  - Canvas performance — `requestAnimationFrame`, object pooling, dirty rectangle rendering
  - `Path2D` — reusable canvas paths, hit testing with `isPointInPath()`
  - SVG `<use>` and symbols — sprite sheets, icon systems, reusable SVG components
  - PixiJS — high-performance 2D WebGL renderer, sprite-based, particle systems
  - Rendering budget — 16ms per frame for 60fps, profiling tools, bottleneck identification

### `[F-18]` CSS Transitions & Animations
- [ ] **Cleared**
- **What to learn:** `transition` property (duration, timing function, delay), `@keyframes` and `animation`, `transform` (translate, scale, rotate), `opacity`, hardware-accelerated properties, `prefers-reduced-motion`, Svelte transitions (`transition:`, `in:`, `out:`)
- **Why it matters:** Smooth marker movement on the map, loading animations, UI transitions between views. Svelte has a built-in transition system that you'll use extensively.
- **Resources:** MDN CSS Transitions, Svelte tutorial transitions section
- **Related Topics:**
  - CSS `@starting-style` — animating from `display: none`, entry animations without JS
  - View Transitions API — `document.startViewTransition()`, page-level transitions, SPA morphing
  - Web Animations API (WAAPI) — `element.animate()`, JS-controlled animations, more powerful than CSS
  - FLIP technique — First, Last, Invert, Play — smooth layout animations, used by Svelte `animate:`
  - Easing functions — cubic-bezier curves, spring physics, `steps()`, custom easing
  - CSS `motion-path` — animating elements along SVG paths (`offset-path`, `offset-distance`)
  - Lottie — After Effects animations exported as JSON, `lottie-web` player, Bodymovin
  - `prefers-reduced-motion` deep dive — accessibility, vestibular disorders, implementing alternatives
  - GPU compositing — which properties are "cheap" to animate (transform, opacity) vs "expensive" (width, height)
  - Svelte `animate:flip` — animating list reordering, keyed each blocks, crossfade transitions
  - Spring and tweened stores in Svelte — physics-based animations, `svelte/motion`

---

## Gate: Block 6 — Database & Historical Data

> These must be cleared before starting Block 6 in `coursework.md`

### `[F-19]` SQL Joins
- [ ] **Cleared**
- **What to learn:** `INNER JOIN`, `LEFT JOIN` (and why it's the most common), `RIGHT JOIN`, `CROSS JOIN`, `FULL OUTER JOIN`, self joins, joining on multiple conditions, table aliases.
- **Why it matters:** Querying historical transit data requires joining vehicles with positions, routes with stops, and snapshots across time ranges. Every non-trivial query will use joins.
- **Resources:** SQLBolt (sqlbolt.com), "Visual Guide to SQL Joins"
- **Related Topics:**
  - NoSQL databases — document stores (MongoDB), key-value (Redis), column-family (Cassandra), when SQL isn't the answer
  - Graph databases — Neo4j, transit networks as graphs, Cypher query language, relationship-first modeling
  - `LATERAL JOIN` — correlated subqueries as joins, powerful for "top N per group" queries
  - Anti-joins — `LEFT JOIN ... WHERE IS NULL` vs `NOT EXISTS` vs `NOT IN`, performance differences
  - Join algorithms — nested loop, hash join, merge join, how query planners choose
  - Materialized views — precomputed joins, refresh strategies, trade-off of storage vs query speed
  - Denormalization — intentionally duplicating data to avoid joins, read-heavy optimization
  - Common Table Expressions (CTEs) — `WITH` clause, recursive CTEs for hierarchical data (transit routes)
  - Set operations — `UNION`, `INTERSECT`, `EXCEPT`, combining result sets

### `[F-20]` GROUP BY, Aggregations, HAVING
- [ ] **Cleared**
- **What to learn:** `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`, `GROUP BY` single and multiple columns, `HAVING` vs `WHERE`, `DISTINCT`, window functions basics (`ROW_NUMBER()`, `RANK()`).
- **Why it matters:** "Average delay per route", "busiest stops by hour", "vehicle count per time window" — all the analytical queries for predictions require aggregations.
- **Resources:** SQLBolt, Mode Analytics SQL tutorial
- **Related Topics:**
  - Window functions deep dive — `OVER()`, `PARTITION BY`, `ORDER BY`, frame specification (`ROWS BETWEEN`)
  - `LAG()` / `LEAD()` — accessing previous/next rows, calculating deltas (time between positions)
  - Running totals and moving averages — `SUM() OVER (ORDER BY ... ROWS BETWEEN)`
  - `ROLLUP` and `CUBE` — multi-level aggregation, subtotals, cross-tabulation
  - `GROUPING SETS` — flexible multi-dimensional aggregation, SQL OLAP operations
  - Approximate aggregations — `APPROX_COUNT_DISTINCT`, HyperLogLog, sketch-based counting
  - OLAP vs OLTP — analytical queries vs transactional queries, data warehouse vs operational DB
  - Pivot/unpivot — transforming rows to columns and back, `CROSSTAB` in PostgreSQL
  - `FILTER` clause — conditional aggregation (`COUNT(*) FILTER (WHERE status = 'late')`)
  - Statistical aggregates in SQL — `STDDEV()`, `VARIANCE()`, `PERCENTILE_CONT()`, `CORR()`

### `[F-21]` Indexing
- [ ] **Cleared**
- **What to learn:** What an index is (B-tree), primary key vs secondary index, composite indexes, when indexes help (reads) vs hurt (writes), `EXPLAIN`/query plans, covering indexes, index selectivity.
- **Why it matters:** Historical position data grows fast. Without proper indexes, queries on timestamps and route IDs will become slow. Understanding indexing is the #1 database performance skill.
- **Resources:** Use The Index, Luke (use-the-index-luke.com)
- **Related Topics:**
  - B-tree internals — balanced tree structure, leaf nodes, branching factor, page size, disk I/O
  - Hash indexes — O(1) lookup, equality only (no range queries), when to use
  - GiST and SP-GiST indexes — generalized search trees, used for geospatial queries in PostGIS
  - GIN indexes — inverted indexes, full-text search, JSONB containment queries in Postgres
  - BRIN indexes — block range indexes, very small, great for time-series data (sequential inserts)
  - Partial indexes — `CREATE INDEX ... WHERE condition`, indexing only relevant rows
  - Expression indexes — `CREATE INDEX ... ON (LOWER(name))`, indexing computed values
  - Index-only scans — covering indexes, `INCLUDE` columns, avoiding table lookups
  - `EXPLAIN ANALYZE` — reading query plans, sequential scan vs index scan, cost estimation
  - Write amplification — how indexes slow down inserts/updates, WAL (Write-Ahead Log)
  - Vacuuming (PostgreSQL) — dead tuples, bloat, autovacuum, `VACUUM FULL` vs regular
  - Connection pooling — PgBouncer, why database connections are expensive, pool sizing

### `[F-22]` Database Migrations & Schema Design
- [ ] **Cleared**
- **What to learn:** Schema design process — entities, relationships, normalization (1NF, 2NF, 3NF), denormalization trade-offs. Migrations — what they are, up/down, version tracking, why you never edit a deployed migration.
- **Why it matters:** The transit tracker schema must handle vehicles, positions over time, routes, stops, and predictions. Getting the schema right early prevents painful migrations later. Drizzle/Prisma both use migration systems.
- **Resources:** Database normalization Wikipedia article, Prisma/Drizzle migration docs
- **Related Topics:**
  - Entity-Relationship (ER) diagrams — crow's foot notation, cardinality (1:1, 1:N, M:N), tools (dbdiagram.io)
  - Temporal tables — `SYSTEM_TIME`, `FOR PORTION OF`, tracking data changes over time, bitemporal modeling
  - TimescaleDB — PostgreSQL extension for time-series data, hypertables, automatic partitioning
  - Table partitioning — range partitioning (by date), list partitioning, partition pruning
  - Soft deletes vs hard deletes — `deleted_at` column, tombstones, legal requirements for data retention
  - UUIDs vs auto-increment — distributed ID generation, UUIDv7 (time-ordered), `ULID`, snowflake IDs
  - JSON columns — `JSONB` in Postgres, when to use structured columns vs JSON, hybrid schemas
  - Database triggers — before/after insert/update/delete, audit logging, derived data
  - Schema versioning strategies — sequential numbering, timestamp-based, content-addressable
  - Zero-downtime migrations — expand-contract pattern, backfill strategies, online schema changes
  - Flyway vs Liquibase vs Drizzle vs Prisma — migration tool comparison, SQL-first vs ORM-managed

---

## Gate: Block 7 — Predictions & Data Analysis

> These must be cleared before starting Block 7 in `coursework.md`

### `[F-23]` Basic Statistics
- [ ] **Cleared**
- **What to learn:** Mean, median, mode, standard deviation, variance, percentiles (p50, p95, p99), normal distribution, outlier detection, correlation basics.
- **Why it matters:** Predicting arrival times requires statistical analysis of historical data. "Route X averages 12 min with a standard deviation of 3 min" is the foundation of your prediction model.
- **Resources:** Khan Academy Statistics, Seeing Theory (seeing-theory.brown.edu)
- **Related Topics:**
  - Central Limit Theorem — why averages of samples become normally distributed, sample size effects
  - Bayesian vs Frequentist statistics — prior beliefs, posterior probability, different philosophies
  - Confidence intervals — 95% CI, margin of error, what it actually means (and doesn't mean)
  - Hypothesis testing — null hypothesis, p-values, Type I/II errors, significance levels
  - Regression — linear regression, R-squared, residuals, predicting continuous values
  - Probability distributions — uniform, normal, Poisson (events per time), exponential (time between events)
  - Monte Carlo simulation — random sampling to estimate outcomes, transit delay modeling
  - Anomaly detection — Z-score method, IQR method, isolation forests, detecting unusual transit patterns
  - A/B testing — statistical significance, sample size calculation, experimentation frameworks
  - Simpson's Paradox — when aggregate trends reverse at group level, transit data pitfalls

### `[F-24]` Time Series Concepts
- [ ] **Cleared**
- **What to learn:** What a time series is, trends (long-term direction), seasonality (daily/weekly patterns), noise, moving averages (SMA, EMA), smoothing, resampling (1-min data -> hourly averages), stationarity basics.
- **Why it matters:** Transit data is a time series. Rush hour patterns, weekend vs weekday differences, seasonal variations — recognizing and extracting these patterns is how you build predictions.
- **Resources:** "Forecasting: Principles and Practice" (otexts.com/fpp3), Khan Academy
- **Related Topics:**
  - ARIMA models — AutoRegressive Integrated Moving Average, Box-Jenkins method, classic forecasting
  - Prophet (Facebook/Meta) — time series forecasting library, handles holidays, changepoints, seasonality
  - Fourier transforms — decomposing signals into frequencies, finding periodic patterns in transit data
  - Kalman filter — state estimation, noise filtering, GPS smoothing, real-time position prediction
  - Exponential smoothing — Holt-Winters method, level + trend + seasonality decomposition
  - Autocorrelation — ACF/PACF plots, identifying lag relationships, model selection
  - Change point detection — identifying when patterns shift (new schedule, construction, etc.)
  - Interpolation and imputation — handling missing data, linear interpolation, forward/backward fill
  - Resampling techniques — upsampling, downsampling, handling irregular time series (GPS data)
  - Time zones and daylight saving — `Temporal` API, `Intl.DateTimeFormat`, UTC storage, display conversion
  - Sliding window algorithms — fixed-size windows, tumbling vs hopping, stream processing concepts

---

## Gate: Block 8 — Polish & Deployment

> These must be cleared before starting Block 8 in `coursework.md`

### `[F-25]` CI/CD Concepts
- [ ] **Cleared**
- **What to learn:** Continuous Integration — automated testing on every push, build pipelines, linting, type checking. Continuous Deployment — auto-deploy on merge to main, staging environments, rollback strategies. GitHub Actions basics.
- **Why it matters:** Before deploying the transit tracker, you need automated checks to prevent deploying broken builds. GitHub Actions will run your tests and deploy automatically.
- **Resources:** GitHub Actions docs, Martin Fowler's CI article
- **Related Topics:**
  - GitHub Actions deep dive — workflows, jobs, steps, matrix builds, caching, artifacts, secrets
  - Other CI systems — GitLab CI, CircleCI, Jenkins, Travis CI, Buildkite — trade-offs and philosophy
  - Docker basics — containers vs VMs, Dockerfile, images, layers, Docker Compose, why it matters for CI
  - Infrastructure as Code (IaC) — Terraform, Pulumi, declarative infrastructure, state management
  - Blue-green deployments — zero-downtime, two environments, traffic switching
  - Canary deployments — gradual rollout, percentage-based routing, automatic rollback
  - Feature flags — LaunchDarkly, Unleash, trunk-based development, decoupling deploy from release
  - Trunk-based development — short-lived branches, feature flags over feature branches
  - GitOps — Git as single source of truth for infrastructure, ArgoCD, Flux
  - Dependency scanning — Dependabot, Snyk, npm audit, supply chain security
  - Semantic versioning — MAJOR.MINOR.PATCH, breaking changes, conventional commits, auto-release

### `[F-26]` Environment Management
- [ ] **Cleared**
- **What to learn:** Development vs staging vs production environments, environment variables (`.env` files), secrets management, feature flags, configuration per environment, why secrets never go in code/git.
- **Why it matters:** Your MBTA API key, database credentials, and deployment configs differ per environment. SvelteKit has a specific env module system (`$env/static/private`, `$env/dynamic/private`) built for this.
- **Resources:** 12-Factor App (12factor.net), SvelteKit env docs
- **Related Topics:**
  - 12-Factor App methodology — all 12 factors, not just config, how SvelteKit aligns
  - `.env` file ecosystem — `dotenv`, `.env.local`, `.env.production`, load order, precedence rules
  - Secrets management services — AWS Secrets Manager, HashiCorp Vault, Doppler, 1Password CLI
  - `.gitignore` patterns — what to exclude, global gitignore, `.env` files, `node_modules`, build output
  - `process.env` vs `import.meta.env` — Node.js vs Vite environment variable access, build-time vs runtime
  - Platform-specific env handling — Vercel env vars, Cloudflare Workers secrets, Netlify env
  - Configuration as Code — YAML configs, TOML (Rust ecosystem), JSON configs, type-safe config validation
  - Environment parity — why dev should match prod, Docker for local development, seed data
  - `.env.vault` — encrypted env files, team sharing, Dotenv Vault, secrets in CI
  - Runtime configuration — loading config at startup vs build time, dynamic vs static env in SvelteKit
  - `zod` for config validation — parsing and validating env vars at startup, fail-fast on missing config

---

## Progress Summary

| ID | Topic | Required By | Cleared | Related Topics Count |
|----|-------|-------------|---------|---------------------|
| F-01 | CSS Flexbox | Block 1 | [ ] | 7 |
| F-02 | CSS Grid | Block 1 | [ ] | 7 |
| F-03 | Semantic HTML | Block 1 | [ ] | 9 |
| F-04 | HTML Forms & Inputs | Block 1 | [ ] | 10 |
| F-05 | DNS & HTTP End-to-End | Block 2 | [ ] | 10 |
| F-06 | Browser Rendering Pipeline | Block 2 | [ ] | 11 |
| F-07 | CSS Positioning & Layout | Block 2 | [ ] | 9 |
| F-08 | HTTP Methods Deep Dive | Block 3 | [ ] | 8 |
| F-09 | REST API Design Principles | Block 3 | [ ] | 9 |
| F-10 | Status Codes & Headers | Block 3 | [ ] | 9 |
| F-11 | CORS | Block 3 | [ ] | 9 |
| F-12 | SSE vs WebSocket vs Polling | Block 4 | [ ] | 10 |
| F-13 | EventSource API | Block 4 | [ ] | 9 |
| F-14 | Streaming Protocols & Data Formats | Block 4 | [ ] | 10 |
| F-15 | GeoJSON Format | Block 5 | [ ] | 10 |
| F-16 | Coordinate Systems | Block 5 | [ ] | 10 |
| F-17 | Canvas vs SVG Rendering | Block 5 | [ ] | 11 |
| F-18 | CSS Transitions & Animations | Block 5 | [ ] | 11 |
| F-19 | SQL Joins | Block 6 | [ ] | 9 |
| F-20 | GROUP BY & Aggregations | Block 6 | [ ] | 10 |
| F-21 | Indexing | Block 6 | [ ] | 12 |
| F-22 | Migrations & Schema Design | Block 6 | [ ] | 11 |
| F-23 | Basic Statistics | Block 7 | [ ] | 10 |
| F-24 | Time Series Concepts | Block 7 | [ ] | 11 |
| F-25 | CI/CD Concepts | Block 8 | [ ] | 11 |
| F-26 | Environment Management | Block 8 | [ ] | 11 |

**Total related topics across all items: ~252**
