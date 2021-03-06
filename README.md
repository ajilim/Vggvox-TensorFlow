# Vggvox-TensorFlow

This model is for speaker identification.

This model could be trained and test pre-trained on the [VoxCeleb(1)](http://www.robots.ox.ac.uk/~vgg/data/voxceleb/) datasets as described in the following paper:

```
[1] A. Nagrani*, J. S. Chung*, A. Zisserman, VoxCeleb: a large-scale speaker identification dataset, 
INTERSPEECH, 2017
```

### Demo

[http://chuyuan.vipgz1.idcfengye.com/](http://chuyuan.vipgz1.idcfengye.com/)

### Dependencies

[1] tensorflow-gpu=1.11.0 

[2] librosa=0.6.3 

[3] scipy=1.1.0 

### Platform

[1] Ubuntu 16.04

[2] Tesla P40

[3] Python 3.5  

### Train

Before training and testing, you must prepare the dataset and configure the environment well.

The full dataset can be freely downloaded from [VoxCeleb](http://www.robots.ox.ac.uk/~vgg/data/voxceleb/).

After get the full dataset, and you can see \[utils/vox1_split_backup.txt\] in this repo so just prepare a gpu environment, get start training!

Training:

```
$ python3 train.py train --voxceleb_wav_dir [wav_dir] --vox_split_txt_file [split_file] --batch_size [bs] --lr [lr] --ckpt_save_dir [save_dir]
```

The args:

1. --voxceleb_wav_dir: After you get full dataset, you will find all data is in a wav dir. Record the dir path.
2. --vox_split_txt_file: You can find this file in \[utils/vox1_split_backup.txt\], and you can also find it in [VoxCeleb](http://www.robots.ox.ac.uk/~vgg/data/voxceleb/).
3. --batch_size: Batch size.
4. --lr: Learning rate. The default optimizer is Adam.
5. --ckpt_save_dir: Where you want to save the ckpt files. Default max ckpt files is 3.

### Test

Before test, you must have the pre-trained ckpt file. 

Test:

```
$ python3 train.py test --voxceleb_wav_dir [wav_dir] --vox_split_txt_file [split_file] --batch_size [bs] --ckpt_restore_file [ckpt_file]
```

The args:

1. --voxceleb_wav_dir: After you get full dataset, you will find all data is in a wav dir. Record the dir path.
2. --vox_split_txt_file: You can find this file in \[utils/vox1_split_backup.txt\], and you can also find it in [VoxCeleb](http://www.robots.ox.ac.uk/~vgg/data/voxceleb/).
3. --batch_size: Batch size.
5. --ckpt_restore_file: Pre-trained model.

### Example

Training:

```
$ python3 train.py train --voxceleb_wav_dir '/data/ChuyuanXiong/up/wav/' --vox_split_txt_file 'utils/vox1_split_backup.txt' --batch_size 32 --lr 0.001 --ckpt_save_dir '/data/ChuyuanXiong/backup/speaker_real318_ckpt' 
```

Testing:

```
$ python3 train.py test --voxceleb_wav_dir '/data/ChuyuanXiong/up/wav/' --vox_split_txt_file 'utils/vox1_split_backup.txt' --batch_size 32 --ckpt_restore_file '/data/ChuyuanXiong/backup/triplet_backup2/Speaker_vox_iter_51500.ckpt' --random_seed 100
```

### Dataset

Set | # POIs | Utterances
----|--------|----------
Train| 1251  |  145265 
Test | 1251  |  8251
Total| 1251  |  153516 

Dataset | My Result
-------|-----------
voxceleb1 | acc=0.7, eer=0.08


### Models

[Model, password: 8gy0](https://pan.baidu.com/s/1fxd-LGzFBUlB9fhBrZHnLQ) trained by me, and this could be used in this repo. The accuracy is about 70%, this can be further optimized. Verification eer=8%.

[Model](https://github.com/a-nagrani/VGGVox) trained by the author, this is for Matlab.

### Citation

```
@InProceedings{Nagrani17,
  author       = "Nagrani, A. and Chung, J.~S. and Zisserman, A.",
  title        = "VoxCeleb: a large-scale speaker identification dataset",
  booktitle    = "INTERSPEECH",
  year         = "2017",
}
```




