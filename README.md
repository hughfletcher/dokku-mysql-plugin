# MySql plugin for Dokku

Create mysql containers on the fly or link them persistantly to your web app you push up to your Dokku install.

See [Dokku](https://github.com/progrium/dokku) for the bigger picture. Project was heavily based on [Kloadut's PostgreSQL plugin](https://github.com/Kloadut/dokku-pg-plugin).

##Install

    cd /var/lib/dokku/plugins
    git clone https://github.com/hughfletcher/dokku-mysql-plugin mysql
    chmod +x mysql/install mysql/commands
    dokku plugins-install