# RISE

**Residential Incentives for Sustainability and Environmentalism**

RISE is a free, public website that helps households find residential sustainability incentives, rebates, and programs across the United States and its territories. It brings state and federal resources into one searchable site and organizes them into four categories: energy, water, transportation, and recycling.

## Features

- Search and browse programs by state or U.S. territory
- Browse nationwide federal programs
- Filter programs by category
- View eligibility and access details with links to official sources
- Find guidance for locating utility, city, and county programs
- Cache program data locally for improved resilience
- Responsive interface for desktop and mobile devices

## Tech stack

- [React](https://react.dev/) and [TypeScript](https://www.typescriptlang.org/)
- [Vite](https://vitejs.dev/)
- [Tailwind CSS](https://tailwindcss.com/)
- [shadcn/ui](https://ui.shadcn.com/) and [Radix UI](https://www.radix-ui.com/)
- [React Router](https://reactrouter.com/)
- [TanStack Query](https://tanstack.com/query/latest)
- [Papa Parse](https://www.papaparse.com/) for CSV data
- [Vitest](https://vitest.dev/) and Testing Library

## Program data

RISE fetches its directory data from the CSV URL configured in `VITE_SHEETS_URL`. The CSV must include these exact column headings:

| Column | Description |
| --- | --- |
| `Program` | Program or incentive name |
| `Type` | `energy`, `water`, `transportation`, or `recycling` |
| `Description` | Short public-facing description |
| `Link` | Official program URL |
| `How to Access` | Eligibility or application details |
| `State` | State or territory name, or the value used for federal records |
| `Level` | Program level, such as `state` or `federal` |

After a successful request, the application saves the parsed program list in browser local storage. If a later request fails, the application uses that cached data when available.

## Available scripts

| Command | Purpose |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Create a production build in `dist/` |
| `npm run build:dev` | Create a development-mode build |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint |
| `npm test` | Run the test suite once |
| `npm run test:watch` | Run tests in watch mode |

## Project structure

```text
src/
├── assets/       Images and brand assets
├── components/   Shared layout, program, filter, and UI components
├── data/         Program types, state data, and CSV loading logic
├── hooks/        Shared React hooks
├── lib/          Utility functions
├── pages/        Route-level page components
└── test/         Test setup and tests
```

## Routes

| Route | Page |
| --- | --- |
| `/` | Home and state search |
| `/states` | State and territory programs |
| `/state/:code` | Program page for an individual state |
| `/federal` | Federal programs |
| `/local` | Guidance for finding local resources |
| `/about` | About RISE |
| `/contact` | Contact and feedback |

## Quality checks

Before opening a pull request, run:

```bash
npm run lint
npm test
npm run build
```

## Disclaimer

RISE is an informational resource. It does not provide financial advice, determine eligibility, process applications, or guarantee that a program is available. Always confirm current requirements and availability with the official program administrator.


