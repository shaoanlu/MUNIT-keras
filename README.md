# MUNIT-keras
A keras (tensorflow) reimplementation of MUNIT: Multimodal Unsupervised Image-to-Image Translation

### [Multimodal Unsupervised Image-to-Image Translation](https://arxiv.org/abs/1804.04732)
Xun Huang, Ming-Yu Liu, Serge Belongie, Jan Kautz

### Deviation from the original implementation
  1. ~~Use [group normalization](https://arxiv.org/abs/1803.08494) instead of layer normalization in upscaling blocks.~~ 
      - Model using group norm failed on reconstructing edge images of edges2shoe dataset.
  2. Use [mixup](https://arxiv.org/abs/1710.09412) technique for training.
  3. Input/Output size is defaulted 128x128.
  4. Use only 3 res blocks (instead of 4) as default in content encoder/decoder in order to reduce training time. 
      - However, I'm worrying that this decreases the receptive field size so that the output quality becomes worse.
  
### Environment
  - [Google Colab](https://colab.research.google.com/)
  
### Result
  - **Edges2shoes** (config. 1)
    - **Cyclic reconstruction loss weight = 1** for the first 80k iters and 0.3 for the rest.
    - Input/Output size: 64x64.
    - Training iterations: ~130k.
    - Optimization: Use [mixup](https://arxiv.org/abs/1710.09412) technique for the first 80k iters.
    - ![](https://github.com/shaoanlu/MUNIT-keras/raw/master/MUNIT_64x64.jpg)
  
  - **Edges2shoes** (config. 2)
    - **Cyclic reconstruction loss weight = 10**
    - Input/Output size: 64x64.
    - Training iterations: ~70k.
    - Optimization: Use [mixup](https://arxiv.org/abs/1710.09412) technique for the entire training process.
    - ![](https://github.com/shaoanlu/MUNIT-keras/raw/master/MUNIT_64x64_cycrec10.jpg)
    - Model performed better on guided translation (generated more detail and clearer edges) when using high reconstruction loss?
  
### Acknowledgement
Code heavily inspired by [original MUNIT pytorch implementation](https://github.com/NVlabs/MUNIT). Also borrow code from [eridgd](https://github.com/eridgd/AdaIN-TF/blob/master/ops.py) and [tjwei](https://github.com/tjwei/GANotebooks).
