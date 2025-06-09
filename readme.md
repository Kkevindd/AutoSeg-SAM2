# README
This is an automatic full segmentation tool based on zrporz/autoseg-sam2 

## Environment Setup
First, clone this repository and submodules
```bash
#SSH
git clone git@github.com:zrporz/AutoSeg-SAM2.git --recursive
```
or
```bash
#HTTPS
git clone https://github.com/zrporz/AutoSeg-SAM2.git --recursive
```



The code requires `python>=3.10`, as well as `torch>=2.3.1` and `torchvision>=0.18.1`
We use [SAM1](https://github.com/zrporz/segment-anything-1) to provide static segmentation results and use the [SAM2](https://github.com/facebookresearch/segment-anything-2) to track the static segmentation results. You can install them by the following commands
```bash
### install sam1 and sam2 modules
pip install -e submodule/segment-anything-1
pip install -e submoudle/segment-anything-2
### download checkpoints
cd checkpoints/sam1
bash download.sh
cd ../sam2
bash download.sh
```


## Model paths initialized
Please update model paths in auto-mask-align-sav.py
```
sam2_checkpoint="/to/path/sam2_hiera_large.pt"      (line 504)
model_cfg="sam2_configs/sam2_hiera_l.yaml"          (line 505)
sam_ckpt_path="/to/path/sam_vit_h_4b8939.pth"       (line 511)
```
## Data setting
Please create paths.txt,write rgb video paths line by line，like
```
/to/path/123.mp4
/to/path/125.mp4
/to/path/128.mp4
```
Please create semantic directory,and create related subfolders
```
cd "/to/path"
mkdir output
cd output
mkdir semantic && mkdir json && mkdir temp && mkdir log

```
Open auto-mask-sav.sh,setting video_list,log_dir
```
video_list="/to/path/paths.txt"   (line 8)
log_dir="to/path/output"          (line 11)
```
## Run segment video and generate json file used rle encode
```
chmod +x auto-mask-sav.sh
./auto-mask-sav.sh
```

## Output
look output folder

## Attention
if video_name(from auto-mask-align-sav.py line 481) appear error, please modify regular expression in line 481

