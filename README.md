# restest
REStful api TEST command line, which read DSL file, test based on config file

# config looks like
```text
set token tk123456789

req: "creating new user"
  head Allow-Original $original
  cookie token $token
  body '{"id":"$builtin_uuid:uid"}'
post:
  http://example.com/api/users
resp:
  head Content-Type applicatoin/json
  body '{"result_code":1, "id":@uid}'
```

# usage looks like
save above file as `create_user.rtt`

`$restest --original=example.com -c 10, -n 1000 -v create_user.rtt`

- -c cocurrent number of request
- -n total number of request
- -v verbose
