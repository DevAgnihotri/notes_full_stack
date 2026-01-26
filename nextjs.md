# **1. Core Fundamentals**

---

## **What is Next.js**

* **Next.js is a React-based full-stack framework** for building modern web apps.
* It adds **routing, server rendering, SEO, backend APIs, file system routing, data fetching, and performance tools** on top of React.
* React alone does UI only, while Next.js gives you the **complete toolkit**.

### **Key Capabilities**

✔ Server-Side Rendering (SSR)
✔ Static Site Generation (SSG)
✔ API Routes (backend)
✔ File-Based Routing
✔ Image Optimization
✔ Built-in SEO Tools
✔ Data Fetching & Caching
✔ Full-stack (Server + Client)

---

## **Why Next.js over React**

React is **UI-only**, meaning:

* No routing system by default
* No SEO optimization
* No server rendering
* No backend APIs
* No file-based structure
* No image optimization

Next.js solves these problems.

### **Comparison Table**

| Feature            | React              | Next.js            |
| ------------------ | ------------------ | ------------------ |
| Routing            | ❌ manual libraries | ✅ built-in         |
| SEO                | ❌ weak (CSR)       | ✅ strong (SSR/SSG) |
| Server Rendering   | ❌ no               | ✅ yes              |
| API Layer          | ❌ no               | ✅ yes              |
| Image Optimization | ❌ no               | ✅ yes              |
| File-based Routing | ❌ no               | ✅ yes              |

➡ **Simple meaning:** Next.js = React + Routing + Server + SEO + Best Speed

---

## **Next.js Architecture**

Next.js architecture combines:

### **(1) Client Layer**

* Browser-side components
* Handles UI, interactions, events

### **(2) Server Layer**

* Runs code on server
* Handles data fetching, authentication, DB

### **(3) Build System**

* Compiles React into optimized JS + HTML
* Handles bundling, code splitting, and caching

### **(4) Routing System**

* File-based routing system using folders

### **(5) Rendering Engine**

Supports multiple rendering types (CSR, SSR, SSG, ISR)

### **(6) API Layer**

* Route Handlers to create backend endpoints
* Example: `/app/api/user/route.js`

➡ Overall Architecture Diagram (simple):

```
Browser <--> Client Components
        <--> Server Components --> DB/API
        <--> Rendering Engine (SSR/SSG/ISR)
```

---

## **App Router vs Pages Router**

Next.js has 2 routers:

### ✅ **Pages Router (Old)**

* Directory: `/pages`
* File example: `/pages/about.js`
* Uses `getStaticProps`, `getServerSideProps`
* Client rendering focus
* Used before Next.js 13

### ✅ **App Router (New)**

* Directory: `/app`
* Uses **server components by default**
* Uses `fetch()` with caching & revalidation
* Adds layouts, templates, streaming
* Introduced in Next.js 13+

### **Key Differences**

| Feature         | Pages              | App                      |
| --------------- | ------------------ | ------------------------ |
| Folder          | `/pages`           | `/app`                   |
| Rendering Focus | CSR + old SSR      | RSC + Streaming          |
| Data Fetching   | getStaticProps etc | fetch() + server actions |
| SEO             | Good               | Better                   |
| Layouts         | Manual             | Built-in                 |
| TypeScript      | Optional           | First-class              |

➡ **Future-proof choice:** **App Router**

---

## **File-Based Routing**

Next.js turns **file and folder names into route URLs**.

### **Example**

Folder:

```
app
 └── about
      └── page.tsx
```

URL:

```
/about
```

### **Rules**

* Folder = route segment
* Each folder needs a `page.js` or `page.tsx` to show UI
* Can create nested routes with nested folders

---

## **next.config.js**

* Root configuration file for Next.js
* Used to **enable features, modify build, and customize behavior**

### **Common Uses**

* Enable experimental features
* Allow external image domains
* Set redirects & rewrites
* Set environment configs

### **Basic Example**

```js
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  images: {
    domains: ["example.com"],
  },
};

module.exports = nextConfig;
```

---

# **2. App Router (Next.js 13–16)**

The **App Router** lives inside `/app` folder and uses **Server Components by default**.

---

## **app Directory**

Structure example:

```
app/
 ├─ layout.tsx
 ├─ page.tsx
 ├─ loading.tsx
 ├─ error.tsx
 ├─ not-found.tsx
 └─ dashboard/
      └─ page.tsx
```

