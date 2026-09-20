# MAS Warsztat (Workshop 3.0) — Multi-Tenant SaaS for Car Workshops

**Live:** [app.garage.mountaincar.is](https://app.garage.mountaincar.is) · **Status:** production, paying workshops · **Built & operated by** [Kamil Jan](https://kamiljan.com)

A workshop management system for independent garages. A job runs from the customer's first phone call to a signed handover, and the software follows it the whole way. Built first for one real workshop in Iceland, then generalised into a multi-tenant product other workshops subscribe to.

Roughly 80 tables, 135 ordered migrations and 24 deployable edge functions. It is the largest system in this account.

## Why it exists

Small garages run on a paper diary, a phone and a mechanic's memory. The expensive failures are the boring ones: a customer is never called back, a part is ordered twice, a quote is agreed verbally and disputed later, a car is returned without anyone recording what was actually done. Every feature below exists because one of those cost someone money.

## What it does

**Job lifecycle.** Booking, visit and job, with the job as the single source of truth. Scope of work, parts, checklist and purchases are views over it, not separate lists that drift apart. Mechanics get their own views, the office gets the whole picture.

**Nothing falls through.** A missed call becomes a task instead of a lost customer. SMS reminders and repair updates go out automatically, behind a kill switch so a test run can never message real customers.

**Parts and vehicle data.** Live parts pricing from supplier APIs with a fallback chain rather than one brittle integration, and Icelandic vehicle registry lookups with caching, because every lookup is billed.

**An assistant that knows the workshop.** Questions about jobs, parts and prices are answered from the workshop's own data, in the workshop's language and currency, not from a generic model's guesses. Voice IVR answers the phone when nobody can.

**Commercial.** Subscriptions and prepaid credit packages, reconciled from payment webhooks. Loyalty scheme, workshop specialisations, customer self-service booking, invoicing.

## Stack

React · TypeScript · TanStack Router · Tailwind · Supabase (Postgres, Auth, Row Level Security, Edge Functions) · Claude · Twilio · Rapyd · Vercel

## How isolation is handled

The system holds other companies' customer data and takes their money, so tenant isolation is the product, not a feature. Row Level Security is the boundary: every tenant-scoped table carries an organisation id and a policy, and the browser holds a user token and nothing else. Isolation was probed deliberately rather than assumed, and what that pass found was closed by migration before a second workshop was let in. Privileged work runs only in server-side functions, payment state is reconciled from webhooks instead of client-reported success, and AI spend is capped per tenant per day so no prompt loop can quietly run up a bill.

Every push is gated: build, lint, dependency audit, licence check, static analysis and a secret scan, plus a pre-commit hook that blocks credential-shaped strings.

## What this repository is

A public reference, not the application. There is no source here and nothing to install or run. The application is private. This page exists so the work can be read without handing out the code.

## Licence

Proprietary. Published for reference only.
