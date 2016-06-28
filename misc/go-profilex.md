import _ "net/http/pprof"

wrk -d 1m http://127.0.0.1:9061/xxxxy
go tool pprof --seconds=5 localhost:9061/debug/pprof/profile
top/web

https://github.com/uber/go-torch
go-torch -t 5  -u http://localhost:9061

