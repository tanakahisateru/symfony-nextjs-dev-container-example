FROM php:8.3-cli

# Dependencies
RUN apt-get update \
    && apt-get install -y \
        git \
        libicu-dev \
        libpq-dev \
        libzip-dev \
        unzip \
        wget \
        zip \
        curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# PHP Extensions
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/
RUN install-php-extensions \
    bcmath \
    gd \
    intl \
    pdo_mysql \
    zip

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# Symfony CLI
RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony*/bin/symfony /usr/local/bin/symfony

# Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs

# ps command (for JetBrains)
RUN apt-get update \
    && apt-get install -y procps \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Vim
RUN apt-get update \
    && apt-get install -y vim \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Bash completion
RUN apt-get update \
    && apt-get install -y bash-completion \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN echo "source /etc/bash_completion" >> ~/.bashrc
RUN composer completion bash > /etc/bash_completion.d/composer
RUN symfony self:completion bash > /etc/bash_completion.d/symfony
RUN npm completion > /etc/bash_completion.d/npm

# Working directory
WORKDIR /workspace
