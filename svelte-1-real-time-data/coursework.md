# Coursework — Svelte Real-Time Transit Tracker (MBTA Boston)

## How This Works

- Each block has **foundation prerequisites** listed from `backlog.md`
- You cannot start a block until its prerequisites are marked `[x]` in `backlog.md`
- Prerequisites are cleared by passing a short interview/quiz with the AI agent
- The agent will not let you proceed if prerequisites are incomplete

---

## Block 0 — JavaScript Deep Review

> **Prerequisites:** None — start here
> **Goal:** Fill JS gaps identified in assessment (event loop, scoping, closures, async)

- [ ] `let`/`const`/`var` — block scope vs function scope vs global
- [ ] Closures — what they are, how they capture variables, practical uses
- [ ] Array methods — `.map()`, `.filter()`, `.reduce()`, `.find()`, `.some()`, `.every()`
- [ ] Destructuring — objects and arrays, nested, default values, renaming
- [ ] Spread/rest — `...` in function params, object/array copies, merging
- [ ] Template literals — interpolation, multiline, tagged templates
- [ ] ES modules — `import`/`export`, named vs default, dynamic imports
- [ ] Event loop — call stack, task queue, microtask queue, execution order
- [ ] Promises — creation, chaining, `.then()/.catch()/.finally()`, `Promise.all()`
- [ ] `async`/`await` — syntax, error handling with try/catch, sequential vs parallel
- [ ] `fetch()` API — GET/POST requests, headers, response parsing, error handling
- [ ] TypeScript intro — type annotations, interfaces, union types, generics basics

**Assessment:** Interview covering all 12 topics. Must pass to proceed.

---

## Block 1 — Svelte Fundamentals

> **Prerequisites from backlog.md:**
> - `[F-01]` CSS Flexbox
> - `[F-02]` CSS Grid
> - `[F-03]` Semantic HTML
> - `[F-04]` HTML Forms & Inputs
>
> **Goal:** Understand Svelte's component model and reactivity

- [ ] What is Svelte — compiler vs runtime, comparison with React/Vue
- [ ] Component anatomy — `<script>`, markup, `<style>`, single-file components
- [ ] Reactivity with runes — `$state`, `$derived`, `$effect` (Svelte 5)
- [ ] Templating — `{#if}`, `{:else}`, `{#each}`, `{@html}`, `{@const}`
- [ ] Event handling — `onclick`, event modifiers, custom events
- [ ] Bindings — `bind:value`, `bind:checked`, `bind:group`, two-way binding
- [ ] Component props — `$props()`, default values, spreading props
- [ ] Component composition — slots, `{@render}` snippets (Svelte 5)
- [ ] Lifecycle — `$effect` for mount/cleanup, `onMount` (legacy)
- [ ] Styling — scoped styles, `:global()`, CSS variables, dynamic classes

**Assessment:** Build a small interactive component from scratch. Interview on reactivity model.

---

## Block 2 — SvelteKit & Routing

> **Prerequisites from backlog.md:**
> - `[F-05]` DNS & HTTP end-to-end
> - `[F-06]` Browser rendering pipeline
> - `[F-07]` CSS Positioning & Layout
>
> **Goal:** Understand SvelteKit's file-based routing and SSR/CSR model

- [ ] SvelteKit project structure — `src/routes`, `src/lib`, `static`
- [ ] File-based routing — `+page.svelte`, directory = route segment
- [ ] Layouts — `+layout.svelte`, nested layouts, layout groups
- [ ] Dynamic routes — `[param]`, `[...rest]`, optional params
- [ ] Navigation — `<a>` tags, `goto()`, `$page` store
- [ ] Error pages — `+error.svelte`, error boundaries
- [ ] SSR vs CSR — what SvelteKit renders where and why
- [ ] `+page.ts` vs `+page.server.ts` — universal vs server-only load

**Assessment:** Set up project routing from scratch. Interview on SSR/CSR trade-offs.

---

## Block 3 — Data Loading & Server-Side

> **Prerequisites from backlog.md:**
> - `[F-08]` HTTP methods deep dive (GET, POST, PUT, PATCH, DELETE)
> - `[F-09]` REST API design principles
> - `[F-10]` Status codes & headers
> - `[F-11]` CORS — what it is, why it exists, how to handle it
>
> **Goal:** Master SvelteKit's server-side data patterns

- [ ] Load functions — `+page.server.ts` `load()`, return data to page
- [ ] Error handling in load — `error()`, `redirect()`
- [ ] Form actions — `+page.server.ts` `actions`, progressive enhancement
- [ ] API routes — `+server.ts`, `GET`/`POST` handlers, `json()` response
- [ ] Environment variables — `$env/static/private`, `$env/dynamic/private`
- [ ] Hooks — `handle`, `handleFetch`, `handleError` in `hooks.server.ts`
- [ ] Fetching external APIs — calling MBTA API from server-side load functions

**Assessment:** Build a working API route that proxies MBTA data. Interview on load function patterns.

---

## Block 4 — MBTA API & Real-Time Data

> **Prerequisites from backlog.md:**
> - `[F-12]` SSE vs WebSocket vs Polling — theory and trade-offs
> - `[F-13]` EventSource API
> - `[F-14]` Streaming protocols & data formats
>
> **Goal:** Connect to MBTA and display live transit data

