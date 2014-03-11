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
- clone or put your project into src dir
- `vagrant up`
- get your project inside VM in WWW dir, install requirements, do stuff (virtualenv is created and activated automatically)

That's it! You are all set.

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
