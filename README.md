0. Bước 1 : Tải các thư viện đúng version theo file requirement_ts.txt
0. Bước 2 : Install espeak
```sh
sudo apt-install espeak

0. Bước 3 : Tạo 1 folder data
0. Bước 4 : Download dataset : LJ Speech và giải nén trong folder : data
0. Bước 5 : Rename và create a link to dataset
```sh
ln -s data/path/to/LJSpeech-1.1/wavs DUMMY1
```
0. Bước 6 :
```sh
cd monotoic_align
python setup.py build_ext --inplace
```
0. Bước 7 : Tạo 1 folder monotonic_align trong folder monotonic_align
0. Bước 8 : copy file: core.cpython-37m-x86_64-linux-gnu.so trong đường dẫn Desktop/tts/vits-main/monotonic_align/build/lib.linux-x86_64-3.7/monotonic_align sang đường dẫn monotonic_align/monotonic_align
0. Bước 9 : 
```sh
cd ..
```
0. Bước 10 : 
```sh
python train.py -c configs/ljs_base.json -m ljs_base
```