➡ This gives **routing + UI + layouts** all in filesystem.

---

## **page.tsx / page.jsx**

* This file **renders UI for the route**
* Each folder must have one page to be visible

### Example

```tsx
export default function Page() {
  return <h1>Home Page</h1>;
}
```

---

## **layout.tsx**

* Wraps **pages inside a shared UI shell**
* Common for **header, sidebar, footer**

### Example

```tsx
export default function RootLayout({ children }) {
  return (
    <html>
      <body>
        <Navbar />
        {children}
      </body>
    </html>
  );
}
```

Layouts can be **nested**.

---

## **template.tsx**

* Similar to layout but **re-renders on navigation**
* Useful for **transitions, animations**

Example:

```tsx
export default function Template({ children }) {
  return <div className="fade">{children}</div>;
}
```

---

## **loading.tsx**

* Shows when **data is loading**
* Used with **streaming**

Example:

```tsx
export default function Loading() {
  return <p>Loading...</p>;
}
```

---

## **error.tsx**

* Catches **errors inside route**

Example:

```tsx
"use client";

export default function Error({ error, reset }) {
  return (
    <>
      <h2>Something went wrong!</h2>
      <button onClick={() => reset()}>Try again</button>
    </>
  );
}
```

---

## **not-found.tsx**

* Renders **404 UI** for route

Example:

```tsx
export default function NotFound() {
  return <h1>404 Page Not Found</h1>;
}
```

---

## **Route Groups `(group)`**

* Create folders **without changing URL**
  Example folder:

```
app/(auth)/login/page.tsx
app/(auth)/register/page.tsx
```

URL:

```
/login
/register
```

➡ Good for organizing project

---

## **Colocation**

* Keeping **component code inside route folders**
* Makes project clean & readable

Example:

```
app/dashboard/
 ├─ page.tsx
 └─ components/
      └─ Chart.tsx
```

---

## **Private folders `_folder`**

* Prefixed with `_`
* Not converted into routes
* Internal-only UI

Example:

```
app/dashboard/_components/Graph.tsx
```

---

# **3. Routing (Deep)**

---

## **Static Routes**

Normal folders → Normal routes.

Example:

```
app/blog/page.tsx
```

URL = `/blog`

---

## **Dynamic Routes `[id]`**

Used for **variable paths** like product pages.

Folder:

```
app/product/[id]/page.tsx
```

URL Example:

```
/product/10
/product/550
```

### Access dynamic parameter:

```tsx
export default function Page({ params }) {
  return <h1>Product {params.id}</h1>;
}
```

---

## **Catch-all Routes `[...slug]`**

Matches multiple segments.

Folder:

```
app/docs/[...slug]/page.tsx
```

Matches:

```
/docs/a
/docs/a/b
/docs/a/b/c
```

---

## **Optional Catch-all `[[...slug]]`**

Works even if no segments exist.

Matches:

```
/docs
/docs/a
/docs/a/b
```

---

## **Parallel Routes `@slot`**

Render **two routes in parallel**.

Example structure:

```
app/dashboard/
 ├─ page.tsx
 ├─ @analytics/page.tsx
 ├─ @users/page.tsx
```

Used for **dashboards & split UIs**

---

## **Intercepting Routes**

Symbols:

* `(.)route` → same level
* `(..)route` → up one level

Used for **modals & overlays**

Example use case: open modal without leaving current page

---

## **Route Masking**

Shows **different URL than actual route**
Used for modals, drawers, overlays.

---

## **Router Hooks**

### **useRouter**

Client navigation

```tsx
"use client";
import { useRouter } from "next/navigation";

const router = useRouter();
router.push("/home");
```

### **usePathname**

Get current URL path

```tsx
const path = usePathname();
```

### **useSearchParams**

Access query params

```tsx
const params = useSearchParams();
const id = params.get("id");
```

---

# **4. Rendering & Components**

---

## **Server Components (RSC)**

* Default in App Router
* Run **on server**
* Do **not** bundle into browser
* Can **access DB, APIs, files**
* Cannot use **browser-only hooks (useState/useEffect)**

Example:

```tsx
export default async function Page() {
  const data = await fetch(...);
  return <div>{data.name}</div>;
}
```

---

## **Client Components**

* Run **in the browser**
* Use interactivity hooks:

  * useState
  * useEffect
  * event listeners (onClick)

### Mark with:

```tsx
"use client";
```

---

