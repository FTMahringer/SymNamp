FROM php:8.4-fpm

# Install required dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    libzip-dev zip unzip \
    && docker-php-ext-install zip opcache \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /var/www/html

# Copy custom PHP configuration
COPY ./php/php.ini /usr/local/etc/php/php.ini

# Expose PHP-FPM port (if needed for debugging)
EXPOSE 9000
