# fpmをインストールしておかないと、Nginx経由でLaravelのプロジェクトが見れないのでfpmのインストールされたPHPイメージを使用した
FROM php:7.4-fpm

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN docker-php-ext-install pdo pdo_mysql

RUN apt-get update \
    && apt-get install -y zlib1g-dev \
                git \
                zip \
                unzip \
                libonig-dev \
                libfreetype6-dev \ 
                libjpeg62-turbo-dev \
                libpng-dev \
                libjpeg-dev \
    && apt-get install -y libzip-dev \
    && docker-php-ext-install zip \
    && docker-php-ext-install \ 
                    bcmath \
                    gd \
    && docker-php-ext-configure gd \
                --with-freetype=/usr/include/ \
                --with-jpeg=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# Node.jsをインストール
# RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
# RUN apt-get install -y nodejs npm
# RUN npm install && npm run dev
# RUN php artisan ui react
# RUN npm install ts-loader typescript react-router-dom @types/react @types/react-dom @types/react-router-dom --save-dev

RUN apt-get install -y httrack
