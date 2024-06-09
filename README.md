## Getting Started

1. Install dependencies

   ```bash
   pnpm install
   ```

2. Run the development server:

   ```bash
   pnpm dev
   ```

3. Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

4. After modifying the CMS, generate types:

   ```bash
   pnpm generate:types
   ```

---

## Payload CMS

### Using Payload 3.0 Beta

This repository includes a demo of the Payload 3.0 Beta running completely within Next.js.

> [!IMPORTANT]
> The installation steps below should not be executed in this repository.
>
> I just included them below as a reference.

### Installation Process

> [!CAUTION]
> This repository contains v3.0 BETA version of the Payload CMS.
>
> I chose the Beta version 3.0 of Payload because it can be added to any Next.js application with minimal footprint.

> Link to the demo repository of the v3.0 BETA of Payload CMS: [payload-3.0-demo
> ](https://github.com/payloadcms/payload-3.0-demo)

1. After setting up the Next.js application.

2. Move everything from `src/app` into `src/app/(app)` route group to include all the Next.js related routes.

3. In the root of the project:

   ```bash
   pnpx create-payload-app@beta
   ```

   - Notice the `beta` at the end

4. The setup process will detect the Next.js application and guide you through the setup.

5. File changes:

- `payload.config.ts`: Payload CMS configuration

- `src/app/(payload)/*`: Payload CMS Routes

  - `src/app/(payload)/api/*`: Payload CMS API Routes

  - `src/app/(payload)/admin/*`: Payload CMS Admin Panel Routes

- `src/collections/*`: Payload CMS Collection Definitions

- `.env`: Environment variables for the Payload CMS

  - Rename `.env` to `.env.local`

6. Add below `scripts` to `package.json` (copied from demo repository):

   ```json
       "payload": "payload",
       "ci": "payload migrate && pnpm build",
       "generate:types": "payload generate:types"
   ```

7. [_**CHECK FIRST**_] In this beta version `(3.0.0-beta.43)` it doesn't install `sharp` package which is required. So, we have to install it manually:

   ```bash
   pnpm install sharp
   ```

   - It is an image processing package and added in `payload.config.ts`.

8. To generate types:

   ```bash
   pnpm generate:types
   ```