## **"use client" Directive**

Placed **at top of file** to force client mode.

---

## **Component Boundaries**

Server Component → can wrap → Client Component
Client Component → cannot wrap → Server Component

---

## **Rendering Hierarchy**

Order of rendering:

1. **Server fetch**
2. **Generate HTML**
3. **Send to browser**
4. **Hydrate (make interactive)**

---

## **Streaming UI**

* Send **chunks** of UI to browser
* Works with `loading.tsx`
* Faster first content load

---

## **Partial Rendering**

* Updates **only changed parts**
* Reduces re-renders
* Better performance

---

# **5. Rendering Strategies**

---

### **CSR — Client-Side Rendering**

* Done fully in browser
* Weak SEO
* Used in dashboards, admin apps

---

### **SSR — Server-Side Rendering**

* HTML generated on **each request**
* Good SEO
* Used for dynamic content

---

### **SSG — Static Site Generation**

* HTML generated at **build time**
* Fastest
* Used for blogs, docs

---

### **ISR — Incremental Static Regeneration**

* SSG + **auto refresh after time**
* Good for products, listings

---

### **Dynamic Rendering**

* Data changes per request
* Usually using `no-store`

---

### **Static Rendering**

* Data cached & reused
* Using `force-cache` or `revalidate`

---

### **Edge Rendering**

* Runs logic on **edge network**
* Very low latency
* Good for personalization (auth, AB tests)

---
Got it dear — now I will follow EXACT instructions:

✔ Detailed explanation
✔ Paragraph + bullet + sub-points wherever needed
✔ Syntax + usage + examples
✔ Differences where needed
✔ Technical terms but 8th-grade simple English
✔ No skipping anything

Ready? Let’s go topic-wise 👇

---

# **6. Data Fetching (Next Way)**

### **Overview**

Next.js gives a **unified data-fetching system** using `fetch()` with **caching, revalidation, deduplication, and server-side default behavior**.
This is different from React because **fetch in Next can run on server**, not only browser.

---

## **1. fetch in Server Components**

Server Components are **default** in App Router, so placing an `await fetch()` inside a component runs **on the server**.

### **Key Benefits**

* No CORS issues
* Can access **database, secrets, environment variables**
* No client-side bundle increase
* Automatic **caching + dedup + revalidate**

### **Syntax**

```tsx
export default async function Page() {
  const res = await fetch("https://api.example.com/products");
  const data = await res.json();
  return <div>{data.length} products</div>;
}
```

### **Usage Cases**

* Product lists
* Blog posts
* SEO-friendly content
* Auth user dashboard data

---

## **2. fetch in Client Components**

Client Components need `"use client"` and `useEffect` or events to fetch.

### **Syntax**

```tsx
"use client";
import { useEffect, useState } from "react";

export default function ClientPage() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("/api/products")
      .then(res => res.json())
      .then(setData);
  }, []);

  return <div>{data.length} items</div>;
}
```

### **Use Cases**

* Buttons triggering fetch
* Forms
* UI interactions
* Real-time updates

---

## **3. Caching Strategies**

Next fetch has two main caching modes:

### **(A) `force-cache` (default)**

* Cache result
* Reuse without refetch
* Good for static data

Example:

```ts
fetch(url, { cache: "force-cache" });
```

### **(B) `no-store`**

* No caching
* Always fetch fresh data

Example:

```ts
fetch(url, { cache: "no-store" });
```

---

## **4. Request Memoization**

Next deduplicates identical requests **within the same render**, so fetch runs only once.

Meaning:

```ts
await fetch("/api")  // executed
await fetch("/api")  // NOT executed again, returned from memo
```

This reduces:

* duplicate calls
* server load
* race conditions

---

## **5. Revalidation**

Revalidation refreshes cached data **after a time interval**.

### **Syntax**

```ts
fetch(url, {
  next: { revalidate: 60 }  // refresh every 60 seconds
});
```

### **Use Cases**

* product price (updates slowly)
* blog content (changes sometimes)
* dashboard stats (periodic)

---

## **6. On-demand Revalidation**

Triggered **manually** after a mutation, not time-based.

Used for:

* Admin panel updates
* CMS updates
* Blog publishing

Triggered using:

```ts
import { revalidatePath, revalidateTag } from "next/cache";
```

### **Example**

```ts
await revalidatePath("/blog");
```

---

## **7. Dynamic Fetch**

When data changes per request, we mark fetch as dynamic.

