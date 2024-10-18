# Nuxt 3 Minimal Starter

Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Theme Management

The project uses a centralized theme management approach. The theme is defined in `assets/theme.css` using CSS variables. This file is imported in `app.vue`, making the theme variables available globally.

To modify the theme, edit the CSS variables in `assets/theme.css`. All components use these variables for styling, ensuring consistency across the application.

## Setup

Make sure to install the dependencies:

```bash
# yarn
yarn install

# npm
npm install

# pnpm
pnpm install
```

## Development Server

Start the development server on http://localhost:3000

```bash
npm run dev
```

## Production

Build the application for production:

```bash
npm run build
```

Locally preview production build:

```bash
npm run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
