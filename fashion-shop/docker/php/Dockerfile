FROM php:8.3-apache

# Cài đặt các PHP extensions cần thiết
RUN apt-get update && apt-get install -y \
    libicu-dev \
    && docker-php-ext-install intl mysqli pdo pdo_mysql \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Kích hoạt Apache modules
RUN a2enmod rewrite

# Thư mục làm việc
WORKDIR /var/www/html

# Thiết lập Document Root trỏ đến thư mục public
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public

# Cập nhật Document Root trong cấu hình Apache
RUN sed -ri 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' \
    /etc/apache2/sites-available/000-default.conf \
    /etc/apache2/apache2.conf

# Cấu hình quyền truy cập thư mục public
RUN printf '<Directory /var/www/html/public>\n\
    Options FollowSymLinks\n\
    AllowOverride All\n\
    Require all granted\n\
</Directory>\n' \
    > /etc/apache2/conf-available/codeigniter.conf \
    && a2enconf codeigniter

EXPOSE 80
