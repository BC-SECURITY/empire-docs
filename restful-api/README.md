# RESTful API

## Introduction

As of Empire 4.0, the RESTful API is the only method for interacting with server and allows for scripting and controlling Empire through HTTP JSON requests. This new method allows for multiple users to interact with the server without a new streamlined client. This API and documentation are based on the [BeEF Project](https://github.com/beefproject/beef/wiki/BeEF-RESTful-API). All credit to [@antisnatchor](https://github.com/antisnatchor) and the entire BeEF community for the great examples to draw on.

The server can be launched by running `./ps-empire server` and can be connected to with the built-in client or [Starkiller](https://github.com/BC-SECURITY/Starkiller). By default, the RESTful API is started on port 1337, over HTTPS using the certificate located at .empire/server/data/empire.pem, which can be generated with ./setup/cert.sh or the default install script. The port can be changed by supplying `--restport <PORT_NUM>` on launch.

![](../.gitbook/assets/image%20%281%29.png)

The default username for the API is 'empireadmin' and the default password is 'password123'. You can also manually specify the username and password for the server with `--username admin --password 'Password123!'`.

## API Authentication

The Empire API uses a simple token-based auth system similar to [BeEF's](https://github.com/beefproject/beef/wiki/BeEF-RESTful-API#authentication). In order to make any requests to the API, a **?token=X** parameter must be supplied, otherwise a 403 error is returned.

The token is randomly generated on rest API start up and displayed on the command line:

```bash
# ./ps-empire server

[*] Loading default config
[*] Loading stagers from: /home/kali/Empire-Sponsors/empire/server/stagers/
[*] Loading modules from: /home/kali/Empire-Sponsors/empire/server/modules/
[*] Loading listeners from: /home/kali/Empire-Sponsors/empire/server/listeners/
[*] Starting listener 'http'
[+] Listener successfully started!
[*] Loading malleable profiles from: /home/kali/Empire-Sponsors/empire/server/data/profiles
[*] Loading listeners from: /home/kali/Empire-Sponsors/empire/server/plugins
[*] Plugin csharpserver found.
[*] Initializing plugin...
[*] Doing custom initialization...
[*] Loading Empire CSharp server plugin
[*] Registering plugin with menu...
[*] Empire starting up...
[*] Starting Empire RESTful API on 0.0.0.0:1337
[*] Starting Empire SocketIO on 0.0.0.0:5000
[*] Testing APIs
[+] empireadmin connected to socketio
[+] Empire RESTful API successfully started
[+] test-aese connected to socketio
[+] Empire SocketIO successfully started
[*] Cleaning up test user
[+] Client disconnected from socketio
```

To retrieve the session token through the login interface, you can POST a request to `/api/admin/login`. Here's an example with curl:

```bash
# curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/admin/login -X POST -d '{"username":"empireadmin", "password":"Password123!"}'
HTTP/1.0 200 OK
Content-Type: application/json
Content-Length: 57
Server: Werkzeug/0.11.4
Date: Thu, 31 Mar 2016 23:38:59 GMT

{
  "token": "ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5"
}
```

## Version Information

### Handler

* **Handler** : GET /api/version
* Description : Returns the current Empire version.
* No parameters

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/version?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "version": "1.5.0"
}
```

## Map Information

### Handler

* **Handler** : GET /api/map
* Description : Returns list of all API routes.
* No parameters

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/map?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

## Configuration Information

### Handler

* **Handler** : GET /api/config
* Description : Returns the current Empire configuration.
* No parameters

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/config?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "config": [
    {
      "api_password": "C3>Jl...",
      "api_username": "empireadmin",
      "autorun_command": "",
      "autorun_data": "",
      "current_api_token": "ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5",
      "default_cert_path": "",
      "default_delay": 5,
      "default_jitter": 0.0,
      "default_lost_limit": 60,
      "default_port": "8080",
      "default_profile": "/admin/get.php,/news.asp,/login/process.jsp|Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko",
      "install_path": "/home/user/Empire/",
      "ip_blacklist": "",
      "ip_whitelist": "",
      "permanent_api_token": "gi5afo3umac6...",
      "server_version": "Microsoft-IIS/7.5",
      "stage0_uri": "index.asp",
      "stage1_uri": "index.jsp",
      "stage2_uri": "index.php",
      "staging_key": "m@T%L?VH...",
      "version": "1.5.0"
    }
  ]
}
```

