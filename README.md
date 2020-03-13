# bigcache-bench

Benchmarks for BigCache project

### GC pause time
```
go version
go version go1.13 linux/amd64

Number of entries:  20000000
Number of repeats:  50
GC pause for startup:  20.811µs
GC pause for warmup:  3.715446ms
GC pause for freecache:  38.607127ms
GC pause for bigcache:  159.066277ms
GC pause for map:  54.543926ms
```

### Writes and reads

```
# go version
go version go1.13 darwin/amd64
# go test -bench=. -benchmem -benchtime=4s ./... -timeout 30m
goos: darwin
goarch: amd64
pkg: github.com/allegro/bigcache-bench
BenchmarkMapSet-8                     	10609958	       511 ns/op	     207 B/op	       3 allocs/op
BenchmarkConcurrentMapSet-8           	 3598414	      1488 ns/op	     361 B/op	       8 allocs/op
BenchmarkGoCacheSet-8                 	 5081526	      1113 ns/op	     325 B/op	       4 allocs/op
BenchmarkFreeCacheSet-8               	 7337565	       923 ns/op	     353 B/op	       2 allocs/op
BenchmarkBigCacheSet-8                	 6786914	       711 ns/op	     301 B/op	       2 allocs/op
BenchmarkMapGet-8                     	12867964	       451 ns/op	      24 B/op	       1 allocs/op
BenchmarkConcurrentMapGet-8           	 9884720	       521 ns/op	      24 B/op	       2 allocs/op
BenchmarkGoCacheGet-8                 	 9570022	       548 ns/op	      24 B/op	       1 allocs/op
BenchmarkFreeCacheGet-8               	 6197871	       871 ns/op	     136 B/op	       3 allocs/op
BenchmarkBigCacheGet-8                	 7721288	       665 ns/op	     152 B/op	       4 allocs/op
BenchmarkBigCacheSetParallel-8        	21367204	       321 ns/op	     312 B/op	       3 allocs/op
BenchmarkGoCacheParallel-8            	 4172646	      1188 ns/op	     368 B/op	       5 allocs/op
BenchmarkFreeCacheSetParallel-8       	24368949	       400 ns/op	     332 B/op	       3 allocs/op
BenchmarkConcurrentMapSetParallel-8   	11666227	       403 ns/op	     200 B/op	       6 allocs/op
BenchmarkBigCacheGetParallel-8        	32574837	       245 ns/op	     152 B/op	       4 allocs/op
BenchmarkGoCacheGetParallel-8         	46485171	       140 ns/op	      24 B/op	       2 allocs/op
BenchmarkFreeCacheGetParallel-8       	24662016	       378 ns/op	     136 B/op	       3 allocs/op
BenchmarkConcurrentMapGetParallel-8   	14588425	       334 ns/op	      24 B/op	       2 allocs/op
PASS
ok  	github.com/allegro/bigcache-bench	362.185s
```
