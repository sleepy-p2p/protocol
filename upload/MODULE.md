# Upload module
**Only for _active_ peers**

The upload module allows to a sleepy peer send files and chunks to another _active_ peers, even if the current peer is behind a NAT. 
Is a mechanism to maximize the availability of the files in the network.

## Offer resource
`POST` `/files/{hash}/pending.json`
Offer a file to a peer. The server peer will respond with a list of chunks desired and another related information.

## Upload file chunk
`POST` `/files/{hash}`
Send a file chunk to another peer. The server peer can reject the offer if not interested.
