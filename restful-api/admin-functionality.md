# Admin-Functionality

## User Login

### Handler

* **Handler:** POST /api/admin/login
* **Description:** Retrieves the API token given the correct username and password.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/admin/login -X POST -d '{"username":"empireadmin", "password":"Password123!"}'
```

**Response**:

```javascript
{
  "token": "ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5"
}
```

## User Logout

### Handler

* **Handler:** POST /api/admin/logout
* **Description:** Logs out of current user account.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/admin/logout -X POST
```

**Response**:

```javascript
{
  "success": "True"
}
```

## Restart the RESTful API Server

### Handler

* **Handler:** GET /api/restart
* **Description:** Restarts the RESTful API server.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/admin/restart?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "success": true
}
```

## Shutdown the RESTful API Server

### Handler

* **Handler:** GET /api/shutdown
* **Description:** Shutdown the RESTful API server.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/admin/shutdown?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "success": true
}
```

