# MySql plugin for Dokku

Create mysql containers on the fly or link them persistantly to your web app you push up to your Dokku install.
See [Dokku](https://github.com/progrium/dokku) for the bigger picture.

##Install

    cd /var/lib/dokku/plugins
    git clone https://github.com/hughfletcher/dokku-mysql-plugin mysql
    chmod +x mysql/install mysql/commands mysql/pre-release
    dokku plugins-install

##Commands

    $ dokku help
     mysql:create <app>     Create a MySql container
     mysql:delete <app>     Delete specified MySql container
     mysql:info <app>       Display database informations
     mysql:link <app> <db>  Link an app to a MySql database
     mysql:logs <app>       Display last logs from MySql contain

##Simple usage


Create a new DB:

    $ dokku mysql:create foo            # Server side
    $ ssh dokku@server mysql:create foo # Client side

    -----> MySql container created: mysql/foo

           Host: 172.16.0.104
           User: 'admin'
           Password: 'RDSBYlUrOYMtndKb'
           Database: 'db'
           Internal port: 3306

Deploy your app with the same name (client side):

    $ git remote add dokku git@server:foo
    $ git push dokku master
    Counting objects: 155, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (70/70), done.
    Writing objects: 100% (155/155), 22.44 KiB | 0 bytes/s, done.
    Total 155 (delta 92), reused 131 (delta 80)
    remote: -----> Building foo ...
    remote:        PHP app detected

    ... blah blah blah ...

    remote: -----> Deploying foo ...
    remote: 
    remote: -----> App foo linked to mysql/foo database
    remote: 
    remote: -----> Deploy complete!
    remote: -----> Cleaning up ...
    remote: -----> Cleanup complete!
    remote: =====> Application deployed:
    remote:        http://foo.server

##Advanced usage

Deleting databases:

    dokku mysql:delete foo

Linking an app to a specific database:

    dokku mysql:link foo bar

MySql logs (per database):

    dokku mysql:logs foo

Database informations:

    dokku mysql:info foo

##Thanks

* [Kloadut/dokku-pg-plugin](https://github.com/Kloadut/dokku-pg-plugin)