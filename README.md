# Muthokinju — Fleet & HOS

A dedicated copy of the ControlTech HOS app for **Muthokinju alone**, built from the Farmer's Choice
deployment and locked to Muthokinju's Wialon resources:

| Wialon resource | ID | What |
|---|---|---|
| Muthokinju Hardware | 19058437 | The trucks; the main account (settings and app data are kept under it) |
| MUTHOKINJUDIRECTORS | 28938806 | The directors' cars |
| Muthokinju | 17382986 | No vehicles; the drivers and most geofences |

Nothing belonging to any other customer can be seen, searched, reported or exported from this
deployment. The "FMB140 Test" unit and the placeholder drivers ("Test Driver", "Sample driver …")
are left out (see `src/lib/customer.ts`).

## Sign-in

| Login | Who | Rights |
|---|---|---|
| Username `Muthokinju` + password (in `.env`: `APP_LOGIN_PASSWORD`) | Muthokinju (shared app login) | Admin of this app: settings, FleetRun imports, services and routes |
| Muthokinju Wialon logins (`@muthokinju.co.ke`, or names containing "muthokinju") | Muthokinju staff | Read-only apart from recording FleetRun services and Logistics work |

Overview · Vehicles · Geofences · Hours of service · Driver behaviour · FleetRun (maintenance and fuel
costs) · Logistics · VSS · Reports · Settings — all showing Muthokinju only.

## Run

```powershell
npm install
npm run dev        # http://localhost:3000
npm run build      # production build
npm start
```

Configuration lives in `.env` (see `.env.example`). On Vercel, set the same variables in the project
settings and deploy this folder as its own project.

## Data

Wialon and VSS are only ever read, never changed. App data (settings, FleetRun service records and
imports, Logistics routes, Needs attention items) is stored in Muthokinju's own Supabase project; create
its tables with `db/schema.sql`.
