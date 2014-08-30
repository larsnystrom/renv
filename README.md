Remote Environment Management
=============================

Background
----------

We have to move our web app from Heroku to our own VPS. The problem is that we've built backup scripts and such around heroku's API, especially `heroku config`.

This is an attempt to get the same functionality as `heroku config` by using ssh to read/write to the `.env` file on our server.

Requirements
------------

* Bash (Probably 3 or 4)

Installation
------------

You must have shell access and read/write permissions to the `.env` file on the server you are using. No other setup is required on the server.

Run `renv` from your client.

Usage
-----

`renv config` Print all environment variables  
`renv config:get KEY` Print the value of a specific environment variable.  
`renv config:set KEY=VAL` Set an environment variable.  
`renv config:unset KEY` Delete an environment variable.  

The app is selected by specifying an SSH host and the path to the `.env` file.

    renv config --host user@domain.com --env-file /var/www/app/.env

If you are using `renv` inside a git repo, you can specify a remote instead of a host.

    renv config --remote production --env-file /var/www/app/.env

If you use a remote to specify the host, you can optionally save the .env filepath with git config.

    git config renv.production.envfile /var/www/app/.env
    # Now we do not need to specify --env-file when working with the production remote.
    renv config --remote production

Issues
------

Please report any issues [here](https://github.com/larsnystrom/renv/issues).


Author and License
------------------

Written by Lars Nyström. Licensed under the MIT license.