Options:

1. `cache: "no-store"`
2. `next: { revalidate: 0 }`

Example:

```ts
await fetch(url, { cache: "no-store" });
```

Used for:

* authenticated dashboards
* user-specific content
* search results

---

## **8. no-store vs force-cache**

| Mode          | Meaning        | Use Case               |
| ------------- | -------------- | ---------------------- |
| `force-cache` | Static, cached | blogs, docs, marketing |
| `no-store`    | Always fetch   | auth pages, dashboards |

---

## **9. Parallel Data Fetching**

Fetch multiple APIs at **same time** using `Promise.all`

### **Syntax**

```ts
const [users, posts] = await Promise.all([
  fetch("/api/users").then(r => r.json()),
  fetch("/api/posts").then(r => r.json())
]);
```

### **Benefits**

* Faster page load
* Ideal for dashboards

---

## **10. Sequential Fetching**

Fetching **one after another** (when result depends on previous)

Example:

```ts
const user = await fetch(`/api/user`).then(r => r.json());
const posts = await fetch(`/api/posts?user=${user.id}`).then(r => r.json());
```

Use when:

* Data dependency (user → posts)
* Transaction flows
* Auth-based fetch

---

# **7. Server Actions (VERY IMPORTANT)**

---

## **1. What are Server Actions**

Server Actions are **async server functions** that run on the server but can be **called directly from Client or Form** without API route.

Meaning:
🟢 No `/api` required
🟢 No fetch required
🟢 Safe on server side
🟢 Full-stack without boilerplate

---

## **2. Action Functions**

Marked using `'use server'` directive.

Example:

```ts
'use server';

export async function addTodo(formData) {
  const task = formData.get("task");
  await db.todo.create({ task });
}
```

Runs:

* On server
* With full backend power

---

## **3. Form Actions**

HTML forms can submit directly to Server Action.

Example:

```tsx
<form action={addTodo}>
  <input name="task"/>
  <button type="submit">Add</button>
</form>
```

➡ No extra API needed.

---

## **4. Mutations**

Server Actions are mainly used for:

* create
* update
* delete

Example Update:

```ts
'use server';
export async function updateUser(data) {
  await db.user.update(...);
}
```

---

## **5. Revalidation After Mutation**

After mutation, cached pages become outdated.
So use:

```ts
import { revalidatePath } from "next/cache";
```

Example:

```ts
'use server';
export async function addTodo(formData) {
  await db.todo.create(...);
  revalidatePath("/todos");
}
```

---

## **6. Security Boundaries**

Server Actions are **secure by default** because:

* run on server
* not shipped to browser
* can use secrets (DB keys, tokens)
* no CORS problems

Better than:

* client fetch
* REST APIs (for simple cases)

---

## **7. useActionState (Client Hook)**

This hook manages **Action lifecycle state** like loading, errors, success.

Example:

```tsx
"use client";
import { useActionState } from "react";

const [state, formAction] = useActionState(addTodo, null);

<form action={formAction}>
  ...
</form>
```

---

## **8. useFormStatus**

Gives status of the closest form action:

Example:

```tsx
"use client";
import { useFormStatus } from "react-dom";

function SubmitButton() {
  const { pending } = useFormStatus();
  return <button disabled={pending}>{pending ? "Loading..." : "Submit"}</button>;
}
```

---

# **8. API & Backend**

Next.js lets you build backend using **Route Handlers**.

---

## **1. Route Handlers**

File-based backend routes stored in:

```
app/api/**/route.ts
```

Example:

```
app/api/users/route.ts
```

### **Syntax**

```ts
export async function GET(req) {
  return Response.json({ message: "ok" });
}
```

Supports: `GET`, `POST`, `PUT`, `DELETE`, etc.

---

## **2. REST APIs**

REST = Representational State Transfer
Communicates via HTTP methods:

* GET (read)
* POST (create)
* PUT/PATCH (update)
* DELETE (remove)

Example:

```ts
export async function POST(req) {
  const body = await req.json();
  return Response.json({ created: true });
}
```

---

## **3. HTTP Methods (Brief Meaning)**

| Method | Meaning          |
| ------ | ---------------- |
| GET    | read data        |
| POST   | create data      |
| PUT    | replace data     |
| PATCH  | update partially |
| DELETE | remove data      |

---

## **4. Request / Response Objects**

### **Request**

Has:

* `headers`
* `body`
* `params`
* `url`

