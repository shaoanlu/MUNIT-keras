# MUNIT-keras
A keras (tensorflow) reimplementation of MUNIT: Multimodal Unsupervised Image-to-Image Translation

### [Multimodal Unsupervised Image-to-Image Translation](https://arxiv.org/abs/1804.04732)
Xun Huang, Ming-Yu Liu, Serge Belongie, Jan Kautz

### Deviation from the original implementation
  1. ~~Use [group normalization](https://arxiv.org/abs/1803.08494) instead of layer normalization in up scaling blocks.~~ Model using group norm failed on reconstructing edge images of edges2shoe dataset.
  2. Use [mixup](https://arxiv.org/abs/1710.09412) technique for training.
  3. Input/Output sizes are 128x128.
  
### Result
  - Edges2shoes result to be updated.
  
### Environment
  - [Google Colab](https://colab.research.google.com/)
  
### Acknowledgement
Code heavily inspired by [original MUNIT pytorch implementation](https://github.com/NVlabs/MUNIT). Also borrow adaptive instance normalization code from [eridgd](https://github.com/eridgd/AdaIN-TF/blob/master/ops.py).
