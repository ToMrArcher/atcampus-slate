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

# Users

## Get All Users

```json
[
  {
    "id": 1,
    "firstName": "Syvert",
    "lastName": "Eidjord",
    "phoneNumber": "94886155",
    "email": "syvert@eidjord.com",
    "school": 1,
    "program": 2,
    "profileImage": "https://flickr.com/sfavzxdsrgsfar4123f",
    "dateCreated": "24.03.1996"
    
  },
  {
    "id": 2,
    "firstName": "Marco",
    "lastName": "Gravbrot",
    "phoneNumber": "93145678",
    "email": "marco@gravbrot.com",
    "school": 2,
    "program": 3,
    "profileImage": "https://flickr.com/sfavzxdsaf123f",
    "dateCreated": "24.03.2000"
  }
  
]
```

This endpoint retrieves all users.

### HTTP Request
`GET /api/user`

## Get a Specific User

```json
{
  "id": 2,
  "firstName": "Marco",
  "lastName": "Gravbrot",
  "phoneNumber": "93145678",
  "email": "marco@gravbrot.com",
  "school": 2,
  "program": 3,
  "profileImage": "https://flickr.com/sfavzxdsaf123f",
  "dateCreated": "24.03.2000"
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
  "id": 2,
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

```json
{
  "id": 2,
  "firstName": "Marco",
  "lastName": "Newname",
  "phoneNumber": "123456789",
  "email": "marco@newname.com",
  "school": 1,
  "program": 2,
  "profileImage": "https://flickr.com/sfa2zxdsaf123f",
  "dateCreated": "24.03.2000"
}
```
This endpoint updates a specific user

### HTTP Request

`POST /api/user/<ID>`

### URL Params

Parameter | Description
--------- | -----------
ID | The ID of the user to delete

### Body

<code>
{
  "id": 2, <br>
  "firstName": "Marco", <br>
  "lastName": "Newname", <br>
  "phoneNumber": "123456789", <br>
  "email": "marco@newname.com",<br>
  "school": 1,<br>
  "program": 2,<br>
  "profileImage": "https://flickr.com/sfa2zxdsaf123f",<br>
  "dateCreated": "24.03.2000" <br>
}
</code>

# Groups

## Get all groups
### HTTP Request

`GET /api/groups/all`

## Get a specific group

### HTTP request

`GET /api/groups/<ID>>`

