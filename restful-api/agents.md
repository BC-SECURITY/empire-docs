# Agents

## Get Current Agents

### Handler

* **Handler:** GET /api/agents
* **Description:** Returns all current Empire agents.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/agents?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "agents": [
    {
      "ID": 1,
      "checkin_time": "2016-03-31 17:36:34",
      "children": null,
      "delay": 5,
      "external_ip": "192.168.52.200",
      "functions": null,
      "headers": "",
      "high_integrity": 0,
      "hostname": "WINDOWS1",
      "internal_ip": "192.168.52.200",
      "jitter": 0.0,
      "kill_date": "",
      "lastseen_time": "2016-03-31 17:38:55",
      "listener": "http://192.168.52.172:8080/",
      "lost_limit": 60,
      "name": "3GHZPWEGADMT2KPA",
      "old_uris": null,
      "os_details": "Microsoft Windows 7 Professional ",
      "parent": null,
      "process_id": "1636",
      "process_name": "powershell",
      "ps_version": "2",
      "results": "",
      "servers": null,
      "sessionID": "3GHZPWEGADMT2KPA",
      "session_key": "7.+...",
      "taskings": "",
      "uris": "/admin/get.php,/news.asp,/login/process.jsp",
      "user_agent": "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko",
      "username": "WINDOWS1\\user",
      "working_hours": ""
    },
    ...
  ]
}
```

## Get Stale Agents

### Handler

* **Handler:** GET /api/agents/stale
* **Description:** Returns all 'stale' Empire agents \(past checkin window\).
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/agents/stale?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "agents": [
    {
      "ID": 1,
      "checkin_time": "2016-03-31 17:36:34",
      "children": null,
      "delay": 5,
      "external_ip": "192.168.52.200",
      "functions": null,
      "headers": "",
      "high_integrity": 0,
      "hostname": "WINDOWS1",
      "internal_ip": "192.168.52.200",
      "jitter": 0.0,
      "kill_date": "",
      "lastseen_time": "2016-03-31 17:38:55",
      "listener": "http://192.168.52.172:8080/",
      "lost_limit": 60,
      "name": "3GHZPWEGADMT2KPA",
      "old_uris": null,
      "os_details": "Microsoft Windows 7 Professional ",
      "parent": null,
      "process_id": "1636",
      "process_name": "powershell",
      "ps_version": "2",
      "results": "",
      "servers": null,
      "sessionID": "3GHZPWEGADMT2KPA",
      "session_key": "7.+...",
      "taskings": "",
      "uris": "/admin/get.php,/news.asp,/login/process.jsp",
      "user_agent": "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko",
      "username": "WINDOWS1\\user",
      "working_hours": ""
    },
    ...
  ]
}
```

## Remove Stale Agents

### Handler

* **Handler:** DELETE /api/agents/stale
* **Description:** Removes all 'stale' Empire agents \(past checkin window\).
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/agents/stale?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5 -X DELETE
```

**Response**:

```javascript
{
  "success": true
}
```

## Get Agent by Name

### Handler

* **Handler:** GET /api/agents/AGENT\_NAME
* **Description:** Returns the agent specified by AGENT\_NAME.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/agents/XMY2H2ZPFWNPGEAP?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "agents": [
    {
      "ID": 1,
      "checkin_time": "2016-03-31 20:29:31",
      "children": null,
      "delay": 5,
      "external_ip": "192.168.52.200",
      "functions": null,
      "headers": "",
      "high_integrity": 0,
      "hostname": "WINDOWS1",
      "internal_ip": "192.168.52.200",
      "jitter": 0.0,
      "kill_date": "",
      "lastseen_time": "2016-03-31 20:29:38",
      "listener": "http://192.168.52.173:8080/",
      "lost_limit": 60,
      "name": "XMY2H2ZPFWNPGEAP",
      "old_uris": null,
      "os_details": "Microsoft Windows 7 Professional ",
      "parent": null,
      "process_id": "2600",
      "process_name": "powershell",
      "ps_version": "2",
      "results": null,
      "servers": null,
      "sessionID": "XMY2H2ZPFWNPGEAP",
      "session_key": "+e`x!...",
      "taskings": null,
      "uris": "/admin/get.php,/news.asp,/login/process.jsp",
      "user_agent": "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko",
      "username": "WINDOWS1\\user",
      "working_hours": ""
    }
  ]
}
```

## Remove Agent

### Handler

* **Handler:** DELETE /api/agents/AGENT\_NAME
* **Description:** Removes the agent specified by AGENT\_NAME \(doesn't kill first\).
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/agents/XMY2H2ZPFWNPGEAP?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5 -X DELETE
```

