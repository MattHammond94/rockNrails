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

> IMPORTANT - Rails will automatically include a git repo (This is great!) However if you're working from a repo that already has a git repo this will mean the new repo would be classed as a submodule. use```rm -fr .git``` from new project to remove git repo.

> !!!! After generating any scaffolds run ```rails db:migrate``` to update database schemas. !!!!

> rails console can be used by running ```rails c``` - Allows instantiating classes in an IRB ENV

### Generating scaffolds:

Pages: 
> ```rails g controller pages home about``` 



>  !!! ```rails g scaffold``` !!!

> running the above command followed by ```<OBJECT NAME>``` will generate:
* An ```<OBJECT NAME>```Controller
* An ```<OBJECT NAME>``` model
* An ```resources :<OBJECT NAME>``` added to the routes.rb file
* A set of view files in the views folder
* A set of testing files for ```<OBJECT NAME>```

> ```rails d scaffold <OBJECT NAME>``` : will destory all files just scaffolded.

> By default all models come with timestamps. adding extra fields looks as below:

```rails g scaffold books title:string publication_year:integer```



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