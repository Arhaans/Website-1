This is the www.emfcamp.org web site, built with Flask & Postgres by the 
EMF web team.

[![Build Status](https://travis-ci.org/emfcamp/Website.svg?branch=master)](https://travis-ci.org/emfcamp/Website)

Get Involved
============

If you want to get involved, the best way is to join us on IRC, on #emfcamp-web on chat.freenode.net.

Join with IRCCloud: <a href="https://www.irccloud.com/invite?channel=%23emfcamp-web&amp;hostname=irc.freenode.net&amp;port=6697&amp;ssl=1" target="_blank"><img src="https://www.irccloud.com/invite-svg?channel=%23emfcamp-web&amp;hostname=irc.freenode.net&amp;port=6697&amp;ssl=1" height="18"></a>

Getting Started
===============

The easiest way is to install [Docker](https://docker.com/) and use Docker Compose.

```
docker-compose up -d postgres
./prepare_db.sh
docker-compose run app make db data dev-data
docker-compose up app
```

You should then be able to view your development server on http://localhost:5000.

On subsequent runs it should be enough to just run `docker-compose up app`. To run commands within
the application's Docker container use `docker-compose run app command`. You may want
to start a shell within the container with `docker-compose run app bash`, which will
allow you to use commands mentioned elsewhere in the documentation without prefixing them
with the `docker-compose run ...` noise.

To delete all data and start over fresh you can use `docker-compose down`.

Once you've created an account, you can use `make admin` to make your user an administrator.
Or, you can create an account and simultaneously make it an admin by using `make admin ARGS="-e email@domain.tld"`

E-mail sending is disabled in development (but is printed out on the console). You can also login directly by setting BYPASS_LOGIN=True in config/development.cfg and then using a URL of the form e.g. `/login/admin@test.invalid` and navigate to `/admin/`.

For more, see:

* [Documentation](docs/documentation.md)
* [Testing](docs/testing.md)
* [Deployment](docs/deployment.md)
* [Contributing](.github/CONTRIBUTING.md)


### Additional Notes

- `make migrate` to generate migration scripts when models have been updated.
- `make db` to run any migration scripts you've generated.