Example:

```ts
const body = await req.json();
```

### **Response**

Used to send data:

```ts
return new Response("ok", { status: 200 });
```

---

## **5. Middleware**

Runs **before request hits route**.

Uses:

* authentication
* redirects
* logging
* geo routing

---

## **6. Edge Middleware**

Runs at **CDN Edge**, fast, low latency for:

* A/B tests
* Auth checks
* Location-based content

---

## **7. CORS Handling**

Cross-Origin Resource Sharing

Used when:

* frontend & backend are on different domains

Example Middleware:

```ts
export const GET = () =>
  new Response(null, {
    headers: { "Access-Control-Allow-Origin": "*" }
  });
```

---

# **9. Middleware**

---

## **1. Middleware Basics**

File: `middleware.ts` at project root

Runs on:

* route match
* before page render

Example:

```ts
import { NextResponse } from "next/server";

export function middleware(req) {
  return NextResponse.next();
}
```

---

## **2. matcher Config**

Control where middleware applies.

Example:

```ts
export const config = {
  matcher: ["/dashboard/:path*", "/settings"]
};
```

---

## **3. Authentication Middleware**

Check cookies, tokens, redirects.

Example:

```ts
import { NextResponse } from "next/server";

export function middleware(req) {
  const token = req.cookies.get("token");
  if (!token) return NextResponse.redirect("/login");
}
```

---

## **4. Redirects & Rewrites**

### **Redirect**

Changes URL + browser navigation.

Example:

```ts
return NextResponse.redirect(new URL("/login", req.url));
```

### **Rewrite**

Keeps URL same but serves different content:

```ts
return NextResponse.rewrite(new URL("/internal", req.url));
```

---

## **5. Middleware vs API Routes**

| Feature | Middleware | API Routes |
|---|---|
| Runs before routes | Yes | No |
| Auth check | Ideal | Yes |
| Data fetching | No | Yes |
| Redirect | Yes | No |
| Return JSON | No | Yes |
| Runs at edge | Yes | Optional |

---

# **10. Authentication & Authorization**

---

## **1. Auth Concepts**

Authentication = **who you are**
Authorization = **what you can access**

Example:

* Login = Authentication
* Admin vs User = Authorization

---

## **2. Cookies in Next**

Cookies store:

* tokens
* session IDs
* preferences

Server read:

```ts
import { cookies } from "next/headers";
const token = cookies().get("token");
```

Client read needs:

* `document.cookie` (not secure for JWT)

---

## **3. Headers**

Server headers contain request info:

```ts
import { headers } from "next/headers";
const agent = headers().get("user-agent");
```

---

## **4. Session-Based Auth**

Server stores **session ID** in DB.
Browser stores **session token** in cookie.

Flow:

1. user logs in
2. server creates session row
3. cookie stores session-id
4. middleware checks session

---

## **5. Token-Based Auth (JWT)**

* No server memory
* Stores token in cookie or header

Example JWT Flow:

1. POST /login → returns JWT
2. Store in `httpOnly cookie`
3. Middleware validates token

---

## **6. Protected Routes**

Routes that only logged-in users can view.

Pattern:

```ts
if (!token) redirect("/login");
```

Can be done via:

* middleware
* layouts

---

## **7. Middleware Auth Patterns**

Common logic:

* read token
* verify token
* allow or redirect

Example:

```ts
export function middleware(req) {
  const token = req.cookies.get("token");
  if (!token) return NextResponse.redirect("/login");
}
```

---

## **8. NextAuth (Concept)**

NextAuth.js = ready-made auth library for Next.js

Supports:

* OAuth (Google, GitHub)
* Credentials
* JWT
* Sessions
* Databases

Handles:

* signup
* login
* refresh tokens
* secure cookies

Good for:

* SaaS apps
* dashboards
* social login

---
Perfect — I’ll go deep, structured, clean, simple English (8th-grade level) but still technical. I will not miss topics, and I will include explanation + concepts + when to use + syntax + examples + important notes.

---

# ✅ **11. Styling & Assets in Next.js**

Styling is how we make UI look good. Assets are files like images, fonts, and static stuff.

---

## **A) Global CSS**

### **Meaning**

Global CSS affects the whole app. It is loaded once and every component can use it.

### **Where used**

Placed in `app/globals.css` or imported in `layout.tsx`.

### **Important points**

* Applies everywhere
* Can cause naming conflicts
* Good for resets, variables, base styles

