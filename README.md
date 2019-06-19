# Deep-emotion-feature-extraction
The scripts are for AVEC 2019 challenge (https://sites.google.com/view/avec2019/home) and emo-pain 2019 (). Currently, this code only works in Linux.

The code contains two parts: face alignment and deep feature extraction.

# Usage:

1. Install OpenFace

2. Copy all files in .zip to './OpenFace/build/bin/'

3. Line 73, 76 and 79 in demo.py are comand lines for runing feature extraction scripts: feature_extraction_RESNET.py, feature_extraction_VGG.py, 
feature_extraction_RESNET_reg.py. Please changing them before the use to make the command lines suitable for your own machine.

4. Run demo by 'python demo.py'

5. You can choose your source video path (--src_vid_path), the path for saving deep features (--dest_out_data_path) as well as other options in command line. 
Please check 'demo.py' for details. 

Please convert all videos to .avi format if the code are not able to read videos. 

If .avi videos still can not be read, please using the following code to convert them.

mkdir -p converted
file *.avi | grep -v "Motion JPEG" | awk -F':' '{ print $1 }' | \
   xargs -L1 -I{} ffmpeg -i {} 
-c:v mjpeg -q:v 3 converted/{}


The code start with 'demo.py'. It will automatically process all videos in the 'videos folder', and save deep features in './Deep_feature' folder,
where 2048-D Affwild ResNet feature will be stored as '_RES.mat', 4096-D Affwild VGG features will be stored as '_VGG.mat' and 2048-D Imagenet ResNet 
feature will be stored as '_RES_reg.mat'.


# Dependency:

Tensorflow version 1.12.0

Python 3.6

Opencv2 

pandas

tqdm

# Citation

If you use this code, please cite 

[1] Baltrusaitis, Tadas, et al. "Openface 2.0: Facial behavior analysis toolkit." 2018 13th IEEE International Conference on Automatic Face & Gesture Recognition (FG 2018). IEEE, 2018.

[2] Kollias, Dimitrios, et al. "Deep affect prediction in-the-wild: Aff-wild database and challenge, deep architectures, and beyond." International Journal of Computer Vision (2019): 1-23.

[3] AVEC 2019 baseline paper

[4] Emo-pain 2019 baseline paper

# Contact:

If there is any problem in the code, please contact siyang.song@notingham.ac.uk
