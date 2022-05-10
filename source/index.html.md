---
title: AtCampus API

language_tabs: # must be one of https://git.io/vQNgJ  
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Atcampus API
---

# Introduction

Welcome to the API for AtCampus. Here you can access all of the information about users, groups, posts, comments, schools, and programs. 

We have language bindings in JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Login / Register

## Login
### INPUT:
```json
{
  "user_email": "fredrik@holtet.com",
  "user_password": "iLoveCats123"
}
```
### HTTP request
`POST /api/login`


## Register:
### INPUT:
```json
{
  "user_first_name": "Fredrik",
  "user_last_name": "Holte",
  "user_email": "fredrik@holtet.com",
  "user_phone_number": 48726423,
  "user_school": "Høyskolen Kristiania",
  "user_program": "  Dance"
}
```
### HTTP request
`POST /api/register`

# Users

## Get All Users

### OUTPUT:
```json
[
  {
    "user_id": 1,
    "user_first_name": "Syvert",
    "user_last_name": "Eidjord",
    "user_phone_number": "94886155",
    "user_email": "syvert@eidjord.com",
    "user_school": 1,
    "user_program": 2,
    "user_profile_image": "https://flickr.com/sfavzxdsrgsfar4123f",
    "user_date_created": "24.03.1996"
    
  },
  {
    "user_id": 2,
    "user_first_name": "Marco",
    "user_last_name": "Gravbrot",
    "user_phone_number": "93145678",
    "user_email": "marco@gravbrot.com",
    "user_school": 2,
    "user_program": 3,
    "user_profile_image": "https://flickr.com/sfavzxdsaf123f",
    "user_date_created": "24.03.2000"
  }
  
]
```

This endpoint retrieves all users.

### HTTP Request
`GET /api/user`

## Get a Specific User
### OUTPUT:
```json
{
  "user_id": 2,
  "user_first_name": "Marco",
  "user_last_name": "Gravbrot",
  "user_phone_number": "93145678",
  "user_email": "marco@gravbrot.com",
  "user_school": 2,
  "user_program": 3,
  "user_profile_image": "https://flickr.com/sfavzxdsaf123f",
  "user_date_created": "24.03.2000"
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET /api/user/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve

## Delete a Specific Kitten

```json
{
  "user_id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific user.

### HTTP Request

`DELETE api/user/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to delete


## Update a user
### OUTPUT:
```json
{
  "user_id": 2,
  "user_first_name": "Marco",
  "user_last_name": "Newname",
  "user_phone_number": "93145678",
  "user_email": "marco@gravbrot.com",
  "user_school": 2,
  "user_program": 3,
  "user_profile_image": "https://flickr.com/sfavzxdsaf123f",
  "user_date_created": "24.03.2000"
}
```
This endpoint updates a specific user

### INPUT
```json
{
  "user_id": 2,
  "user_first_name": "Marco",
  "user_last_name": "Newname",
  "user_phone_number": "93145678",
  "user_email": "marco@gravbrot.com",
  "user_school": 2,
  "user_program": 3,
  "user_profile_image": "https://flickr.com/sfavzxdsaf123f",
  "user_date_created": "24.03.2000"
}
```

### HTTP Request

`PUT /api/user/`

### URL Params

Parameter | Description
--------- | -----------
ID | The ID of the user to delete


# Groups

## Get all groups
### HTTP Request

`GET /api/groups/all`
### OUTPUT:
```json
[
  {
    "group_id": 1,
    "group_name": "Group 1",
    "group_description": "Awesome group",
    "group_image": "https://flickr.com/sfavzxdsrgsfar4123f",
    "group_school": "Høyskolen Kristiania",
    "group_admin": 1,
    "date_created": "24.03.1996"
  },
  {
    "group_id": 2,
    "group_name": "Group 2",
    "group_description": "Studygroup for programming",
    "group_image": "https://flickr.com/sfavzxdsrgsfar4123f",
    "group_school": "Høyskolen Kristiania",
    "group_admin": 3,
    "date_created": "24.03.1996"
  }
  
]
```

## Get a specific group
### OUTPUT:
```json
{
  "group_id": 1,
  "group_name": "Group 1",
  "group_description": "Awesome group",
  "group_image": "https://flickr.com/sfavzxdsrgsfar4123f",
  "group_school": "Høyskolen Kristiania",
  "group_admin": 1,
  "date_created": "24.03.1996"
}
```

### HTTP request

`GET /api/groups/<ID>`

## Request to join group
### INPUT:
```json
{
  "group_id": 1,
  "group_description": "Awesome group"
}
```

### HTTP request
`POST /api/groups/<request>`

## Admin delete user from group
### INPUT:
```json
{
  "group_id": 1,
  "user_id": 2
}
```

### HTTP request
`DELETE /api/groups/remove`

## Get all members in a group
### OUTPUT:
```json
[
{
  "user_first_name": "Fredrik",
  "user_last_name": "Holtet",
  "user_profile_image": "https://flickr.com/sfavzxdsrgsfar4123f"
},
  {
    "user_first_name": "Jonas",
    "user_last_name": "Hansen",
    "user_profile_image": "https://flickr.com/sfavzxdsrgsfar4123f"
  }
]
```

### HTTP request
`GET /api/groups`

## Post a post in group
###INPUT:
```json
{
  "group_id": 1,
  "title": "I need help",
  "description": "Can someone help me with this problem"
}
```

### HTTP request
`POST /api/groups/posts`


