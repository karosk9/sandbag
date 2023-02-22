# README
**App Setup**

- install Docker and run in the terminal:

```bash
docker volume create ruby-bundle-cache
alias docked='docker run --rm -it -v ${PWD}:/rails -v ruby-bundle-cache:/bundle -p 3000:3000 ghcr.io/rails/cli'
```


```
docker-compose build
docked bundle install
docker-compose run web rails db:create
docker-compose run web rails db:migrate
```


**Running app on docker:**

Running web rails console with dockerized container:

If there are any changes to gems:
```bash
docked bundle install
```

run docker in detached mode 
```bash
docker-compose up -d
```

show interactive rails server logs:
```bash
docker attach <webcontainer id>
```

Running rails console:
```bash
docker-compose run web rails c 
```

**Debugging**

just add to your code:
```bash
debugger 
```

to find out more about debugging with debug check: https://guides.rubyonrails.org/debugging_rails_applications.html#debugging-with-the-debug-gem

example of more advanced debugging logic:
```bash
debugger(do: "catch ActiveRecord::RecordInvalid do: info")
```

rdbg will be automatically called by debug and allow to interactively debug your application.

**Code quality**

just run following command to dectect and fix all violations:

```bash
standardrb --fix
```



Things you may want to cover:

* DATABASE: PostgreSQL 15.2

* Ruby version 3.2.1

* Rails version 7.0.4

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