- [ ] MBTA V3 API — endpoints, JSON:API format, query parameters, includes
- [ ] Fetching static data — routes, stops, schedules
- [ ] SSE streaming — connecting to MBTA's live vehicle feed via EventSource
- [ ] Svelte stores — writable, readable, derived stores for real-time state
- [ ] Store subscriptions — auto-subscribe with `$`, manual subscribe/unsubscribe
- [ ] Updating UI reactively — binding store data to components
- [ ] Error handling — reconnection logic, stale data detection
- [ ] Rate limiting awareness — respecting MBTA's 1,000 req/min limit

**Assessment:** Working live data feed displayed in the UI. Interview on SSE internals and store patterns.

---

## Block 5 — Maps & Geospatial Visualization

> **Prerequisites from backlog.md:**
> - `[F-15]` GeoJSON format
> - `[F-16]` Coordinate systems (lat/lng, projections)
> - `[F-17]` Canvas vs SVG rendering
> - `[F-18]` CSS Transitions & Animations
>
> **Goal:** Plot live transit vehicles on an interactive map

- [ ] Leaflet or MapLibre — setup, tile layers, basic map rendering
- [ ] Svelte + map library — component wrapper, lifecycle management
- [ ] Markers — plotting vehicle positions, custom icons per vehicle type
- [ ] Live updates — smoothly updating marker positions as SSE data arrives
- [ ] Popups & tooltips — vehicle info on click/hover
- [ ] Route overlays — drawing transit routes as polylines on the map
- [ ] Clustering — handling many markers without performance degradation
- [ ] Responsive maps — handling resize, mobile layout

**Assessment:** Working map with live-updating vehicle markers. Interview on geospatial concepts.

---

## Block 6 — Database & Historical Data

> **Prerequisites from backlog.md:**
> - `[F-19]` SQL joins — INNER, LEFT, RIGHT, CROSS
> - `[F-20]` GROUP BY, aggregations, HAVING
> - `[F-21]` Indexing — what it is, when to use, trade-offs
> - `[F-22]` Database migrations & schema design
>
> **Goal:** Persist transit data and enable historical queries

- [ ] Database choice — SQLite (dev) vs Postgres (prod), trade-offs
- [ ] ORM setup — Drizzle or Prisma with SvelteKit
- [ ] Schema design — vehicles, positions, routes, stops, snapshots
- [ ] Data ingestion — background job to store incoming SSE data
- [ ] Querying historical data — time ranges, route filtering, aggregations
- [ ] API endpoints for historical data — paginated, filterable
- [ ] Data cleanup — retention policies, archival strategies

**Assessment:** Working data pipeline (SSE -> DB -> query). Interview on schema decisions and SQL.

---

## Block 7 — Predictions & Data Analysis

> **Prerequisites from backlog.md:**
> - `[F-23]` Basic statistics — mean, median, standard deviation, percentiles
> - `[F-24]` Time series concepts — trends, seasonality, smoothing
>
> **Goal:** Analyze patterns and predict arrival times

- [ ] Analyzing historical patterns — peak hours, route reliability, delays
- [ ] Arrival time predictions — simple statistical model from historical data
- [ ] Data visualization — charts (Chart.js or D3), heatmaps, sparklines
- [ ] Comparison views — predicted vs actual, route performance rankings
- [ ] User-facing insights — "Route X is typically 5 min late at 8am"

**Assessment:** Working prediction feature with visualization. Interview on statistical approach.

---

## Block 8 — Polish & Deployment

> **Prerequisites from backlog.md:**
> - `[F-25]` CI/CD concepts
> - `[F-26]` Environment management (dev/staging/prod)
>
> **Goal:** Production-ready application

- [ ] Error handling — global error boundaries, toast notifications, fallbacks
- [ ] Loading states — skeletons, spinners, progressive loading
- [ ] Responsive design — mobile-first, breakpoints, touch interactions
- [ ] Accessibility — semantic markup, ARIA, keyboard navigation
- [ ] Performance — lazy loading, code splitting, image optimization
- [ ] Testing — unit tests (Vitest), component tests, E2E basics
- [ ] Deployment — adapter selection, Vercel/Cloudflare, environment config
- [ ] Monitoring — error tracking, basic analytics

**Assessment:** Deployed app. Final comprehensive interview.

---

## Progress Tracker

| Block | Status | Prerequisites Cleared | Assessment Passed |
|-------|--------|-----------------------|-------------------|
| 0 — JS Deep Review | `not started` | N/A | `no` |
| 1 — Svelte Fundamentals | `locked` | `no` | `no` |
| 2 — SvelteKit & Routing | `locked` | `no` | `no` |
| 3 — Data Loading & Server | `locked` | `no` | `no` |
| 4 — MBTA API & Real-Time | `locked` | `no` | `no` |
| 5 — Maps & Visualization | `locked` | `no` | `no` |
| 6 — Database & Historical | `locked` | `no` | `no` |
| 7 — Predictions & Analysis | `locked` | `no` | `no` |
| 8 — Polish & Deploy | `locked` | `no` | `no` |
