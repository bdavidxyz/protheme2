---
layout: post
author: David Boureau
minread: 6
title: "Rails 6 and Active Job tutorial"
date: 2020-07-14
categories: work
permalink: /blog/:title/
description: "Rails 6 and Active Job : a tutorial"
---


## 1. Overview

Active Job is a feature of the Ruby-on-Rails framework, that allows you to launch heavy jobs in the background.

For example, scraping or mailing are these kind of jobs, that are 

 - time-consuming, 
 - asynchronous, 
 - launched at pre-defined time

They are the exact opposite of the request/response pattern of your web server, that is fast, synchronous, and launched at anytime.

A serious drawback is requires a lot more tooling than the "rails new" command offers.

Even building the simplest "hello world" job is not *that* simple.

This tutorial is dedicated to those who 
 - 🕒 have few time to learn, 
 - ❤️ loves to learn by example


## 2. Steps to reproduce

### 2a. Prerequisites

```bash

$> git --version
git version 2.7.2
$> docker -v
Docker version 17.12.0-ce
$> docker-compose -v
docker-compose version 1.18.0
```

Any upper version should work

### 2b. Installation

```bash

~/workspace/$ git clone https://github.com/bdavidxyz/rails_sidekiq_docker

~/workspace/$ cd rails_sidekiq_docker

~/workspace/rails_sidekiq_docker$> docker-compose build
... build images

~/workspace/rails_sidekiq_docker$> docker-compose run --rm --no-deps web rails new . --skip --database=postgresql
... create new rails project

~/workspace/rails_sidekiq_docker$> ./.dockerdev/post_build.sh
... create and modify some files

~/workspace/rails_sidekiq_docker$> docker-compose up
```

Now go to [localhost:3000/sidekiq](http://localhost:3000/sidekiq)

Hurray ! You can monitor every job.

I suggest you to see in more details docker-compose, to see how all the tools talks to each other.

I also suggest to go to every file created or modified by post_build.sh

## 3. Create a "hello world" job

create file app/jobs/hello_world_job.rb

```ruby
# app/jobs/hello_world_job.rb
class HelloWorldJob < ApplicationJob
  queue_as :default

  def perform(*args)
    p 'hello from HelloWorldJob'
  end

end
```

modify file app/controllers/welcome_controller.rb to call your job

```ruby
# app/controllers/welcome_controller.rb
class WelcomeController < ApplicationController
  def index
    HelloWorldJob.set(wait: 15.seconds).perform_later
  end
end
```

Now go to [localhost:3000](http://localhost:3000), it will ask to enqueue the HelloWorldJob since the request goes through WelcomeController#index function.

Now go to [localhost:3000/sidekiq](http://localhost:3000/sidekiq), you will see the job in the "scheduled" section. 

After a few seconds, it appears in the "Processed" section


## 4. Conclusion

We have built a working "hello world" job in less than 3 minutes, without side-effects, with all required tooling and configuration.

Enjoy !

😍😍😍

David.


