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
<code>
{<br>
  "user_email": "fredrik@holtet.com",<br>
  "user_password": "iLoveCats123"<br>
}
</code>

### HTTP request
`POST /api/login`
### STATUS CODE:
200 OK

## Register:
### INPUT:
<code>
{<br>
  "user_first_name": "Fredrik",<br>
  "user_last_name": "Holte",<br>
  "user_email": "fredrik@holtet.com",<br>
  "user_phone_number": 48726423,<br>
  "user_school": "Høyskolen Kristiania",<br>
  "user_program": "  Dance"<br>
}
</code>

### HTTP request
`POST /api/register`
### STATUS CODE:
201 OK

# Users

## Get All Users

### STATUS CODE:
200 OK

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
`GET /api/user/all`


## Get a Specific User
### STATUS CODE:
200 OK

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


## Delete a Specific User

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
### STATUS CODE:
204 OK

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
<code>
{<br>
  "user_id": 2,<br>
  "user_first_name": "Marco",<br>
  "user_last_name": "Newname",<br>
  "user_phone_number": "93145678",<br>
  "user_email": "marco@gravbrot.com",<br>
  "user_school": 2,<br>
  "user_program": 3,<br>
  "user_profile_image": "https://flickr.com/sfavzxdsaf123f",<br>
  "user_date_created": "24.03.2000"<br>
}
</code>

### HTTP Request
`PUT /api/user/update/<ID>`

### URL Params

Parameter | Description
--------- | -----------
ID | The ID of the user to delete


# Groups


## Get all groups
### STATUS CODE:
200 OK

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
### HTTP Request
`GET /api/group/all`


## Get a specific group
### STATUS CODE:
200 OK

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
`GET /api/group/<ID>`


## Request to join group
### STATUS CODE:
201 OK

### Parameters
Parameter | Description
--------- | -----------
userId | The ID of the user to add a request for
groupId | The id of the group to add the user request to

### HTTP request
`POST /api/group/request/<userId>/<groupId>`


## Admin delete user from group
### STATUS CODE:
204 OK

### Parameters
Parameter | Description
--------- | -----------
userId | The ID of the user to add a request for
groupId | The id of the group to add the user request to

### HTTP request
`DELETE /api/group/remove/<userId>/groupId`


## Get all members in a group
### STATUS CODE:
200 OK

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
`GET /api/group/<groupId>/users`

### Parameters
Parameter | Description
--------- | -----------
groupId | The ID of the group


## Post a post in group
### STATUS CODE:
201 OK

### INPUT:
<code>
{<br>
  "post_title": "I need help",<br>
  "post_body": "This is the body of the post",<br>
  "user_id": 1<br>
}
</code>

### HTTP request
`POST /api/group/<ID>/post`


## Get all posts in a group
### STATUS CODE:
200 OK

### OUTPUT:

```json
[
{
  "posts_id": 1,
  "post_title": "I need help",
  "post_body": "Can someone help me with this problem",
  "post_date_created" : "24.03.1996",
  "user_id": 1,
  "group_id": 2
},
  {
    "posts_id": 2,
    "post_title": "I need help again",
    "post_body": "Can someone help me with this problem again",
    "post_date_created" : "24.03.1996",
    "user_id": 1,
    "group_id": 2
  },
  {
    "posts_id": 1,
    "post_title": "I need help pls help",
    "post_body": "Can someone help me with this problem IU NEED HELP",
    "user_id": 1,
    "group_id": 2
  }
]
```
### HTTP request
`GET /api/group/<ID>/post`

## Post a comment on a post
### STATUS CODE:
201 OK

### INPUT:
<code>
{<br>
  "comment_body": "I can help",<br>
  "post_body": "This is the body of the post",<br>
  "comment_user_id": 1<br>
}
</code>

### HTTP request
`POST /api/post/<ID>/comment`

### Parameters
Parameter | Description
--------- | -----------
id | Id of the post to add the comment to 

## Get all comments by post
### STATUS CODE:
200 OK

### OUTPUT:

```json
[
{
  "comment_id": 1,
  "comment_body": "I can help",
  "comment_date": "24.03.1996",
  "comment_post_id": 1,
  "comment_user_id": 1
},
  {
    "comment_id": 2,
    "comment_body": "I can also help",
    "comment_date": "24.10.1996",
    "comment_post_id": 1,
    "comment_user_id": 2
  }
]
```
### HTTP request
`GET /api/post/<ID>/comment/all`

### Parameters
Parameter | Description
--------- | -----------
ID | The ID of the post


## Get all groups of user
### STATUS CODE:
200 OK

### OUTPUT:

```json
[
{
  "user_group_id": 1,
  "user_id": 2,
  "group_id": 4,
  "is_Favorite": true,
  "date_joined": "24.10.2021"
},
  {
    "user_group_id": 1,
    "user_id": 2,
    "group_id": 4,
    "is_Favorite": true,
    "date_joined": "24.10.2021"
  }
]
```
### HTTP request
`GET /api/user/<ID>/group/all`

## Parameters
Parameter | Description
--------- | -----------
ID | The ID of the user

