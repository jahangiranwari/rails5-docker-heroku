# Docker container deployment to Heroku

Sample Rails 5 project to demonstrate deployment of a Docker container to Heroku using `heroku.yml` and `git push heroku master`

### Development setup
```
$ docker-compose build
$ docker-compose run --rm web rails db:create
$ docker-compose up
```

### Deploy to Heroku

```
$ heroku update beta
$ heroku plugins:install @heroku-cli/plugin-manifest
$ heroku apps:create --manifest
$ heroku addons:create heroku-postgresql:hobby-dev

$ heroku config:set RAILS_MASTER_KEY=`cat config/master.key`
$ heroku config:set RACK_ENV=production RAILS_ENV=production
$ heroku config:set RAILS_SERVE_STATIC_FILES=enabled
$ heroku config:set WEB_CONCURRENCY=2
$ heroku config:set LANG=en_US.UTF-8

$ git push heroku master
$ heroku run rails --trace db:migrate
$ heroku open
```
