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
end

req: "delete exist user"
  head Allow-Original $original
  cookie token $token
  body '{"id":"$builtin_uuid:uid"}'
post:
  http://example.com/api/users
resp:
  head Content-Type applicatoin/json
  body '{"result_code":1, "id":@uid}'
end
```

# usage looks like
save above file as `create_user.rtt`

`$restest --original=example.com  -v create_user.rtt`

- -n total number of request
- -v verbose
