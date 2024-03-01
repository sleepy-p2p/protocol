# Router module

## Test connection
Test if client is present and handle connections

**Request:** `OPTION` `/router/introduction.json`: 

## Introduce to other client
The client present itself to another client by sending its [introduction](../introduction/MODULE.md) information.

**Request:** `POST` `/router/introduction.json`

**Response:** The introduction information for the target client

## Get client list
Get a list of other sleepy clients

**Request:** `GET` `/router/nodes.json`

_Query params_:
 - `closest={nodeId}`: Obtains only the list of closests clients to `{nodeId}`.

## Get file information
Request another client about a file sources

**Request:** `GET` `/router/files/{fileHash}.json`

**Response:** The list of clients with this file

**Response (307):** The other client doesn't have information about this file, but knows another client who might have the information. Redirection

**Response (404):** The other client doesn't have information about this file.

## Send file information
It sends another client information about a specific file.

**Request:** `POST` `/router/files/{fileHash}.json`