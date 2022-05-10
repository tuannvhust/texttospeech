


## Pre-requisites
0. Python >= 3.6
0. Clone this repository
## Các bước training
1.Cài đặt các thư viện theo đúng version trong file [requirements.txt](requirements.txt)

2. install espeak : 
```sh
`sudo apt-get install espeak`
```

3. Tạo 1 folder "data"
4. Download datasets
    4.1. Download and extract the LJ Speech dataset in folder : "data", then rename or create a link to the dataset folder: 
    ```sh
    `ln -s data/LJSpeech-1.1/wavs DUMMY1`
    ```
    6.1. For mult-speaker setting, download and extract the VCTK dataset, and downsample wav files to 22050 Hz. Then rename or create a link to the dataset folder: `ln -s /path/to/VCTK-Corpus/downsampled_wavs DUMMY2`
7. Build Monotonic Alignment Search (bắt buộc) and run preprocessing if you use your own datasets.
```sh
# Cython-version Monotonoic Alignment Search
5.1"cd monotonic_align"
5.2core.cpython-37m-x86_64-linux-gnu.so"python setup.py build_ext --inplace"

# Preprocessing (g2p) for your own datasets. Preprocessed phonemes for LJ Speech and VCTK have been already provided.
# python preprocess.py --text_index 1 --filelists filelists/ljs_audio_text_train_filelist.txt filelists/ljs_audio_text_val_filelist.txt filelists/ljs_audio_text_test_filelist.txt 
# python preprocess.py --text_index 2 --filelists filelists/vctk_audio_sid_text_train_filelist.txt filelists/vctk_audio_sid_text_val_filelist.txt filelists/vctk_audio_sid_text_test_filelist.txt
```
6. Trong folder monotonic_align tạo 1 folder monotonic_align 
7. Copy file: core.cpython-37m-x86_64-linux-gnu.so trong đường dẫn Desktop/tts/vits-main/monotonic_align/build/lib.linux-x86_64-3.7/monotonic_align
ra folder monotonic_align/monotonic_align

## Training Exmaple
```sh
# LJ Speech
8. python train.py -c configs/ljs_base.json -m ljs_base

# VCTK
8. python train_ms.py -c configs/vctk_base.json -m vctk_base
```


## Inference Example
See [inference.ipynb](inference.ipynb)
