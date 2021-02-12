---
layout: post
title:      "Using a Rails API With Javascript"
date:       2021-02-12 13:22:56 -0500
permalink:  using_a_rails_api_with_javascript
---


As a student at Flatiron School, I learned how to create the backend with Ruby on Rails, and the front end with JavaScript. Before moving on to learn React, I had to learn how to bring Rails and JS together into one application.

This concept was one that seemed more complex at first glance than it turned out to be once I really got into it, so I'm writing this tutorial for anyone else who is intimidated at the prospect of learning to combine these two tools.

The first thing to do starting off is to create two separate directories, one for your backend and one for your frontend. This is different from projects built solely with Ruby on Rails where you would keep everything in one directory.

The reason for this is that we are going to be using Rails for our backend and JS for our frontend. To keep things simple, I like to name the two directories very explicitly - backend and frontend.

After doing that, go ahead and go through all of the usual steps for creating your Ruby on Rails backend: 

* Create the models and relationships
* Create the database tables and any seed data that you want
* Create your controllers

The main difference between the backend that we're creating here and the backends that you will be used to creating with Rails is that here we *don't create any views.* Instead of rendering our webpage and data with views, we'll be doing that with JavaScript.

When you're building out your frontend, you'll be creating functions that create and display elements. In order for that to work, your JS needs to be able to read the data from your backend, we will need to send that data in a way that is accessible.

To do that, we will be making some changes to our controllers. Instead of displaying our objects in the way we did before, we will be rendering them in the json format.

```
 def show
        user = User.find_by(id: params[:id])
            if user
            render json: user, except: [:created_at, :updated_at]
        else
            render json: {message: "User not found."}
        end
    end

```

As you can see here, we are rendering properties of the user object in the json data format, one that is easily readable by our JS code and will allow us to access that data via various fetch requests.

```
function fetchFavorites(){
    fetch(BASE_URL + '/users/' + currentUser.id + '/favorites')
    .then(res => res.json())
    .then(favorites => putFavoritesOnDom(favorites))
}
```

Once you learn how your Rails API and your JS code work together, it's pretty simple. 
```
function loggedInUser(object){
    currentUser = object
    signupForm.style.display = 'none'
    welcome.innerHTML = `<h3>Hello, <i>${currentUser.email}</i> !</h3>`
    // logout.innerText = "Logout"
		}
```
In the above example, you see how we can display data from our backend on the webpage. 

This was just a basic tutorial in how to begin using these tools. For more information, and for live examples, I would recommend looking up some of the live coding lectures that have been published by the excellent instructors here at Flatiron!
