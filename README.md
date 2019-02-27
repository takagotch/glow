### glow
---
.py
https://github.com/openai/glow

.cc
https://github.com/pytorch/glow



```
pip install -r requirements.txt

wget https://storage.googleapis.com/glow-demo/celeba-tfr.tar
tar -xvf celeb-tfr.tar

CUDA_VISIBLE_DEVICES=0 python train.py --depth 1
mpiexec -n 8 python train.py
mpiexec -n 8 python train.py --problem cifar10 --image_size 32 --n_level 3 --depth 32 --flow_permutation[0/1/2] --flow_coupling [0/1] --seed [0/1/2] --learntop --lr 0.001
```

```
```

```
```


