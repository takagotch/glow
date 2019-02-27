### glow
---
.py
https://github.com/openai/glow

.cc
https://github.com/pytorch/glow

.go
https://github.com/chrislusf/glow

```
pip install -r requirements.txt

wget https://storage.googleapis.com/glow-demo/celeba-tfr.tar
tar -xvf celeb-tfr.tar

CUDA_VISIBLE_DEVICES=0 python train.py --depth 1
mpiexec -n 8 python train.py
mpiexec -n 8 python train.py --problem cifar10 --image_size 32 --n_level 3 --depth 32 --flow_permutation[0/1/2] --flow_coupling [0/1] --seed [0/1/2] --learntop --lr 0.001
```

```
go get github.com/chrislusf/glow
go get github.com/chrislusf/glow/flow

./word_count

go get github.com/chrislusf/glow
etc/start_local_glow_cluster.sh

./word_count -glow -glow.leader="localhost: 8930"

./word_count -glow -glow.flow.plot > x.dot
dot -Tpng -otestSelfJoin.png x.dot
GOOS=linux GARCH=amd64 CGO_ENABLED=0 go build .
docker build -t glow .
```

```go
package main

import (
  "flag"
  "string"
  
  "github.com/chrislusf/glow/flow"
)

func main() {
  flag.Parse()
  
  flow.New().TextFile(
    "/etc/passwd", 3,
  ).Filter(func(line string) bool {
    return !strings.HasPrefix(line, "#")
  }).Map(func(line string, ch chan string) {
    for _, token := range strings.Split(line, ":") {
      ch <- token
    }
  }).Map(func(key string) int {
    return 1
  }).Reduce(func(x int, y int) int {
    return x + y
  }).Map(func(x int) {
    println("count:", x)
  }).Run()
}
```


