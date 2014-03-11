# Vagrant-Puppet-Django

This is a Vagrant Ubuntu (Saucy 64) box with a single Puppet manifests file (no modules) for Django development.

## What's included

Puppet provisions:

- Nginx
- uWSGI
- MySQL
- Python
- Virtualenv
- Django
- PIL dependencies to support jpg, zlib, freetype
- Git
- Mercurial
- Vim

## Usage

- Edit configuration variables in the `site.pp` file
- clone or put your project into `src` dir
- `vagrant up`
- `vagrant ssh` to get inside VM
- your project is in `www` dirinside VM 
- install requirements, do stuff (virtualenv is created and activated automatically), develop

That's it! You are all set.

Now you can run 
```python manage.py runserver 0.0.0.0:8000```
inside VM and get your project on `127.0.0.1:8000`
Also there is nginx+uwsgi binded to your 127.0.0.1:8080 but usually you have to spend some time to set it up properly.

## Note

You may want to:

- Run `git config --global` to set your `user.name` and `user.email`
- Edit `my.cnf` file to configure charset and collation to UTF8 as follows:

```ini
[client]
default-character-set = utf8

[mysqld]
character-set-server = utf8
collation-server = utf8_general_ci
```