**Response**:

```javascript
{
  "success": true
}
```

## Task an Agent to run a Shell Command

### Handler

* **Handler**: POST /api/agents/AGENT\_NAME/shell
* **Description**: Tasks the agent specified by AGENT\_NAME to run the given shell command.
* **Parameters:**
  * **Command:** the shell command to task the agent to run \(required\)

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/CXPLDTZCKFNT3SLT/shell?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5 -X POST -d '{"command":"whoami"}'
```

**Response**:

```javascript
{
  "success": true
}
```

## Task all Agents to run a Shell Command

### Handler

* **Handler:** POST /api/agents/all/shell
* **Description:** Tasks all agents to run the given shell command.
* **Parameters:**
  * **Command:** the shell command to task the agents to run \(required\)

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/all/shell?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5 -X POST -d '{"command":"pwd"}'
```

**Response**:

```javascript
{
  "success": true
}
```

## Get Agent Results

### Handler

* **Handler:** GET /api/agents/AGENT\_NAME/results
* **Description:** Retrieves results for the agent specifed by AGENT\_NAME.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/CXPLDTZCKFNT3SLT/results?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "results": [
    {
      "agentname": "CXPLDTZCKFNT3SLT",
      "results": "WINDOWS1\\user\nPath                                                                           \r\n----                                                                           \r\nC:\\Users\\user
    }
  ]
}r
```

## Delete Agent Results

### Handler

* **Handler:** DELETE /api/agents/AGENT\_NAME/results
* **Description:** Deletes the result buffer for the agent specifed by AGENT\_NAME.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/CXPLDTZCKFNT3SLT/results?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5 -X DELETE
```

**Response**:

```javascript
{
  "success": true
}
```

## Delete All Agent Results

### Handler

* **Handler:** DELETE /api/agents/all/results
* **Description:** Deletes all agent result buffers
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/all/results?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5 -X DELETE
```

**Response**:

```javascript
{
  "success": true
}
```

## Clear Queued Agent Tasking

### Handler

* **Handler:** POST/GET /api/agents/AGENT\_NAME/clear
* **Description:** Clears the queued taskings for the agent specified by AGENT\_NAME.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/CXPLDTZCKFNT3SLT/clear?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "success": true
}
```

## Rename an Agent

### Handler

* **Handler:** POST/GET /api/agents/AGENT\_NAME/rename
* **Description:** Renames the agent specified by AGENT\_NAME.
* **Parameters:**
  * **Newname:** the name to rename the specified agent to \(required\)

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/CXPLDTZCKFNT3SLT/rename?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5 -X POST -d '{"newname":"initial"}'
```

**Response**:

```javascript
{
  "success": true
}
```

## Kill an Agent

### Handler

* **Handler:** POST/GET /api/agents/AGENT\_NAME/kill
* **Description:** Tasks the agent specified by AGENT\_NAME to exit.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/CXPLDTZCKFNT3SLT/kill?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "success": true
}
```

## Kill all Agents

### Handler

* **Handler:** POST/GET /api/agents/all/kill
* **Description:** Tasks all agents to exit.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i -H "Content-Type: application/json" https://localhost:1337/api/agents/all/kill?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "success": true
}
```

