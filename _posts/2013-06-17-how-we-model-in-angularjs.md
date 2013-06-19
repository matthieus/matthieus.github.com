---
layout: post
category: Sharing Code
---
{% include JB/setup %}

This post follows a [blog post](http://eviltrout.com/2013/06/15/ember-vs-angular.html) about some of AngularJS weaknesses, how to model being the main subject. There isn't one idiomatic way to use a model in AngularJS and this lack of guidance was considered a problem. I think this is a strength on the contrary. AngularJS doesn't force the way you access your data, but it doesn't leave you alone either. The different features will give you different options that will make sense or not for your particular set of features.
To illustrate that opinion I'll describe the way we make our model accessible in one part of our application.

# Model basics

Our application provides partial CRUD on pre-existing objects, with some sometimes complex business processing done server side. On the client side, there are many rules about what can be modified, depending on object states, depending on privileges and depending on ownership. So there is a lot of dependencies between different areas of our model.
To tackle that issue, we use a global model. We don't use services or resources, our model is directly on a global scope. And we don't use the rootScope either, we use the scope corresponding to what contains our app, footer and header excluded. Here is how it looks like:

    app.controller('GlobalCtrl', function($scope) {
        $scope.model     = {/* contains model objects coming from the server */};
        $scope.refresher = {/* contains refresh methods allowing to refresh the model objects. Conventions says method name = object name. */};
        $scope.global    = {/* contains some global state relevant for the client side. */};
    });

Refreshers are method named with the same name as the objects contained in the model (user object will give user() method to refresh the user object). The refresher is the only way to update the model. The purpose of that is to have the model containing only valid committed data coming from the server.

For the controller organisation, we have more or less one controller per object, but we don't have any hard rule there (yet). Here is a sample of one:

    app.controller('UserCtrl', function($scope, $http) {
        $scope.refresher.user = function() {
            $http.get('app/user', {'userID': $scope.global.userID})
            .success(function(data) {
                $scope.model.user = data;
            });
        };
        // initialize the data at load time
        $scope.refresher.user();
    });

Very simple, but what does it give us?
+ the global model is an exact reproduction of the DTO defined on the server side.
+ this gives access from anywhere in the app to $scope.model.user.someProperty, which gives {{model.user.someProperty}} in the HTML. We thought this maximises the expressiveness of the HTML code, where you know what is model data and what is local data.
+ the refresher method is the only way to update the model. Our convention is to NEVER update the model directly, the model must be a representation of what's on the server.

So if we want to modify some data, this will look like:

    app.controller('UserCtrl', function($scope, $http) {
        $scope.modifyName = function(newName) {
            $http.post('app/user/modifyName', {'name': newName})
            .success(function(data) {
                $scope.refresher.user();
                $scope.refresher.history();
                // + potentially other refresher calls if 
                // we know some other parts of the model have been impacted
            })
            .error(function(data, status) {
                displaySomeAlert(data, status);
            });
        };
    });

We can see the use of refreshers in the code above, the relevant refreshers are called when the POST returns.  
_Note:_ From a server roundtrip point of view, this method is ineffecient. We could return the modified objects with the POST response, but that would assume that the server knows what is the data that should be updated on the screen, that's a mix of concern I'd be ready to accept only if really necessary.

# Questioning that choice

My colleagues asked a few questions about that design, below are some attempts to answer.

+ _Why not using angular services or resources factories to access the objects and the corresponding methods to do CRUD on that object?_  

The model is part of the scope for 2 reasons:
1. you can do \{\{model.user.property\}\} from anywhere in the HTML, without having to create scoped data through a controller
2. the model is readonly, modifications are done by methods that will modify only values and not whole objects. Symmetry between reading and writing methods don't make sense in our context (and I expect this happens in a lot of contexts). To reflect the changes on the displayed data, the relevant refreshers are called once the data has been modified.

+ _Why not using the $rootScope instead of "global" scope?_

We could definitely use the rootScope, but it feels like the rootScope is too _global_ for a business model. We use the rootScope, but to contain things like our resource bundles and utility methods. We might be wrong to not use the rootScope for everything global though.

+ _Isn't it dangerous to rely on convention to avoid people modifying the model directly?_  

Note: If you didn't follow, only the refresher methods are allowed to update the model, so the data displayed is always committed data from the server. Also refresher must be called with the same name as the model objects.

It is a weakness, but if you show the right example and keep an eye open for dangerous behaviour, you will be fine.

+ _Doing 2+ server calls when at most 1 is enough feels violently inefficient. How do you live with yourself?_  

Good question ...
There should be a way to group HTTP requests and responses together. Maybe there is a global solution that can be applied there. If you have a solution for that issue, I thank you in advance for your help!

+ _If it is inefficient, why did you choose that design?_  

Simplicity, expressiveness and productivity. These are also the reasons we chose AngularJS in the first place. Our app was first written (not by us) using jQuery and a cohort of plugins and libraries, and it ended up bloated, difficult to maintain ... and inefficient. By migrating to AngularjJS and this global model, the amount of javascript has been reduced to 1/5 and we use much less third party libraries. The server side code was also considerably reduced. Now our main problem is that we have difficulties to get use to our new productivity as our estimates are now way too pessimistic.