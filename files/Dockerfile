#FROM nextcloud:latest
#RUN apt-get update && apt-get install -y smbclient libsmbclient-dev
FROM nextcloud:latest

# Install smbclient and other dependencies
RUN apt-get update && apt-get install -y \
    smbclient \
    && rm -rf /var/lib/apt/lists/*

# Ensure the PHP configuration directory is writable
RUN mkdir -p /usr/local/etc/php/conf.d && \
    chown -R www-data:www-data /usr/local/etc/php/conf.d

# Set the entrypoint script permissions
RUN chown -R www-data:www-data /entrypoint.sh && \
    chmod +x /entrypoint.sh

# Switch to www-data user to match the runtime user
USER www-data

# Entrypoint script
ENTRYPOINT ["/entrypoint.sh"]
CMD ["apache2-foreground"]