### **Example**

`app/globals.css`:

```css
* {
  margin: 0;
  padding: 0;
}
body {
  background: #f5f5f5;
  font-family: sans-serif;
}
```

Then in `app/layout.tsx`:

```tsx
import './globals.css'

export default function RootLayout({ children }) {
  return <html><body>{children}</body></html>
}
```

---

## **B) CSS Modules**

### **Meaning**

CSS Module is a CSS file where class names are scoped (local). No conflicts.

### **File naming**

`Button.module.css`

### **Usage**

```css
/* Button.module.css */
.btn {
  color: white;
  background: blue;
}
```

```tsx
// Button.tsx
import styles from './Button.module.css'

export function Button() {
  return <button className={styles.btn}>Click</button>
}
```

### **Benefits**

* No global conflicts
* Best for components

---

## **C) Tailwind CSS**

### **Meaning**

Utility-first CSS framework. Styling done using small utility classes.

### **Example**

```tsx
<button className="bg-blue-500 text-white px-4 py-2 rounded">
  Click
</button>
```

### **Why useful**

* Fast styling
* Responsive classes built-in
* No custom CSS needed for basics

### **Installation (concept)**

Tailwind config + globals import

---

## **D) CSS-in-JS**

### **Meaning**

Write CSS using JavaScript. Styling stays inside component.

### **Examples of libraries**

* styled-components
* Emotion

### **Example (styled-components)**

```tsx
import styled from 'styled-components'

const Box = styled.div`
  padding: 20px;
  background: black;
`

export default function Page() {
  return <Box>Hello</Box>
}
```

### **Notes**

* Can run on server or client
* Slight runtime overhead

---

## **E) Fonts (next/font)**

### **Meaning**

Built-in system for optimized font loading.

### **Types**

* Local fonts
* Google fonts

### **Example (Google font)**

```tsx
import { Inter } from 'next/font/google'
const inter = Inter()

export default function Page() {
  return <div className={inter.className}>Hello</div>
}
```

### **Benefits**

* No layout shift
* Auto optimizations

---

## **F) Image Optimization (`next/image`)**

### **Meaning**

Special component for optimized images:

* Lazy loading
* Responsive sizes
* WebP conversion

### **Example**

```tsx
import Image from 'next/image'

<Image src="/dog.png" width={400} height={300} alt="Dog" />
```

### **Notes**

* Requires `width` and `height`
* Works well with remote images using config
* Reduces bundle size

---

## **G) Static Assets**

Static assets are files bundled with the app (images, SVGs, audio, etc.)

### **Usage**

```tsx
<Image src="/logo.svg" width={100} height={40} alt="Logo" />
```

---

## **H) Public Folder**

All files placed inside `public/` are directly available at root path.

### **Example**

`public/avatar.png` → accessible at `/avatar.png`

### **Notes**

* Good for images, icons, PDF, files
* No import required

---

# ✅ **12. SEO & Metadata in Next.js**

SEO = improving visibility on search engines.

Metadata = info about page for browser + social media.

---

## **A) Metadata API**

### **Meaning**

Used to define `title`, `description`, `icons`, etc.

### **Types**

* Static Metadata (known at build time)
* Dynamic Metadata (computed at runtime)

---

## **B) Static Metadata**

Defined directly inside a page layout or component.

### **Example**

```tsx
export const metadata = {
  title: "About Page",
  description: "This is about page"
}
```

### **Use**

Simple pages (no dynamic values)

---

## **C) Dynamic Metadata**

Generated using a function when data depends on params.

### **Example**

```tsx
export async function generateMetadata({ params }) {
  return {
    title: `User ${params.id}`
  }
}
```

### **Use**

* product pages
* user profiles

---

## **D) Open Graph**

### **Meaning**

Metadata for social media preview cards (Facebook, LinkedIn, etc.)

### **Example**

```tsx
export const metadata = {
  openGraph: {
    title: "My Blog",
    description: "Cool blog",
    images: ['/cover.png']
  }
}
```

---

## **E) Twitter Cards**

### **Meaning**

Special meta tags for Twitter previews.

### **Example**

```tsx
export const metadata = {
  twitter: {
    card: "summary_large_image",
    title: "My Blog"
  }
}
```

---

## **F) Robots**

### **Meaning**

Controls what search engines can crawl.

### **Example**

`/robots.txt` can allow or block paths

In Next:

