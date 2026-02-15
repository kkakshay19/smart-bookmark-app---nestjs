This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.




# Smart Bookmark App

A real-time bookmark manager built using Next.js (App Router), Supabase (Auth, PostgreSQL, Realtime), and Tailwind CSS.

## 🚀 Live Demo
Deployed on Vercel:
[Live URL Here]

---

## ✨ Features

- Google OAuth authentication (no email/password)
- Private bookmarks per user using Row Level Security (RLS)
- Add bookmarks (title + URL)
- Delete bookmarks
- Real-time updates across multiple tabs
- Fully deployed on Vercel

---

## 🛠 Tech Stack

- Next.js (App Router)
- Supabase (Authentication, PostgreSQL Database, Realtime)
- Tailwind CSS
- Vercel (Deployment)

---

## 🧠 How It Works

- Users authenticate via Google OAuth using Supabase Auth.
- Each bookmark is stored with a `user_id` linked to `auth.users`.
- Row Level Security ensures users can only view, insert, and delete their own bookmarks.
- Supabase Realtime listens to database changes and updates the UI instantly without page refresh.

---

## 🔐 Database Schema

```sql
create table bookmarks (
  id uuid primary key default gen_random_uuid(),
  created_at timestamp default now(),
  user_id uuid references auth.users not null,
  title text not null,
  url text not null
);
