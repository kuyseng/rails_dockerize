## Step
- **clone project**
```sh
git clone git@github.com:kuyseng/rails_dockerize.git myapp
cd myapp
```
- **generate rails project**
```sh
docker run -it --rm --user "$(id -u):$(id -g)" -v "$PWD":/usr/src/app -w /usr/src/app ruby:2.6.6-slim-buster bash

$ gem install rails -v 6.1.3
$ rails new . --skip-bundle
```
- **change docker-compose**
1. RUBY_VERSION  e.g 2.6.6-slim-buster
2. NODE_MAJOR
3. YARN_VERSION
4. BUNDLER_VERSION
5. Delete one of db i.e mysql or postgres depends on the app

- **change .dockerdev/Aptfile**
1. can delete unused dependencies
2. or can add more

- **build image**
```sh
docker-compose build app
```
- **setup project base on requirement**
```sh
docker-compose run --rm app bash

$ rails webpacker:install
$ rake db:create db:migrate db:seed
```

- **run the project**
```sh
docker-compuse up -d
```

### Commands
```sh
docker-compose up        # run project in foreground
docker-compose up -d     # run project in background
docker-compose down      # stop project

docker-compose ps        # show project status
docker-compose logs -f   # show project logs

docker-compose run --rm app bash   # login app container.
docker attach domainsnipe_app      # to attach for binding.pry
```
