---
title: Golf

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/khiet/golf'>Source Code (Github)</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction

Welcome to the Golf API!

# Authentication

> JSON request:

```shell
curl "https://example.com/user_token"
  -H "Content-Type: application/json"
  -X "POST"
  -d $'{"auth": {"email": "foo@example.com", "password": "password123"}}'
```

> JSON response:

```json
{
  jwt: "eyJ0eXA.."
}
```

Authentication (and authorization) is handled by JWT which is set to be valid for one year.
API expects JWT to be included all requests (except a request for a user signup) to the server in a header that looks like the following:

`Authentication: Bearer eyJ0eXA..`

<aside class="notice">
<code>eyJ0eXA..</code> is an HS256 signed token.
</aside>

# Users

## Get All Users

> JSON request:

```shell
curl "https://example.com/users"
  -H "Authorization: Bearer eyJ0eXA.."
```

> JSON response:

```json
[
  {
    "id": 1,
    "email": "foo@example.com",
    "role": null
  },
  {
    "id": 2,
    "email": "bar@example.com",
    "role": "organizer"
  }
]
```

This endpoint retrieves all users.

### HTTP Request

`GET https://example.com/api/users`

### Error Code

Error Code | Meaning
---------  | -----------
200        | success
401        | unauthorized - missing or invalid JWT in the header
