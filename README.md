# Tasks for Today Management System

A Laravel version of the TSA1 Tasks for Today Management System. It has a Welcome page filtered to today's tasks, a full task list, a demo user's profile, and a static About page.

## Requirements

- PHP 8.2 or newer
- Composer
- SQLite (the default) or MySQL/MariaDB

The project uses Laravel 12 to support PHP 8.2. Laravel's official release notes list PHP 8.2 as supported for Laravel 12. See the [Laravel release notes](https://laravel.com/docs/12.x/releases).

## Run locally

1. Open this folder in VS Code and open a terminal in the project root.
2. Install PHP packages:

   ```sh
   composer install
   ```

3. Create your local environment file:

   **Windows PowerShell:**

   ```powershell
   Copy-Item .env.example .env
   ```

   **macOS/Linux:**

   ```sh
   cp .env.example .env
   ```

4. Generate the application key and create the database tables with sample data:

   ```sh
   php artisan key:generate
   php artisan migrate --seed
   ```

   SQLite is configured by default. The included `database/database.sqlite` file is the local database. To use MySQL instead, create a database named `tasks_today_laravel`, then set `DB_CONNECTION=mysql`, `DB_HOST=127.0.0.1`, `DB_PORT=3306`, `DB_DATABASE=tasks_today_laravel`, `DB_USERNAME=root`, and `DB_PASSWORD=` in `.env` before running the migration command.

5. Start the Laravel development server:

   ```sh
   php artisan serve
   ```

6. Open the address printed by Artisan, usually `http://127.0.0.1:8000`.

## Pages

- `/` — only tasks whose date is today
- `/tasks` — all tasks in date order
- `/profile` — the one seeded demo user
- `/about` — project and developer information

## Database and seed data

The migrations create `tasks` and `users` with the TSA1 fields. The database seeder inserts eight tasks across today and the two preceding dates, plus exactly one demo user. Running `php artisan migrate:fresh --seed` rebuilds the database and deletes existing data; use it only when you intend to reset the database.
