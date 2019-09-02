# CURL

### REST Calls

##### GET

```
curl <url>
```

`-o <path/to/file>` is a helpful flag to output the response to a file. (Especially when response is large)
`-v` shows the verbose version of response.

##### POST

```
curl -X POST -d 'id=zzy96' <url>
```

The default `Content-Type` is `application/x-www-form-urlencoded`. Explicitly set the header with `-H` if want to POST JSON content.

```
curl -X POST -d '{"json": "message"}' -H 'Content-Type: application/json' <url>
```

`-X` sets the request method.

### Authentication


With user id & password
```
curl --user zzy96:secretPassword <url>
```

With token
```
curl -H "Authorization: Bearer <Bearer Token>" <url>
```

### JSON RPC Example

```
curl -X POST http://127.0.0.1:22000 --data '{"jsonrpc":"2.0","method":"eth_sendRawPrivateTransaction","params":["0xf8a6068084d4143e008080b8584b4a664a36426a65576e50753071554f4e6d684333376443463949637533422f35422f736761634b5a73497a48672b6f6c334f465069795a735a6b5773367a384955657a63686441486e584b73707a525133363032413d3d26a07bba3b21966d0231ba3bbc9cf7709032310e9bc695e92377bf7a941826d91640a067bd5804db9a5cc56e173390a2e03bd61456aeebe3c490d7746c575530996cc7",{"privateFor":["1iTZde/ndBHvzhcl7V68x44Vx7pl8nwx9LqnM/AfJUg=","QfeDAys9MPDs2XHExtc84jKGHxZg/aj52DTh0vtA3Xc="]}],"id":"100"}' --header "Content-Type: application/json"
```
