---
title: Kings.ge - API Reference

language_tabs:
  - http

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the kings.ge API

#Making Requests
##Headers
HTTP header fields.
<h3>Accept</h3>
<p>
API requires that clients send a valid Accept header with every request. This also voids the default API version and format.
</p>
<ul>
  <li>API versions: <code class="prettyprint">v1</code></li>
  <li>API formats: <code class="prettyprint">json</code></li>
</ul>

##Languages
<p>
  Available languages: ka
</p>
<p>  
  Request with lang parameter is not neccessary, default language always is georgian.
</p>

# Authentication

> To authorize, use this code:

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
``` -->

> Make sure to replace `meowmeowmeow` with your API key.

Some api

# Main page

<!-- Get menu tree -->

## Get menu tree
<p>
  This service retreives menu tree
</p>
<p>
  Tree - Objects
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "tree": {
      "link": "title"
    }
  }
}
```

<p>
  This endpoint retrieves menu tree
</p>

<!-- Get slider -->

## Get slides
<p>
  This service retreives all slides
</p>
<p>
  Slides - Objects
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "slides": [
      {
        "id": "slideID",
        "src": "slideImg",
        "active": "slideIsActive",
        "order_number": "sliderOrderNumb",
        "locale": "ka",
        "created_at": "slideCreatedAt",
        "updated_at": "slideUpdateAt",
        "link": "SlideLink",
        "mobileSrc": "Image for mobile devices"
      }
    ]
  }
}
```

<p>
  This endpoint retrieves all slides
</p>

<p>
  If is null link - hide show more button   
</p>

<!-- Get memberCount -->
## Get memberCount
<p>
  This service retrieve counted members
</p>
<p>
  memberCount - Integer
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "memberCount": "memberCount"
  }
}
```

<p>
  This endpoint retrieves counted members
</p>


### HTTP Request

`GET http://kings.ge/Api/memberCount`

<!-- Get registrationIsActive -->
## Get registrationIsActive
<p>
  This service retrieve register is active or not
</p>
<p>
  isActive - Boolean
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "isActive": "isActive"
  }
}
```

<p>
  This endpoint retrieves boolean
</p>


### HTTP Request

`GET http://kings.ge/Api/registrationIsActive`


###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- Profile registration and auth -->

# Profile registration and auth

<!-- Get schools by city -->
## Get schools by city
<p>
  This service is return schools by city_id
</p>
<p>
  Schools - Objects
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "schools": {
      id: id,
      label:label
      ....
    }
  }
}
```

This endpoint retrieves schools of city

### HTTP Request

`GET http://kings.ge/Api/getSchoolsByCity/{city_id}`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- |
city_id | For tbilisi schools e.g : http://kings.ge/Api/getSchoolsByCity/1

<!-- Get teacher by school -->
## Get teachers by school
<p>
  This service is return teacher by school_id
</p>
<p>
  Teachers - Objects
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "teachers": {
      id: id,
      label:label
      ....
    }
  }
}
```

This endpoint retrieves teachers of school

### HTTP Request

`GET http://kings.ge/Api/getTeachersBySchool/{school_id}`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- |
school_id |  e.g : http://kings.ge/Api/getSchoolsByCity/1


<!-- Register To Profile GET/POST -->
## Register To profile GET/POST

    
> The above command returns JSON structured like this:

```json
{
  "status" : "ok",
  "phone" : "5555555555",
  "isMobileVerified": 0
}
```

### HTTP Request GET

`GET http://kings.ge/Api/getRegisterData/1`

<p>
  This endpoint retrieves all field of profile registration
</p>


### HTTP Request POST

<p>
  This service is registration in profile
</p>
<p>
  Fields - name,surname,phone,email(not required),password,password confirmation,city,school, class
</p>

<p>
  This endpoint creates new user in profile
</p>

<p>
  except email all fields is required
</p>

`POST http://kings.ge/Api/Auth/register`

    If register is success service returns response in JSON format:
    It means that user is successfuly registered and system send verification code to requested phone and need to verify his phone number
    


## Verify Phone Number

<p>
  This service for verify mobile number
</p>

<p>
  Fields required - phone, code(verifiction code received from the system to requested phone number)
</p>

<p>
  This endpoint verifys the phone number and returns response ( isMobileVerified=1 and the welcome text which must be used only once. This text must be shown on the profile main page when user is logged in first time only) 
</p>


### HTTP Request

`POST http://kings.ge/Api/Auth/checkVerify`

## Send again

<p>
  This service is used to send verification code to the requested phone (Any service which uses sending sms to the phone number is limited 5 sms per day (24 hours))
</p>

<p>
  Fields required - phone
</p>


### HTTP Request

`POST http://kings.ge/Api/Auth/sendAgain`

