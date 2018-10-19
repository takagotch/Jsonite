### Jsonite
---

https://github.com/crepe/jsonite

npm
https://www.npmjs.com/package/jsonite
gem
https://rubygems.org/gems/jsonite/versions/0.0.3


```
gem 'jsonite'

```

```ruby
class TodoPresenter < Jsonite
  property :description
end

require 'todo_presenter'
class UserPresenter < Jsonite
  property :id
  property :email
  embed :todos, with: TodoPresenter
  link do |context|
    context.user_url self
  end
end

# users_presenter.rb
require 'user_presenter'
class UsersPresenter < Jsonite
  property :count
  embed :users, with: UserPresenter do |context|
    self
  end
end

# users_controller .rb
require 'users_presenter'
require 'user_presenter'
class UsersController < ApplicationController
  def index
    user = User.find params[:id]
    render json: UserPresenter.new(user, context: self)
  end
  #{
  #  "count": 12,
  #  "_embedded": {
  #    "users": {
  #    }
  #  }
  #}
  
  def show
    user = User.find params[:id]
    render json: UserPresenter.new(user, context: self)
  end
  #{
  #  "id": "Bolibpyjetu8",
  #  "email": "stephen@ex.com",
  #  "_embedded": {
  #    "todos": [
  #      {
  #         "description": "Buy milk"
  #      }
  #    ]
  #  },
  #  "_links": {
  #    "self":{
  #      "href": "http://example.com/users/Bolibpyjetu8"
  #    }
  #  }
  #}
  
end




```

```
```

