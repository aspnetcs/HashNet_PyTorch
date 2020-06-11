# HashNet: Deep Learning to Hash by Continuation

# Paper
https://arxiv.org/pdf/1702.00758.pdf

# Reference
Cao Z , Long M , Wang J , et al. HashNet: Deep Learning to Hash by Continuation[J]. 2017.

## REQUIREMENTS
`pip install -r requirements.txt`

1. pytorch >= 1.0
2. loguru

## DATASETS
1. [CIFAR-10](https://pan.baidu.com/s/1YJVe-tTfWTSKHMSYnxfjVg) Password: aemd
2. [NUS-WIDE](https://pan.baidu.com/s/1qVKFQz4_PbQX0CrSWwUwYw) Password: msfv
3. [Imagenet100](https://pan.baidu.com/s/17koNbdMLIYHgPFEFzjblvQ) Password: xpab

## USAGE
```
usage: run.py [-h] [--dataset DATASET] [--root ROOT]
              [--code-length CODE_LENGTH] [--arch ARCH]
              [--batch-size BATCH_SIZE] [--lr LR] [--max-iter MAX_ITER]
              [--num-workers NUM_WORKERS] [--topk TOPK] [--gpu GPU]
              [--alpha ALPHA] [--seed SEED]
              [--evaluate-interval EVALUATE_INTERVAL]

HashNet_PyTorch

optional arguments:
  -h, --help            show this help message and exit
  --dataset DATASET     Dataset name.
  --root ROOT           Path of dataset
  --code-length CODE_LENGTH
                        Binary hash code length.
  --arch ARCH           CNN model name.(default: alexnet)
  --batch-size BATCH_SIZE
                        Batch size.(default: 256)
  --lr LR               Learning rate.(default: 1e-5)
  --max-iter MAX_ITER   Number of iterations.(default: 300)
  --num-workers NUM_WORKERS
                        Number of loading data threads.(default: 6)
  --topk TOPK           Calculate map of top k.(default: all)
  --gpu GPU             Using gpu.(default: False)
  --alpha ALPHA         Hyper-parameter.(default: 1)
  --seed SEED           Random seed.(default: 3367)
  --evaluate-interval EVALUATE_INTERVAL
                        Evaluation interval.(default: 10)
```

## Examples

python run.py --dataset cifar-10 --root .\data\cifar-10\ --code-length 12

## EXPERIMENTS
CNN model: Alexnet.

cifar10: 1000 query images, 5000 training images, MAP@ALL.

nus-wide: Top 21 classes, 2100 query images, 10500 training images, MAP@5000.

imagenet100: Top 100 classes, 5000 query images, 10000 training images, MAP@1000.

 bits | 16 | 32 | 48 | 128
   :-:   |  :-:    |   :-:   |   :-:   |   :-:   
cifar10@ALL | 0.7290 | 0.7528 | 0.7512 | 0.7579 
nus-wide-tc21@5000 | 0.7981 | 0.8200 | 0.8300 | 0.8424 
imagenet100@1000 | 0.3651 | 0.4629 | 0.5094 | 0.5787

