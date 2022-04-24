
## Overview

The existing research in action recognition is mostly focused on high-quality videos where the action is distinctly visible. Therefore, the available action recognition models are not designed for low-resolution videos and their performance is still far from satisfactory when the action is not distinctly visible. In real-world surveillance environments, the actions in videos are captured at a wide range of resolutions. Most activities occur at a distance with a small resolution and recognizing such activities is a challenging problem.
  <br>
  
  The ActivityNet challenge has seen a wide range of tasks relevant to action recognition, ranging from temporal activity recognition to spatio-temporal action detection. However, in all the tasks we have seen so far, the focus has never been on low-resolution activities. In all the used datasets the videos are of high-resolution and the occurring activities cover most of the frame area.
  <br>
  
  In this challenge, the focus is on recognizing and detecting tiny actions in videos. The existing approaches addressing this issue perform their experiments on artificially created datasets where the high-resolution videos are down-scaled to a smaller resolution to create a low-resolution sample. However, re-scaling a high-resolution video to a lower- resolution does not reflect real world low-resolution video quality. Real world low-resolution videos suffer from grain, camera sensor noise, and other factors, which are not not present in the down-scaled videos. We will provide benchmark datasets for activity recognition and activity detection which contains natural low-resolution activities.
  <br>

## Tasks
This year we will focus on two different tasks:

- **Activity recognition**: The goal of this task is to recognize activities occurring in a video. There can be multiple activities happening at the same time. We will use Tiny-VIRAT-v2 benchmark for this task. The developed models should solve a multi-label classification problem and recognize all the activities occuring in a video. 

- **Activity detection**: In this task, the goal is to perform spatio-temporal localization of activities in videos. The developed models should not only recognize the activities, but also provide their spatio-temporal localization in the input video. Similar to the recognition task, this task can also have multiple activities at the same time. 

## Dataset details
This challenge will use two different benchmark datasets for the above tasks. For the recognition task, we will use TinyVIRAT-v2 benchmark and for activity detection we will use MAMA (Multi-Actor Muti-Action) dataset. 

**Recognition**: We will use TinyVIRAT-v2 benchmark for low-resolution action recognition. The videos in TinyVIRAT-V2 are realistic and extracted from real-world surveillance videos. This is a multi-label dataset with multiple actions per video clip which makes it even more challenging. The dataset has around 26355 activity instances with 16950 training, 3308 validation and 6097 testing instances. The length of the activities vary from sample to sample with an average length of around 3 seconds. It contains arbitrary sized low-resolution videos which ranged from 10x10 pixels to 128x128 pixels with an average of 70x70 pixels. The videos in the proposed dataset are naturally low resolution and they reflect real-life challenges.
  <br>
  
- Dataset download: <a href="https://www.crcv.ucf.edu/tiny-actions-challenge-cvpr2021/data/TinyVIRAT-v2.zip"> Tiny-VIRAT-v2</a>
- Code to train baseline models: <a href="https://github.com/aayushjr/tinyAction"> GitHub code</a>
- Pre-trained baseline models: <a href="https://www.crcv.ucf.edu/data1/tiny-actions/trained_weights/i3d_tinyVirat.pth"> I3D </a>, <a href="https://www.crcv.ucf.edu/data1/tiny-actions/trained_weights/r2p1d_K_50_tinyVirat.pth"> R(2+1)D </a>, <a href="https://www.crcv.ucf.edu/data1/tiny-actions/trained_weights/wideresnet_50_tinyVirat.pth"> ResNet50 </a>
- More details: <a href="https://arxiv.org/pdf/2107.11494.pdf">Report</a>    
<br>

**Detection**: We provide a new benchmark dataset (MAMA dataset) for activity detection which has naturally occurring tiny actions. This dataset is a temporally trimmed version of VIRAT/MEVA datasets. All of our samples are obtained from CCTV cameras mounted at high altitudes, which results in lower resolution of the action regions. MAMA consists of 35 classes. MAMA consists of a total of 32726 videos with 25837 videos in the train split, and 6889 videos in the test split. The length of clips in the dataset ranges from 1 sec to 5 sec. The action-classes in the MAMA dataset capture both human-human "indirect" actions like talking, as well as physical contact such as "hand_interacting_with_person". Furthermore, we also annotate the human-object interactions, such as opening a door, etc. Further details about the evaluation protocol and the annotation format can be found <a href="https://www.crcv.ucf.edu/research/projects/mama-multi-actor-multi-action-dataset-for-action-detection"> here </a>.