## Forgot password

<p>
  This service is used to reset user's current password and send newly setted password to the requested phone number
</p>

<p>
  Fields required - phone
</p>


### HTTP Request

`POST http://kings.ge/Api/Auth/forgotPassword`

## Auth
<p>
  This service is auth and return token
</p>
<p>
  Fields - email or phone, password
</p>


> The above command returns JSON structured like this:

<p>
  All fields are required
</p>

### HTTP Request

`POST http://kings.ge/Api/Auth/Authenticate`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- Registration on olympiad -->

# Registration on olympiad

## Get fields for registration
<p>
  This service is registration on olympiad without profile
</p>
<p>
  Fields - Objects
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "cities": {
      ...
    },
    "schools": {
      ...
    },
    "school_classes": {
      ...
    }
    ....
  }
}
```

<p>
  This endpoint retrieves all field of olympiad registration
</p>

### HTTP Request

`GET http://kings.ge/Api/getRegisterData`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- Get schools by city -->
## Get schools by city
<p>
  This service is return schools by city_id
</p>
<p>
  Schools - Objects
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "schools": {
      id: id,
      label:label
      ....
    }
  }
}
```

This endpoint retrieves schools of city

### HTTP Request

`GET http://kings.ge/Api/getSchoolsByCity/{city_id}`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- |
city_id | For tbilisi schools e.g : http://kings.ge/Api/getSchoolsByCity/1

<!-- Get teacher by school -->
## Get teachers by school
<p>
  This service is return teacher by school_id
</p>
<p>
  Teachers - Objects
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "teachers": {
      id: id,
      label:label
      ....
    }
  }
}
```

This endpoint retrieves teachers of school

### HTTP Request

`GET http://kings.ge/Api/getTeachersBySchool/{school_id}`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- |
school_id |  e.g : http://kings.ge/Api/getSchoolsByCity/1

<!-- Post register -->
## Post registration
<p>
  This service store registration
</p>
<p>
  All registartion data is required
</p>

> The above command returns JSON structured like this:


### HTTP Request

`Post http://kings.ge/register`


# Text Pages

## Get Ana's page
<p>
  This page is news type and has posts,
</p>
<p>
  Posts - Objects
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "posts": {
      "total": 9,
      "per_page": 4,
      "current_page": 1,
      "last_page": 3,
      "next_page_url": "url",
      "prev_page_url": null,
      "from": 1,
      "to": 4,
      "data": [
        {
          "id": "itemId",
          "heading": "ItemTitle",
          "cover_photo": "itemPhoto",
          "content": "itemContent",
          "created_at": "itemCreatedAt",
          "updated_at": "itemUpdatedAt"
        }
      ]
    },
    "pageTitle": "postTitle"
  }
}
```

This endpoint retrieves each post of ana

### HTTP Request

`GET http://kings.ge/Api/ana`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- |
page | For pagination needs parameter e.g : http://kings.ge/Api/ana?page=2


## Get Ana's each post
<p>
  This is detail page of Ana's post
