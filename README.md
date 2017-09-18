# apiguard-jwt
Open APIs Guard JWT Plugin

### API Doc
```markdown

/* Create API */
curl -X POST \
  http://localhost:8080/apiguard/apis \
  -H 'content-type: application/json' \
  -d '{
  "id": "f8157910-d857-11e6-8bc0-2d9f23b1a052",
  "creationDate": 1484178301729,
  "request_uri": "/google/(.*)/abc",
  "name": "google",
  "downstream_uri": "http://www.google.com"
  }'
  
/* Update API (downstream_uri) */
curl -X PATCH \
  http://localhost:8080/apiguard/apis \
  -H 'content-type: application/json' \
  -d '{
  "id": "f8157910-d857-11e6-8bc0-2d9f23b1a052",
  "creationDate": 1484178301729,
  "request_uri": "/google/(.*)/abc",
  "name": "google",
  "downstream_uri": "http://www.msn.com"
}'

/* Create client */
curl -X POST \
  http://localhost:8080/apiguard/clients \
  -H 'content-type: application/json' \
  -d '{"id":"Jason"}'

/* Add jwt auth (return secret) */
curl -v -X POST http://localhost:8080/apiguard/clients/tesla/jwt-auth -H 'content-type: application/json' -d '{"request_uri":"/google/(.*)/[0-9]+"}'

/* Invoke with jwt - issuer:7ceb15c7-7e69-4094-95e6-973e13b4af56 "secret": "0ce5f35e-a9b9-4717-93bd-4d3daa6b60d3"
 * https://www.jsonwebtoken.io/ - paste secret, header then body to create jwt
 */
curl http://localhost:8080/apiguard/apis/google/ho1/1 -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiI3Y2ViMTVjNy03ZTY5LTQwOTQtOTVlNi05NzNlMTNiNGFmNTYiLCJleHAiOjE0OTkxMjMzMTcsIm5iZiI6MTQ0MjQyNjQ1NCwiaWF0IjoxNDQyNDI2NDU0LCJqdGkiOiI1NWRjN2Y4ZC1mZmMzLTRmODEtOTE3Mi0zMDZjYTVlMzlkYmQifQ.c6Gp4btTpu68yC5_GrAYAMdaeUWGf_xtVP0c9vtXxvY'

```

