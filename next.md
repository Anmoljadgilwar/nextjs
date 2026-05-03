Shifting from **Node.js** to **Next.js** is less about abandoning Node and more about moving _up the stack_. Next.js still runs on Node (or edge runtimes), but adds structure, conventions, and full-stack features.

Here are the **must-know things**, especially around **naming, structure, and mindset changes**:

---

# 🧠 1. Mental Shift: From “Backend-first” to “Full-stack Framework”

In plain Node.js (e.g., with Express), you manually define:

- Routes
- Controllers
- Middleware
- APIs

In Next.js:

- Routing is **file-based**
- Backend + frontend live together
- Many conventions replace configuration

---

# 📁 2. File & Folder Naming Conventions (VERY IMPORTANT)

## App Router (modern Next.js – recommended)

if you have to create a signup first create a signup folder inside it page.tsx

Uses `/app` directory.

### 🔹 Routing by folder names

```
app/
  page.tsx        → "/"
  about/
    page.tsx      → "/about"
  blog/
    [slug]/
      page.tsx    → "/blog/:slug"
```

### 🔹 Special filenames (must follow exactly)

- `page.tsx` → route UI
- `layout.tsx` → shared layout
- `loading.tsx` → loading UI
- `error.tsx` → error boundary
- `not-found.tsx` → 404 page

👉 These names are **reserved and required** — you can’t rename them.

---

## 🔹 Dynamic Routes Naming

```
[slug]        → single param
[...slug]     → catch-all
[[...slug]]   → optional catch-all
```

Example:

```
app/products/[id]/page.tsx
```

---

# ⚙️ 3. API Routes Naming

Instead of Express routes:

### Node.js (old way)

```js
app.get('/api/users', ...)
```

### Next.js

```
app/api/users/route.ts
```

And inside:

```ts
export async function GET() {}
export async function POST() {}
```

👉 File name must be `route.ts` (not flexible)

---

# 🧩 4. Component Naming Conventions

- Use **PascalCase**:

  ```
  UserCard.tsx
  Navbar.tsx
  ```

- Hooks:

  ```
  useAuth.ts
  useUser.ts
  ```

- Utility files:

  ```
  formatDate.ts
  apiClient.ts
  ```

---

# 🌐 5. Server vs Client Components (CRITICAL)

By default, everything is a **Server Component**.

To use browser features:

```ts
"use client";
```

👉 Naming tip:

- Some teams suffix client components:

  ```
  Button.client.tsx
  Modal.client.tsx
  ```

---

# 🎯 6. Environment Variables Naming

Must prefix with:

```
NEXT_PUBLIC_
```

Example:

```
NEXT_PUBLIC_API_URL
```

👉 Without this prefix → only available on server

---

# 🚀 7. Data Fetching Naming Patterns

Common conventions:

- `getUsers()`
- `fetchPosts()`
- `getServerSession()`

Used inside:

- Server components
- Route handlers

---

# 📦 8. Project Structure (Typical)

```
app/
components/
lib/          → helpers, DB, utils
hooks/
types/
public/
styles/
```

Naming conventions:

- `lib/` → backend logic
- `utils/` → pure helpers
- `services/` → API calls (optional pattern)

---

# 🔐 9. Middleware Naming

```
middleware.ts
```

Only one global middleware file (by default)

---

# ⚡ 10. Styling Naming

- CSS Modules:

  ```
  Button.module.css
  ```

- Tailwind:
  No special naming, but keep components clean

---

# 🧭 11. Key Differences from Node.js

| Node.js               | Next.js              |
| --------------------- | -------------------- |
| Manual routing        | File-based routing   |
| Express APIs          | `route.ts`           |
| Separate frontend     | Built-in frontend    |
| Middleware everywhere | Limited + structured |
| Freedom               | Convention-heavy     |

---

# ⚠️ Common Mistakes to Avoid

- ❌ Renaming `page.tsx` → breaks routing
- ❌ Forgetting `"use client"` when needed
- ❌ Mixing server/client logic incorrectly
- ❌ Treating it like Express (it’s not)

---

# 🧩 Pro Tips (from real-world usage)

- Keep **business logic in `/lib`** (like Node services)
- Treat **API routes like mini Express handlers**
- Use **server components as much as possible** (better performance)
- Don’t overuse client components

---

# 👍 Quick Summary

- File names = routing (very strict)
- `page.tsx`, `layout.tsx`, `route.ts` are **special**
- Prefer server components
- Use `NEXT_PUBLIC_` for client env vars
- Think **full-stack React**, not just backend

---

If you want, I can:

- Convert a sample Node/Express app → Next.js structure
- Give you a **starter folder template**
- Or show **before/after code comparisons**
