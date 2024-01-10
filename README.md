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


### DB interaction - Important:

> !!!! After generating any scaffolds run ```rails db:migrate``` to update database schemas. !!!!

> !!!! to clear DB and re migrate run ```rails db:drop``` !!!!

> rails console can be used by running ```rails c``` - Allows instantiating classes(Seeding DB) in an IRB ENV

> Within seeds.rb in the config dir can add logic like ```10.times { Post.create(title: "Post title") }``` to seed our database in the dev env. 

> Migrations are used to editing a database schema/structure - This command is used to add a column to a table: ```rails g migration add_views_to_posts views:integer``` - Can also add a default value from within the new migration file before running the db:migrate command.

> Using a migration to make a DB relational: ```rails g migration add_user_to_post user:belongs_to``` This creates a one Post to many Users DB relationship. - After running this command and migrating your DB schema you will need to ensure that both Models are updated accordingly. In the ```post Model```  You can add ```belongs_to :user``` and in the ```user Model``` you can add ```has_many :posts``` to confirm the DB relationship.


### Generating scaffolds:

Pages: 
> ```rails g controller pages home about``` 

Scaffolding for full design pattern:
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


### Controllers:

> The before_action at the top of the post sets the post to be acted on in each of the controller functions by calling the first of the private functions at the bottom of the page.

> Notice how in the controllers format returns a response in both JSON and in HTML. If I were to use React on the frontend I can then send a REQ to these endpoints to access the json response at .json

> The final private function is stating tht the chosen Object requires requires certain attributes and only the selected are permitted.

> The update and save methods are similar to the mongoose methods used in a MERN app controller (under the hood they are running SQL commands)

> IF USING DEVISE FOR AUTH: Adding ```before_action :authenticate_user!``` at the top of a controller will protect all functions in this controller from being accessed without logging in. You can ensure that some are still accessible by adding ```before_action :authenticate_user!, except: %i[show index]```


### Models:

> Can add input validation for a models existing forms: ```validates :title, presence: true, length: { minimum: 5, maximum: 50 }```

> further functions would be added to the model if required.


### View files and Routing:

> ```yield``` tags at the bottom of the selected layout html.erb files is similar to ```Outlet``` in react. 

> The layout files are similar to the index.html or entry point in a react file. These files are what the page files are rendered inside of (replace yield)

> If you have go to the ```PagesController``` you will notice the home action is an empty function. This means no logic is being passed to our view file, its simply rendered the ```home``` view within the ```pages``` folder in the ```view``` file

> Within our layouts folder we can utilize the use of partials: A partial is a reusable element (similar to a react component) which can be persisted across multiple parts of the application. 

> Partials will always starts with a underscore ```_navbar.html.erb``` and can be rendered into elements as so: ```<%= render 'layouts/navbar' %>```

> button_to is similar to an onClick function in React. if deleting it takes two coma separated params as so: ```<%= button_to "Delete this post", @post, method: :delete %>``` the method: :delete signals the type of REQ being made.

> EASY TO REMEMBER - ```link_to``` for get routes - ```button_to``` for other REQ methods.

> 

##### Routing:

> Can use : ```resources :posts, only: [:index, :show]``` or ```resources :users, except: [:index]``` to specify specfic routes for certain models.

> Running ```rails routes``` from CL shows all active routes for application. Refer top to bottom (Bottom routes are auto generated by rails.)

> ```resources:example``` within the routes.rb file will generate all 7 default REST api routes for 'example'

> nested routes use a # instead of /

> Can use : ```resources :posts, only: [:index, :show]``` or ```resources :users, except: [:index]``` to specify only the specific routes you need for each different model/type.

> To define new routes in app/config/routes.rb: ```get 'about', to: 'pages#about'``` - This defines a new GET route for @ ```/about``` which will pass through the ```PagesController``` and render the 'about.html.erb' ```view``` file

> After initializing a rails app. Go to routes.rb within the app/config file. The final line commented out defines the root path. !!! AKA '/' AKA 'Home' !!!

> Setting the root as ```pages#home``` sets our rooting to go through the ```PagesController``` and find the ```home``` action

> In view files we can still use anchor tags to redirect to certain routes but using ERB's link_to approach is much better as it prevents having to write long url's and also means if we change the url destination in our routes.rb file the route itself remains the same meaning we don't have to alter multiple a tags in multiple routes:
```<%= link_to "This about is using ERB's path", about_path %>``` - The first string before the coma is what the A tag appears as the second is the route path.


### Optional extras/gem files:

* Devise:

> add ```gem 'devise'``` to bottom of gem file and run ```bundle install```

> Used for authentication: ```rails generate devise:install``` - Follow added instructions in terminal on install.

> Using devise to generate a scaffold: ```rails g devise User``` - Generates MVC for User objects. !!! MAKE SURE TO MIGRATE DB AFTER!!! You will notice in the routes.rb file that the :users endpoints are protected by a ```devise_for```

> NOTE: after scaffolding using devise the view files are not visible in the views dir. run ```rails g devise:views``` to generate the view files for exisiting devise files.

* Tailwind 

> initializing rails app with tailwind or bootstrap from start:```rails new --css <APP NAME> --css tailwind```

* Bootstrap 

> An easier approach with bootstrap than generating a new rails app with bootstrap from the get go is to add the bootstrap JS bundle and stylesheet link to the head inside of the application.html.erb entry point.