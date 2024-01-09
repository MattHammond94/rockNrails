# Ruby On Rails

### Overview

> This repo is used for all learning materials I will be following for learning the fundamentals of Ruby on Rails.

### Rails for Ruby

* Rails is a framework for Ruby based backend

```gem install rails```

> Rails 7 provides import maps allowing use of JS modules directly from browser. 

* Although this is the case it is best to use Yarn as some files may need to be compiled or bundled.

* Yarn is another package manager - like npm or bundler.

> Installed yarn globally in past. run: ```yarn -v``` to check version.


* Creating a rails app from chosen directory: ```rails new rails_app```

* running a rails app: ```rails server``` or ```rails s```

> After generating any scaffolds run ```rails db:migrate``` to update database schemas.

> rails console can be used by running ```rails c``` - Allows instantiating classes in an IRB ENV

### Routing:

> ```rails routes``` shows all current routes for application.

> ```resources:example``` within the routes.rb file will generate all 7 default REST api routes for 'example'

> Can use : ```resources :posts, only: [:index, :show]``` or ```resources :users, except: [:index]``` to specify specfic routes for certain models. 

> ```get '/somepath', to: 'somecontroller#someaction'``` specifies a custom path (non-RESTful)

### Controllers:

> 




### Optional extras/gem files:

> Devise - used for authentication: ```rails generate devise:insta``` - Follow added instructions in terminal on install.

> Using devise to generate 

> initializing rails app with tailwind or bootstrap from start:```rails new --css <APP NAME> --css tailwind```