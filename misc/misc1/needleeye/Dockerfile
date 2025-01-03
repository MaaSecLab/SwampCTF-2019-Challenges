FROM php:7.2-apache

# Enable mod_autoindex for directory indexing
RUN a2enmod autoindex

# Configure directory indexing only for the root directory and disable for subdirectories
RUN echo '<Directory /var/www/html>\n' \
         'Options Indexes\n' \
         'AllowOverride None\n' \
         'Require all granted\n' \
         '</Directory>' \
         > /etc/apache2/conf-available/enable-indexing.conf && \
    echo '<Directory /var/www/html/*>\n' \
         'Options -Indexes\n' \
         'AllowOverride None\n' \
         'Require all granted\n' \
         '</Directory>' \
         >> /etc/apache2/conf-available/enable-indexing.conf && \
    a2enconf enable-indexing

# Copy project files to the web root
COPY . /var/www/html

# Restart Apache (to apply changes)
CMD ["apache2-foreground"]