```tsx
export function robots() {
  return {
    rules: [{ userAgent: '*', allow: '/' }],
  }
}
```

---

## **G) Sitemap**

### **Meaning**

File that lists all accessible URLs for search engines.

Example usage:

```
/sitemap.xml
```

In Next (auto generated using libs or api routes).

---

## **H) Canonical URLs**

### **Meaning**

Tells Google which URL is the “main” one to avoid duplicate content issues.

### **Example**

```tsx
export const metadata = {
  alternates: {
    canonical: 'https://example.com/blog/page'
  }
}
```

---

# ✅ **13. Performance Optimization**

Goal = make app load faster and use fewer resources.

---

## **A) Image Optimization**

Use `next/image` for:

* smaller images
* lazy loading
* responsive images

Better than `<img>` tag.

---

## **B) Font Optimization**

`next/font` prevents layout shifts (CLS).

Benefits:

* Preloading
* Subsetting
* No network delay from Google font CDN

---

## **C) Code Splitting**

Split code to load only what is required.

### **Types**

* Route-based splitting (auto)
* Component-based (manual)

### **Example**

```tsx
const Chat = dynamic(() => import('./Chat'))
```

---

## **D) Lazy Loading**

Loads component only when needed.

```tsx
const Video = dynamic(() => import('./Video'), { ssr: false })
```

---

## **E) Prefetching**

Next prefetches links in viewport for faster navigation.

Example:

```
<Link href="/about">About</Link>
```

---

## **F) Bundle Analysis**

Helps find large libraries in build.

Tools:

* `@next/bundle-analyzer`

---

## **G) Tree Shaking**

Removes unused code from final bundle.

Applies to:

* ES modules
* Libraries exporting multiple things

---

# ✅ **14. Error Handling**

---

## **A) `error.tsx`**

### **Meaning**

Handles UI errors in a route segment.

Example:
`app/dashboard/error.tsx`

---

## **B) Global Error**

Error at root level (layout error).

### **Example**

In `app/error.tsx`

---

## **C) not-found handling**

`not-found.tsx` runs when a page does not exist.

---

## **D) try/catch in Server Components**

Used for data fetching or API calls.

### **Example**

```tsx
try {
  const res = await fetch(...)
} catch (err) {
  console.error(err)
}
```

---

## **E) Error Boundaries (React)**

Client-side error catching.

---

# ✅ **15. Environment & Config**

---

## **A) Environment Variables**

Located in:

```
.env
.env.local
.env.production
```

### **Rules**

* `NEXT_PUBLIC_` prefix makes variables available to client
* Others are server-only

---

## **B) Runtime Config**

Values read during server execution.

---

## **C) next.config.js**

Central config file for:

* images
* redirects
* rewrites
* webpack

Example:

```js
module.exports = {
  images: {
    domains: ['images.com']
  }
}
```

---

## **D) Headers Config**

Modify response headers:

```js
async headers() {
  return [{
    source: "/(.*)",
    headers: [{ key: "X-Frame-Options", value: "DENY" }]
  }]
}
```

---

## **E) Redirects Config**

```js
async redirects() {
  return [{ source: "/old", destination: "/new", permanent: true }]
}
```

---

## **F) Rewrites Config**

Rewrites change path without redirect.

---

# ✅ **16. Deployment & Production**

---

## **A) Build Process**

Command:

```
npm run build
```

Creates `.next` folder.

---

## **B) Static Export**

Used for SSG apps:

```
next export
```

---

## **C) Vercel Deployment**

Best platform (native support).

---

## **D) Self-hosting**

Using Node server:

```
next start
```

---

## **E) Edge Deployment**

Runs code at edge locations for low latency.

---

## **F) Environment Handling**

Different `.env` files for envs:

* dev
* staging
* production

---

# ✅ **17. Advanced / Rare but Powerful**

---

## **A) Turbopack**

Next.js bundler (Rust-based) replacing Webpack in dev.

Benefits:

* Faster HMR
* Faster rebuilds

---

## **B) Partial Prerendering (PPR)**

Hybrid of static + dynamic rendering.

---

## **C) React Server Actions Internals**

Server-only functions that can mutate data without API routes.

---

## **D) Web Streams**

Used for:

* streaming SSR
* large file transfers

---

## **E) Incremental Adoption**

Migrating React apps to Next without full rewrite.

---

## **F) Monorepos**

Using workspaces:

* TurboRepo
* Nx

---
