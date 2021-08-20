# User-Management

## Display All Users

### Handler

* **Handler:** GET /api/users
* **Description:** Returns all users from database
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/users?token=oa2vqer0si0rhehvwgvg3ncgec06hlb5ts58hmle
```

**Response**:

```javascript
{
    "users": [
        {
            "ID": 1,
            "admin": true,
            "enabled": true,
            "last_logon_time": "2020-03-21 18:57:36",
            "username": "empireadmin"
        }
    ]
}
```

## Current User

### Handler

* **Handler:** POST /api/users/me
* **Description:** Returns the current user
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/users/me?token=oa2vqer0si0rhehvwgvg3ncgec06hlb5ts58hmle  -X POST
```

**Response**:

```javascript
{
    "admin": true,
    "api_token": "oa2vqer0si0rhehvwgvg3ncgec06hlb5ts58hmle",
    "enabled": true,
    "id": 1,
    "last_logon_time": "2020-03-21 18:57:36",
    "username": "empireadmin"
}
```

## Create New User

### Handler

* **Handler:** POST /api/users
* **Description:** Creates a new users.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/users?token=oa2vqer0si0rhehvwgvg3ncgec06hlb5ts58hmle -X POST -d '{"username":"user", "password":"pass"}'
```

**Response**:

```javascript
{
    "admin": true,
    "api_token": "oa2vqer0si0rhehvwgvg3ncgec06hlb5ts58hmle",
    "enabled": true,
    "id": 1,
    "last_logon_time": "2020-03-21 18:57:36",
    "username": "empireadmin"
}
```

## Disable User

### Handler

* **Handler:** PUT /api/users/UID/disable
* **Description:** Disables a users account from their UID.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/users/1/disable?token=oa2vqer0si0rhehvwgvg3ncgec06hlb5ts58hmle -X PUT
```

**Response**:

```javascript
{
    "success": true,
}
```

