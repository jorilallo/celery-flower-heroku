# Celery Flower monitoring for Heroku

[Flower](https://github.com/mher/flower/) is a handy tool for monitoring [Celery](http://www.celeryproject.org/) processes. As it's build on top of Tornado web server it needs it's own outside facing port and can't be run as part of your regular Heroku app which only provides one ```web``` process type. Luckily Flower is really easy to install as another app and can be run free of charge on Heroku.

This project template/guide helps you to bootstrap the process and creates a simple app for running Flower.

Clone the repo:

    git clone https://github.com/jorilallo/celery-flower-heroku.git

Create an Heroku app:

    heroku create APP_NAME

Add database for persistance:

    heroku addons:create heroku-postgresql:hobby-dev
    heroku config:set DATABASE_URL=<copy the newly created database url here>

Configure the app by providing your broker url (RabbitMQ, Redis, what have you) and a password for logging into Flower:

    heroku config:set BROKER_URL=redis://...
    heroku config:set FLOWER_BASIC_AUTH="username:password"

Push to heroku:

    git push heroku master

Now visit the app. It will ask for a username and a password which you defined above.
