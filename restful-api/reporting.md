# Reporting

## Get All Logged Events

### Handler

* **Handler:** GET /api/reporting
* **Description:** Returns all logged events.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/reporting?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "reporting": [
    {
      "ID": 1,
      "agentname": "3GHZPWEGADMT2KPA",
      "event_type": "checkin",
      "message": "2016-03-31 17:36:34",
      "timestamp": "2016-03-31 17:36:34"
    },
    ...
  ]
}
```

## Get Agent Logged Events

### Handler

* **Handler:** GET /api/reporting/agent/AGENT\_NAME
* **Description:** Returns the events for a specified AGENT\_NAME
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/reporting/agent/initial?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "reporting": [
    {
      "ID": 28,
      "agentname": "SMLHRBLTP4Z14SHC",
      "event_type": "checkin",
      "message": "2016-03-31 21:01:34",
      "timestamp": "2016-03-31 21:01:34"
    },
    ...
  ]
}
```

## Get Logged Events of Specific Type

### Handler

* **Handler:** GET /api/reporting/type/MSG\_TYPE
* **Description:** Returns the events of a specified MSG\_TYPE \(checkin, task, result\).
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/reporting/type/checkin?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "reporting": [
    {
      "ID": 1,
      "agentname": "3GHZPWEGADMT2KPA",
      "event_type": "checkin",
      "message": "2016-03-31 17:36:34",
      "timestamp": "2016-03-31 17:36:34"
    },
    {
      "ID": 4,
      "agentname": "PK4HAFLH4231E14X",
      "event_type": "checkin",
      "message": "2016-03-31 17:36:50",
      "timestamp": "2016-03-31 17:36:50"
    },
    ...
  ]
}
```

## Get Logged Events w/ Specific Msg

### Handler

* **Handler:** GET /api/reporting/msg/MSG
* **Description:** Returns the events matching a specific MSG.
* **Parameters:** None

### Example

**Request**:

```bash
curl --insecure -i https://localhost:1337/api/reporting/msg/mimikatz?token=ks23jlvdki4fj1j23w39h0h0xcuwjrqilocxd6b5
```

**Response**:

```javascript
{
  "reporting": [
    {
      "ID": 5,
      "agentname": "PK4HAFLH4231E14X",
      "event_type": "task",
      "message": "TASK_CMD_JOB - function Invoke-Mimikatz\n{\n[CmdletBinding(DefaultP",
      "timestamp": "2016-03-31 17:36:54"
    },
    ...
  ]
}
```

