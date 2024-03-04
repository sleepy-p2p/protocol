# Download module
The download module allows to a sleepy peer or http clients (like browsers) to download files from the current peer.

## Get file information
`GET` `/files/{hash}/info.json`
Obtains information from a single file.

The format of the `info.json` is on openapi.yml file.

## Download file chunk
`GET` `/files/{hash}/filename.ext`
Request a file or a chunk of a file. 

The request is performed as a standard HTTP request to download a file, but with some differences:
- The file hash must be in the URL and must be correct. The _active_ peers serve contents based only on the hash.
- The filename must match the filename specified in the `info.json` file. This is for compatibility with _passive_ peers that serve files based on the path.
- The range header is supported and is mandatory in _active_ peers. The _passive_ peers doesn't need to support it, for maximize compatibility, but it is recommended.