Here are the links to donwload the dataset
- Dataset Download: <a href="https://www.crcv.ucf.edu/data1/UCF-MAMA/UCF-MAMA-train.zip"> Train [118 GB]</a>, <a href="https://www.crcv.ucf.edu/data1/UCF-MAMA/UCF-MAMA-test.zip"> Test [31 GB] </a>
- Dataset Visualization: <a href='https://www.crcv.ucf.edu/data1/UCF-MAMA/UCF-MAMA.sq'> Link </a>
- Paper: <a href='https://arxiv.org/pdf/2204.07892.pdf'> Link </a>

  
## Evaluation
Both the tasks will be evaluated using a public leaderboard where the participants will submit their models prediction on the test set.


  **Recognition**: TinyVIRAT-v2 has multiple labels in each sample and the submissions will be asked to predict multiple action classes for each sample. The performers can choose a prediction threshold of their choice and will be required to submit only the occurring activities for each sample. The submissions will be evaluated using precision, recall, and F1-score. The winners will be determined based on the F1-score averaged over each class.
  <br>
  
  We will provide an evaluation server where the performers can submit their results. A text file with multiple lines will be submitted by the performers for evaluation where each line will have predictions for a test sample. The performers will be required to submit a one-hot vector indicating which activities are present for each test sample. These one-hot vectors will be used to compute class-wise precision, recall, and F1-score. 
  <br>  
  
  - Evaluation server: <a href="https://codalab.lisn.upsaclay.fr/competitions/1832"> Link </a>
  - Sample submission: <a href="https://www.crcv.ucf.edu/tiny-actions-challenge-cvpr2021/data/submission_sample.zip"> Link </a>

  **Detection**: MAMA dataset will have multiple activites in each sample and the submissions should contain detections for all activity instance in each sample. The performers can choose a prediction threshold of their choice and will be required to submit only the occurring activities for each sample. The submissions will be evaluated using frame-level and video-level mean-average precision (mAP) at 0.5 threshold. The winners will be determined based on the video-level mAP averaged over all classes at 0.5 threshold.
  <br>
  
  We will provide an evaluation server where the performers can submit their results. A text file with multiple lines will be submitted by the performers for evaluation where each line will have detections for a test sample. For action detection, the predictions will include the class probablity and detected bounding boxes on each frame of a video.
  <br>  
  
  - Evaluation server: Coming Soon!
  - Sample submission: Coming Soon!


## Important dates
- <strong> Feb 10, 2022 </strong>: Challenge is announced
- <strong> Feb 20, 2022 </strong>: Evaluation server for Recognition task is opened
- <strong> Apr 12, 2022 </strong>: Data for the "Detection" task is released
- <strong> May 30, 2022 </strong>: Submission deadline
- <strong> June 6, 2022 </strong>: Reports due
- <strong> June 10, 2022 </strong>: Winner announcement 

## Organizers
<div style="display: flex">
  <div style="width:22.5%">
    <a href="https://www.linkedin.com/in/praveen-tirupattur-2044ba51/">
    <img alt="Praveen" src="pics/praveen.jpg">
    </a><br>
    <a href="https://www.linkedin.com/in/praveen-tirupattur-2044ba51/">Praveen Tirupattur</a><br>
    CRCV, University of Central Florida (UCF)
  </div>
  
  <div style="width:2.5%">
  </div>
   
  <div style="width:22.5%">
    <a href="">
    <img alt="Aayush" src="pics/aayush.jpg">
    </a><br>
    <a href="">Aaysuh J Rana</a><br>
    CRCV, University of Central Florida (UCF)
  </div>
  
  <div style="width:2.5%">
  </div>
   
  <div style="width:22.5%">
    <a href="">
    <img alt="Akash" src="pics/ak_cvpr_im.jpg">
    </a><br>
    <a href="">Akash Kumar</a><br>
    CRCV, University of Central Florida (UCF)
  </div>
  
  <div style="width:2.5%">
  </div>
   
  <div style="width:22.5%">
    <a href="">
    <img alt="Rajat" src="pics/rajat.jpg">
    </a><br>
    <a href="">Rajat Modi</a><br>
    CRCV, University of Central Florida (UCF)
  </div>
   
  <div style="width:2.5%">
  </div>  

  <div style="width:22.5%">
    <a href="">
    <img alt="Shruti Vyas" src="pics/shruti.jpg">
    </a><br>
    <a href="">Shruti Vyas</a><br>
    CRCV, University of Central Florida (UCF)
  </div>
  
  <div style="width:2.5%">
  </div>
   
  <div style="width:22.5%">
    <a href="https://www.crcv.ucf.edu/person/rawat/">
    <img alt="Yogesh Rawat" src="pics/yogesh.jpg">
    </a><br>
  <a href="https://www.crcv.ucf.edu/person/rawat/">Yogesh Rawat</a><br>
    CRCV, University of Central Florida (UCF)
  </div>
  
  <div style="width:2.5%">
  </div> 
   
  <div style="width:22.5%">
    <a href="https://www.crcv.ucf.edu/person/mubarak-shah">
    <img alt="Mubarak Shah" src="pics/mubarak.jpg">
    </a><br>
  <a href="https://www.crcv.ucf.edu/person/mubarak-shah">Mubarak Shah</a><br>
    CRCV, University of Central Florida (UCF)
  </div>
  
</div>


## References
<div>
  Please cite the following works, if you use these datasets in your research:
  <ul>
    <li> Modi, Rajat, et al. "Video Action Detection: Analysing Limitations and Challenges." arxiv preprint arXiv:2204.07892 (2022). </li>
    <li> Tirupattur, Praveen, et al. "TinyAction Challenge: Recognizing Real-world Low-resolution Activities in Videos." arXiv preprint arXiv:2107.11494 (2021).       </li>
    <li> Demir, Ugur, et al. "TinyVIRAT: Low-resolution Video Action Recognition." 2020 25th International Conference on Pattern Recognition. IEEE Computer Society, 2021. </li>
  </ul>
</div>

## Contact
<div>
Feel free to contact us at yogesh@ucf.edu if you have any questions.
<br>  
Join this mailing list for updates: <a href="https://groups.google.com/g/tinyactions">https://groups.google.com/g/tinyactions</a>
<br>
Thanks for being with us!
</div>



