# PremeFeed REST API Documentation

<img src="https://avatars1.githubusercontent.com/u/16073020?v=3&s=200" />

Base URL:  server-premefeed.rhcloud.com


----------
<h1>User Routes</h1>

**Create User**

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
**Login as Existing User**

    POST /api/user/login

***Form Parameters (Content-Type: application/x-www-form-urlencoded) :***

 - **email**
 - **password**

***Example Response:***

    {
      "token": "uKcQ7qlmVQ9DeQtS"
    }
 
 ----------

**Reset User Password**

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

**Log out as existing user**

    POST /api/user/logout

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.

***Example Response:***

    {
      "message": "You have successfully logged out."
    }

**Note: When you log out your user token get's reset**

----------

**View your current user information**

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
<h1>Brand Routes</h1>

**View a list of all featured brands**

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


**View a list of all available brands**

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

**Find Brand by ID**

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
<h1>Subscription Routes</h1>

**Subscribe to a brand**

    POST /api/subscribe/:id

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.
 - **:id**: Brand ID.

***Example Response:***

    {
      "message": "Successfully Subscribed"
    }


----------

**Unsubscribe to a brand**

    POST /api/unsubscribe/:id

***URL Parameter :***

 - **access_token**: Use the token received when authenticating.
 - **:id**: Brand ID.

***Example Response:***

    {
      "message": "Successfully Unsubscribed"
    }
