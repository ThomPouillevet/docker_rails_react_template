# README

---
> WARNING: this README does not contain instructions for production and deployment.
---

I created this template while learning how to create a Rails app with Docker. It runs with:
* Ruby version : 2.6.6
* Rails version : 5.2.4
* A Postgres DB
* React (if needed on some views)
* Rspec & Capybara instead of default test suite

Things you may want to add:
* Devise
* Stimulus

# Deployment instructions

Clone the project

At the root add `.env/development` directory and create two files inside :

In a file named `database`add
```
POSTGRES_USER=postgres
POSTGRES_PASSWORD=some-long-secure-password
POSTGRES_DB=myapp_development
```

In a file named `web`add
```
DATABASE_HOST=database
```

Then, build the docker image with
```
docker build -t railsapp .
```

Launch the app with
```
docker-compose up -d
```

Create and migrate your DB with
```
docker-compose exec web bin/rails db:create db:migrate
```

Install Rspec and run a first test with
```
docker-compose exec web bin/rails generate rspec:install
docker-compose exec web bin/rails spec
```
