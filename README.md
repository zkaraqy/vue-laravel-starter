# Laravel + Vue Starter Kit

A Laravel 12 application with an [Inertia](https://inertiajs.com) + Vue 3 + TypeScript frontend, Tailwind CSS 4, Laravel Fortify (two-factor authentication) and Wayfinder (typed routes).

## Requirements

- PHP 8.2+ with the `pdo_sqlite` extension (needed by the test suite)
- Composer 2
- Node.js 22+ and npm

## Setup

```bash
composer install
cp .env.example .env
php artisan key:generate
touch database/database.sqlite
php artisan migrate
npm ci
```

## Development

```bash
composer dev       # app server, queue worker, logs (Pail) and Vite
composer dev:win   # same without Pail, for Windows (Pail needs the pcntl extension)
composer dev:ssr   # app server, queue worker, logs and Inertia server-side rendering
```

## Checks

```bash
composer test          # PHPUnit
vendor/bin/pint --test # PHP code style
npm run format:check   # Prettier
npm run lint:check     # ESLint (no auto-fix)
npm run types:check    # vue-tsc
npm run build          # production build
```

CI (`.github/workflows`) runs the same checks on pushes and pull requests to `develop`, `main` and `master`.

## Security

Run `composer audit` and `npm audit` before each release. `User::$hidden` must keep `two_factor_secret` and `two_factor_recovery_codes`, because the authenticated user is shared with every Inertia page.

## Official Documentation

Documentation for all Laravel starter kits can be found on the [Laravel website](https://laravel.com/docs/starter-kits).

## License

Open-sourced software licensed under the MIT license.
