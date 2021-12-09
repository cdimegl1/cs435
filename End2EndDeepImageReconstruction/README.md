# End-to-End Deep Image Reconstruction

Data, pre-trained models and code for [Shen, Dwivedi, Majima, Horikawa, and Kamitani (2019) End-to-end deep image reconstruction from human brain activity. Front. Comput. Neurosci](https://www.frontiersin.org/articles/10.3389/fncom.2019.00021/full). ([bioRxiv preprint](https://www.biorxiv.org/content/10.1101/272518v1)).

## Requirements

- Python 2.7
- Numpy 
- Scipy
- Pillow (PIL)
- Caffe with up-convolutional layer
    - https://github.com/dosovits/caffe-fr-chairs (Branch: deepsim)

## Usage

### Reconstruct image using pre-trained model

We have released pre-trained models (generator networks of the end-to-end deep image reconstruction models) of the 3 human subjects in our study (see [net_pretrained/README.md](net_pretrained/README.md)).

You can use these pre-trained models to reconstruct images from fMRI data (see [data/README.md](data/README.md)).

The images are reconstructed by inputting the test fMRI data to the trained generator, and forward passing through the generator net.

We provide an example script, `end2end_test.py`, to reconstruct images from human brain fMRI activity.

``` shellsession
$ python end2end_test.py
```

### Train your own models

You can train your own models by using a training script (`end2end_training.py`).

1. Get preprocessed fMRI data and stimulus images (see [data/README.md](data/README.md)).
2. Create LMDB data. The LMDB data will be saved in `lmdb` directory.

        $ python end2end_create_lmdb.py

3. Download pre-trained CNN model (see [net/bvlc_reference_caffenet/README.md](net/bvlc_reference_caffenet/README.md)).
5. Run the training script. The trained models will be saved in `net_trained` directory.

        $ python end2end_training.py

## Reference

[1] We used the framework proposed in this article: [Dosovitskiy & Brox (2016) Generating Images with Perceptual Similarity Metrics based on Deep Networks. Advances in Neural Information Processing Systems (NIPS).](http://lmb.informatik.uni-freiburg.de//Publications/2016/DB16c)

The article is available at: http://arxiv.org/abs/1602.02644

[2] The code for training models are modified from the released code of the above article, and the original code are available at: https://lmb.informatik.uni-freiburg.de/resources/binaries/arxiv2016_alexnet_inversion_with_gans/release_deepsim_v0.5.zip

[3] The code for creating LMDB data are based on the example code shared in: http://deepdish.io/2015/04/28/creating-lmdb-in-python/

[4] For the details of fMRI preprocessing, please refer to: Shen, Horikawa, Majima, and Kamitani (2019) Deep image reconstruction from human brain activity, http://dx.doi.org/10.1371/journal.pcbi.1006633

## Author

Shen Guo-Hua

## Contact

Kamitani Lab, Kyoto University and ATR <kamitanilab@gmail.com>

## Acknowledgement

The author thanks precious discussion and advice from the members in DNI (http://www.cns.atr.jp/dni/) and Kamitani Lab (http://kamitani-lab.ist.i.kyoto-u.ac.jp/).
The author thanks Mitsuaki Tsukamoto for software installation and computational environment setting.
The author thanks Tomoyasu Horikawa for fMRI data preprocessing.
The author thanks Shuntaro Aoki for data curation and example code to read fMRI data.
