
## Description
A small app for creating and managing personal notes.

## Installation:

1. Create `.env` file
```bash
cp .env.example .env
```
2. Install Composer dependencies using small container containing PHP and Composer (or you can use usual `composer install` 
if you have Composer installed localy)
```bash
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs
```

3. Build and run containers via Sail
```bash
./vendor/bin/sail down -v
```
```bash
./vendor/bin/sail build --no-cache
```
```bash
./vendor/bin/sail up -d
```

4. Generate app key
```bash
./vendor/bin/sail artisan key:generate
```

5. Execute migrations (repeat this command if the Connection refused error occurred)
```bash
./vendor/bin/sail artisan migrate 
```

6. Build assets
```bash
./vendor/bin/sail npm install
```
```bash
./vendor/bin/sail npm run build
```

## Usage:
* go to http://localhost/register and register your account
* go to  http://localhost:8025/ (Mailpit email testing server) and click on the verification link inside your email
