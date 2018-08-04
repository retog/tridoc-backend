# 3DOC

## Setup with Docker-compose 

```
docker-compose build
docker-compose up
``` 

## Alternative methods for setup

The following methods expect an instance of Fuseki running on http://fuseki:3030/ with user `admin`  and password `pw123`. 

### Yarn
This method also expects that there is a database called `3doc` on the fuseki instance.

If you haven't already, install yarn first. Then run the following:
```
yarn install
yarn start
```

### Docker 

```
docker build -t 3doc .
docker run -p 8000:8000 3doc
```

# API

| Address | Method | Description | Status |
| - | - | - | - |
| /doc | POST | Add Document | Implemented |
| /doc | GET | Returns an array of objects with document identifiers and titles (if available) | Implemented |
| /doc/{id} | GET | Get this document | Implemented |
| /doc/{id} | DELETE | Deletes all metadata associated with the document. Document will not be deleted and is stays accessible over /doc/{id}. | Implemented |
| /doc/{id}/comment | POST | Add comment to document |
| /doc/{id}/comment	| GET | Get comments |
| /doc/{id}/tag | POST | Add a tag to document |
| /doc/{id}/tag | GET | Get tags of document |
| /doc/{id}/tag/{tagName} | DELETE | Remove tag from document |
| /doc/{id}/title | PUT | Set document title. The entity body must be a JSON object like `{"title": "the_Title"}` | Implemented |
| /doc/{id}/title | GET | Get document title. Returns a JSON object like `{"title": "the_Title"}` | Implemented |
| /doc/{id}/title | DELETE | Reset document title | Implemented |
| /doc/{id}/meta | GET | Get title and tags |
| /tag | POST | Create new tag |
| /tag | GET | Get (list of) all tags |
| /tag/{tagName} | GET | Get tag description |
| /tag/{tagName} | DELETE | Delete this tag |

Deleting / editing comments might be supportet in the future