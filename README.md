# PremeFeed REST API Documentation

Base URL:  server-premefeed.rhcloud.com

Have any questions? contact <a href="mailto:thepcmrtim@gmail.com">Peter</a> or <a href="mailto:steelesam72@gmail.com">Sam</a> for help.

# User Routes

<h3>Create User</h3>

    POST /api/user/register

***Form Parameters (Content-Type: application/x-www-form-urlencoded) :***

 - **name**
 - **email**
 - **password**

***Example Response:***

    {
      "token": "9eaXLcOyLcXvuYKn",
      "email": "ayy@lmao.com",
      "name": "Ayy Lmao",
      "_id": "572c08f40b026afc4e5a0876",
      "subscriptions": [],
      "created_at": "2016-05-06T03:01:08.896Z"
    }

----------
<h3>Login as Existing User</h3>

    POST /api/user/login

***Form Parameters (Content-Type: application/x-www-form-urlencoded) :***

 - **email**
 - **password**

***Example Response:***

    {
      "token": "uKcQ7qlmVQ9DeQtS"
    }
 
 ----------

<h3>Reset your password</h3>

    POST /api/user/reset

***Form Parameters (Content-Type: application/x-www-form-urlencoded) :***

 - **currentPassword**
 - **newPassword**

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.

***Example Response:***

    {
      "message": "Password successfully changed"
    }

----------

<h3>Edit Profile </h3>

    PUT /api/user/edit

***Form Parameters (Content-Type: application/x-www-form-urlencoded) :***

 - **name**
 - **email**

***URL Parameter:***

 - **access_token**: Use the token received when authenticating.

***Example Response:***

    {
      "message": "Profile successfully changed."
    }

----------

<h3>Log out</h3>

    POST /api/user/logout

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.

***Example Response:***

    {
      "message": "You have successfully logged out."
    }

**Note: When you log out your user token get's reset**

----------
<h3>View your current user information</h3>

    GET /api/user/me

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.

***Example Response:***

    {
      "_id": "571ee1957d0072aa053aa9df",
      "token": "E2nNQWSrZBbaEUup",
      "email": "thepcmrtim@gmail.com",
      "name": "Peter Soboyejo",
      "isAdmin": true,
      "subscriptions": [
        {
          "_id": "57228edb83562f0a59198c2a",
          "availability": true,
          "featuredImage": "http://www.nycgo.com/images/460x285/SupremeV1_460x285.jpg",
          "url": "http://www.supremenewyork.com/",
          "description": "Skateboards & related gear, sneakers & house-brand streetwear make this SoHo shop a skater mecca.",
          "name": "Supreme New York",
          "isFeatured": true,
          "products": [],
          "subscriberCount": 1
        }
      ],
      "created_at": "2016-04-26T03:33:41.189Z"
    }

----------
# Brand Routes

<h3>View a list of all featured brands</h3>

    GET /api/brand/list/featured

***Example Response:***

    [
	    {
	    "_id": "5722bb8b0fa0e67f6210c837",
	    "availability": true,
	    "featuredImage": "http://i.imgur.com/gvcHX7O.jpg",
	    "url": "http://www.lxrdknows.com/",
	    "description": "LXRDKNOWS IS FOR THE MISUNDERSTOOD KIDS WHO DONT KNOW THEIR PURPOSE AND RELY ON THE STREETS",
	    "name": "Lxrd Knows",
	    "isFeatured": true,
	    "products": [],
	    "subscriberCount": 0
	    },
	    {
	    "_id": "57228edb83562f0a59198c2a",
	    "availability": true,
	    "featuredImage": "http://www.nycgo.com/images/460x285/SupremeV1_460x285.jpg",
	    "url": "http://www.supremenewyork.com/",
	    "description": "Skateboards & related gear, sneakers & house-brand streetwear make this SoHo shop a skater mecca.",
	    "name": "Supreme New York",
	    "isFeatured": true,
	    "products": [],
	    "subscriberCount": 1
	    }
    ]

----------


<h3>View a list of all available brands</h3>

    GET /api/brand/list

***Example Response:***

    [
	    {
	    "_id": "5722bb8b0fa0e67f6210c837",
	    "availability": true,
	    "featuredImage": "http://i.imgur.com/gvcHX7O.jpg",
	    "url": "http://www.lxrdknows.com/",
	    "description": "LXRDKNOWS IS FOR THE MISUNDERSTOOD KIDS WHO DONT KNOW THEIR PURPOSE AND RELY ON THE STREETS",
	    "name": "Lxrd Knows",
	    "isFeatured": true,
	    "products": [],
	    "subscriberCount": 0
	    },
	    {
	    "_id": "57228edb83562f0a59198c2a",
	    "availability": true,
	    "featuredImage": "http://www.nycgo.com/images/460x285/SupremeV1_460x285.jpg",
	    "url": "http://www.supremenewyork.com/",
	    "description": "Skateboards & related gear, sneakers & house-brand streetwear make this SoHo shop a skater mecca.",
	    "name": "Supreme New York",
	    "isFeatured": true,
	    "products": [],
	    "subscriberCount": 1
	    }
    ]

----------

<h3>Find Brand by ID</h3>

    GET /api/brand/:id

***URL Parameter :***

 - **:id** : Use ID associated with a brand to find it. You can get the IDs by checking out `/api/brand/list` or `/api/brand/list/featured`

***Example Response:***

    {
	    "_id": "5722bb8b0fa0e67f6210c837",
	    "availability": true,
	    "featuredImage": "http://i.imgur.com/gvcHX7O.jpg",
	    "url": "http://www.lxrdknows.com/",
	    "description": "LXRDKNOWS IS FOR THE MISUNDERSTOOD KIDS WHO DONT KNOW THEIR PURPOSE AND RELY ON THE STREETS",
	    "name": "Lxrd Knows",
	    "isFeatured": true,
	    "products": [],
	    "subscriberCount": 0
    }


----------
# Subscription Routes

<h3>Subscribe to a brand</h3>

    POST /api/subscribe/:id

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.
 - **:id**: Brand ID.

***Example Response:***

    {
      "message": "Successfully Subscribed"
    }


----------

<h3>Unsubscribe to a brand</h3>

    POST /api/unsubscribe/:id

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.
 - **:id**: Brand ID.

***Example Response:***

    {
      "message": "Successfully Unsubscribed"
    }
