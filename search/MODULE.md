# Search module
**Dependencies:** [Router module](../router/MODULE.md)

## Search files
Search files in the P2P network

**Request:** `GET` `/search/files.json`

_Query params_:
- `searchString={search}`: Filter the results in base a URL encoded UTF-8 string. Can search whole strings or partial strings using operators:
   - `+`: Search for two or more terms. Only responses that contain all the terms will be returned.
   - `-`: Exclude a term. Only responses that do not contain the term on the right side of the operator will be returned.
   - `( )`: Group terms.
- `limit={limit}`: Limit the number of results. Default is 100.
- `fileType={fileType}`: Filter the results by file type. Can be a file extension or a mime type. For example: `pdf`, `application/pdf`.
- `fileSize={fileSize}`: Filter the results by file size in bytes. Can be a range or a specific size. For example: `100..200`, `gt100`, `lt200`.
- `available={true}`: Filter the results to full seed files.