</p>
<p>
  Post - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "post": {
      "id": "itemId",
      "heading": "itemTitle",
      "cover_photo": "itemPhoto",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt"    
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves all posts of ana's page.

### HTTP Request

`GET http://kings.ge/Api/ana/{id}`

###Headers
Header | Description
--------- | ------- | 
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- | 
{id} | For pagination needs parameter e.g : http://kings.ge/Api/ana/{id}

<!-- news page -->

## Get news page
<p>
  This page is news type and has posts,
</p>
<p>
  Posts - Objects
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "posts": {
      "total": 511,
      "per_page": 4,
      "current_page": 1,
      "last_page": 128,
      "next_page_url": "url",
      "prev_page_url": null,
      "from": 1,
      "to": 4,
      "data": [
        {
          "id": "itemId",
          "heading": "itemTitle",
          "cover_photo": "itemPhoto",
          "content": "itemContent",
          "created_at": "itemCreatedAt",
          "updated_at": "itemUpdatedAt"
        }
      ]
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves each post of news

### HTTP Request

`GET http://kings.ge/Api/news`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- |
page | For pagination needs parameter e.g : http://kings.ge/Api/news?page=2


## Get news each post
<p>
  This is detail page of Ana's post
</p>
<p>
  Post - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "post": {
      "id": "itemId",
      "heading": "itemTitle",
      "cover_photo": "itemPhoto",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt"    
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves all posts of ana's page.

### HTTP Request

`GET http://kings.ge/Api/news/{id}`

###Headers
Header | Description
--------- | ------- | 
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameter | Description
--------- | ------- | 
{id} | For pagination needs parameter e.g : http://kings.ge/Api/news/{id}

<!-- about page -->

## Get about page
<p>
  This page is text page
</p>
<p>
  Page - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "page": {
      "id": "itemId",
      "title": "itemTitle",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt" , 
      "slug": "slug"
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves about page

### HTTP Request

`GET http://kings.ge/Api/about`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- payment page -->

## Get payment page
<p>
  This page is text page
</p>
<p>
  Page - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "page": {
      "id": "itemId",
      "title": "itemTitle",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt" , 
      "slug": "slug"
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves payment page

### HTTP Request

`GET http://kings.ge/Api/payment`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- Payment Action -->

## Payment Action
<p>
  This service returns redirect url of cartu payment page
</p>

This endpoint retrieves payment page

### HTTP Request

`GET http://kings.ge/Api/getPaymentUrl`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- partners page -->

## Get partners page
<p>
  This page is text page
</p>
<p>
  Page - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "page": {
      "id": "itemId",
      "title": "itemTitle",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt" , 
      "slug": "slug"
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves partners page

### HTTP Request

`GET http://kings.ge/Api/partners`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- contact page -->

## Get contact page
<p>
  This page is text page
</p>
<p>
  Page - Object
</p>
<p>
  PageTitle - Title of page
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "page": {
      "id": 1,
      "address": "address",
      "email": "email",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt"
      "emails": [
        "subject" : "email addres",
        ...
      ]
    },
    "pageTitle": "კონტაქტი"
  }
}
```

This endpoint retrieves contact page

### HTTP Request

`GET http://kings.ge/Api/contact`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- places page -->

## Get places page
<p>
  This page has lists
</p>
<p>
  lists - Objects
</p>
<p>
  PageTitle - Title of page
</p>

> The above command returns JSON structured like this:

```json
{
  "data": {
    "lists": [
      {
        "id": "itemId",
        "city": "itemCity",
        "address": "itemAddress",
        "map_link": "itemMapLink",
        "created_at": "itemCreatedAt",
        "updated_at": "itemUpdatedAt"
      }
    ],
    "pageTitle": "Title of page"
  }
}
```

This endpoint retrieves places page

### HTTP Request

`GET http://kings.ge/Api/places`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response


<!-- schedule page -->

## Get schedule page
<p>
  This page is text page
</p>
<p>
  Page - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "page": {
      "id": "itemId",
      "title": "itemTitle",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt" , 
      "slug": "slug"
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves schedule page

### HTTP Request

`GET http://kings.ge/Api/schedule`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- rules page -->

## Get rules page
<p>
  This page is text page
</p>
<p>
  Page - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "page": {
      "id": "itemId",
      "title": "itemTitle",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt" , 
      "slug": "slug"
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves rules page

### HTTP Request

`GET http://kings.ge/Api/rules`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- preparation page -->

## Get preparation page
<p>
  This page is text page
</p>
<p>
  Page - Object
</p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "page": {
      "id": "itemId",
      "title": "itemTitle",
      "content": "itemContent",
      "created_at": "itemCreatedAt",
      "updated_at": "itemUpdatedAt", 
      "slug": "slug"
    },
    "pageTitle": "pageTitle"
  }
}
```

This endpoint retrieves preparation page

### HTTP Request

`GET http://kings.ge/Api/preparation`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

<!-- rating page -->

## Get ratings page
<p>
  This page is text page
</p>
<p>
  list - Objects, if has not parameters - [],
</p>
<p>
  schoolClasses - For select box (school_class_id)
</p>

<p>
  active_ratings - For tabs (result_context_id)
</p>
<p>For more details <a target="_blank" href="http://kings.ge/ratings">http://kings.ge/ratings</a></p>
<p>
  PageTitle - Title of page
</p>


> The above command returns JSON structured like this:

```json
{
  "data": {
    "pageTitle": "Title of page",
    "list": [
      {
        "id": "itemId",
        "result_context_id": "itemContextId",
        "uid": "itemUid",
        "school_class": "itemSchoolClass",
        "city": "itemCity",
        "tel": "itemTel",
        "saerto_qula": "itemSaertoQula",
        "woonder_qula": "itemWoonderQula",
        "results": "itemResults",
        "result_woonder": "",
        "school_class_id": "itemSchoolCLassId",
        "created_at": "itemCreatedAt",
        "updated_at": "itemUpdatedAt",   
        "seen": "itemSeend",
        "wseen": "itemWseen",
        "wactive": "itemWactive",
        "saxeli": "itemSaxeli",
        "block": "itemBlock",
        "priority": "itemPriority",
        "comment": null,
        "color": "itemColor",
        "meta_id": "itemMetaId"
      }
    ],
    "schoolClasses": [
      {
        "id": "itemId",
        "label": "itemLabel",
        "created_at": "itemCreatedAt",
        "updated_at": "itemUpdatedAt" 
      }
    ],
    "active_ratings": [
      {
        "id": "itemId",
        "label": "itemLabel",
        "max_score": "itemMaxScore",
        "greetings": "itemGreetings",
        "related_dir": "",
        "active": "itemActive",
        "priority": "itemPriority",
        "created_at": "itemCreatedAt",
        "updated_at": "itemUpdatedAt", 
        "rating_heading": "itemTitle",
        "rating_active": "itemRatingActive",
        "rating_default_colors": "itemDefaultColorActive",
        "payments_active": "itemPaymentsActive"
      }
    ]
  }
}
```

This endpoint retrieves ratings page

### HTTP Request

`GET http://kings.ge/Api/ratings`

###Headers
Header | Description
--------- | ------- |
Accept | Content-Types that are acceptable for the response

### Query Parameters

Parameters | Description
--------- | ------- | 
{result_context_id,school_class_id} | For get lists need parameters e.g : http://kings.ge/Api/ratings/?result_context_id=12&school_class_id=5

<!-- Profile logic -->

# Profile pages

<!-- Get user profile -->
## Get user profile
<p>
  This service retrieves user profile
</p>
<p>
  
</p>


### HTTP Request

`Get http://kings.ge/Api/getProfile`

###Headers
Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

<!-- Change personal info -->
## Change personal info
<p>
  This service is update user personal info
</p>
<p>
  Fields(not required) - user_email,pname(parent name),plname(parent lastname),pphone(parent phone)
</p>


### HTTP Request

`Post http://kings.ge/Api/changePersonaInfo`

###Headers
Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

<!-- Update password -->
## Update password
<p>
  This service is change password
</p>
<p>
  Fields - old_password,password(new password),password_confirmation(new password confirm)
</p>


### HTTP Request

`Post http://kings.ge/Api/changePassword`

###Headers
Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

<!-- Change mobile -->
## Change mobile


> The above command returns JSON structured like this:

```json
{
  "change_mobile" : "ok",
  "new_phone" : "5555555555",
  "isMobileVerified": 0
}
```

<p>
  This service is change mobile
</p>
<p>
  Fields - new mobile phone
</p>
<p>
    If register is success service returns response in JSON format It means that new mobile phone is setted successfully and new verification code is sent to newly setted phone number
</p>


### HTTP Request

`Post http://kings.ge/Api/changeMobile`

###Headers
Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

<!-- Get notifications -->
## Get notifications
<p>
  This service retrieves notifications
</p>
<p>
  
</p>


### HTTP Request

`Get http://kings.ge/Api/notifications/get`

###Headers

Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

### Query Parameters

Parameters | Description
--------- | ------- |
page| for pagination  e.x http://kings.ge/Api/notifications/get?page=2
limit| for several notifications e.x http://kings.ge/Api/notifications/get?limit=5 

<!-- Search notifications -->
## Search notifications
<p>
  This service retrieves notifications by keyword
</p>
<p>
  
</p>


### HTTP Request

`Get http://kings.ge/Api/notifications/search`

###Headers

Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

### Query Parameters

Parameters | Description
--------- | ------- |
keyword|  e.x http://kings.ge/Api/notifications/search?keyword="გილოცავთ"

<!-- Hide notification -->
## Hide notification
<p>
  This service hide notification
</p>
<p>
  
</p>


### HTTP Request

`Post http://kings.ge/Api/notifications/hide`

###Headers

Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

### Query Parameters

Parameters | Description
--------- | ------- |
id| notification id, e.x http://kings.ge/Api/notifications/hide"

<!-- Delete notifications -->
## Delete notifications
<p>
  This service delete notifications
</p>
<p>
  
</p>


### HTTP Request

`Post http://kings.ge/Api/notifications/delete`

###Headers

Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

### Query Parameters

Parameters | Description
--------- | ------- |
ids| notification ids(array of notification ids e.x [300,301,....]) , e.x  http://kings.ge/Api/notifications/delete"

<!-- Read notification -->
## Read notification
<p>
  This service mark notification as read
</p>
<p>
  
</p>

### HTTP Request

`Post http://kings.ge/Api/notifications/read`

###Headers

Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

### Query Parameters

Parameters | Description
--------- | ------- |
notificationId| e.x  http://kings.ge/Api/notifications/hide"

<!-- Count notification -->
## Count notifications
<p>
  This service count newest notifications
</p>
<p>
  
</p>

### HTTP Request

`Post http://kings.ge/Api/notifications/count`

###Headers

Header | Description
--------- | ------- |
Token | This request needs token(after auth returned)

### Query Parameters

Parameters | Description
--------- | ------- |
notificationId| e.x  http://kings.ge/Api/notifications/count"

