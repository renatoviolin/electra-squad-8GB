# electra-squad-8
Fine tunning Electra large model using RTX2080 8 GB on Squad 2 

This repo is a clone of original implementation of Electra (https://github.com/google-research/electra).

I did a fine tunning on Squad 2.0 of the large model pre-trained using a limited resource RTX 2080 8GB.

To achieve this I did:
- reduce batch size to 4 (original is 32)
- use mixed precision to slight reduce the memory consuption
- freeze 2/3 of the network and train the last 8 layers (layer 16 to 23).

With one epoch (~ 8 hours of computing), the eval results were:

```
- HasAns_exact: 82.22 
- HasAns_f1: 87.31 
- HasAns_total: 5928.00 
- NoAns_exact: 91.34 
- NoAns_f1: 91.34 
- NoAns_total: 5945.00 
- best_exact: 86.85 
- best_exact_thresh: -2.53 
- best_f1: 89.41
- best_f1_thresh: -2.53 
- exact: 86.79 
- f1: 89.33 
- total: 11873.00
```

The train scripts/train.sh.
The other modifications is in configure_finetunning.py and model/optimization.py.
