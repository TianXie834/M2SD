# Distilling Multi-level Semantic Cues across Multi-modalities for Face Forgery Detection(M2SD) 

Lingyun Yu, Tian Xie, Chuanbin Liu, Guoqing Jin, Zhiguo Ding, and Hongtao Xie

**Accepted by TCSVT**

## Abstract
> Existing face forgery detection methods attempt to identify low-level forgery artifacts (e.g., blending boundary, flickering) in spatial-temporal domains or high-level semantic inconsistencies (e.g., abnormal lip movements) between visual-auditory modalities for generalized face forgery detection. However, they still suffer from significant performance degradation when dealing with out-of-domain artifacts, as they only consider single semantic mode inconsistencies, but ignore the complementarity of forgery traces at different levels and different modalities. In this paper, we propose a novel Multi-modal Multi-level Semantic Cues Distillation Detection framework that adopts the teacher-student protocol to focus on both spatial-temporal artifacts and visual-auditory incoherence to capture multi-level semantic cues. Specifically, our framework primarily comprises the Spatial-Temporal Pattern Learning module and the Visual-Auditory Consistency Modeling module. The Spatial-Temporal Pattern Learning module employs a mask-reconstruction strategy, in which the student network learns diverse spatial-temporal patterns from a pixel-wise teacher network to capture low-level forgery artifacts. The Visual-Auditory Consistency Modeling module is designed to enhance the student network’s ability to identify high-level semantic irregularities, with a visual-auditory consistency modeling expert serving as a guide. Furthermore, a novel Real-Similarity loss is proposed to enhance the proximity of real faces in feature space without explicitly penalizing the distance from manipulated faces, which prevents the overfitting in particular manipulation methods and improves the generalization capability. Extensive experiments show that our method substantially improves the generalization and robustness performance. Particularly, our approach outperforms the SOTA detector by 1.4% in generalization performance on DFDC with large domain gaps, and by 2.0% in the robustness evaluation on the FF++ dataset under various extreme settings.

# Setup
First setup python 3.8.0 environment with pytorch 2.0.1 installed.

then install dependencies for the experiment:

```
pip install -r requirements.txt
```

# Test

## Inference Using fine-tuned Model on Raw Video
Download `M2SD` model fine-tuned on FF++ from [here](https://github.com/TianXie834/M2SD/releases/download/v1.0/M2SD.pt) and place it under `./save` folder
```bash
python test_on_raw_video.py examples/test.mp4 output
```
the output will be a video under folder `output` named `test.avi`

![](./examples/test.gif)

# TODO
- [x] Release model checkpoint.
- [x] Release inference code.
- [ ] Release training code.
- [ ] Code cleaning.


# Acknowledgments


This code borrows from [FTCN](https://github.com/yinglinzheng/FTCN) and [VideoaMAE](https://github.com/MCG-NJU/VideoMAE).

The face detection network comes from [biubug6/Pytorch_Retinaface](https://github.com/biubug6/Pytorch_Retinaface).

The face alignment network comes from [cunjian/pytorch_face_landmark](https://github.com/cunjian/pytorch_face_landmark).


# Citation
If you think this project is helpful, please feel free to cite our paper:
```
@ARTICLE{10819430,
  author={Yu, Lingyun and Xie, Tian and Liu, Chuanbin and Jin, Guoqing and Ding, Zhiguo and Xie, Hongtao},
  journal={IEEE Transactions on Circuits and Systems for Video Technology}, 
  title={Distilling Multi-level Semantic Cues across Multi-modalities for Face Forgery Detection}, 
  year={2024},
  volume={},
  number={},
  pages={1-1},
  keywords={Forgery;Semantics;Faces;Training;Overfitting;Feature extraction;Detectors;Robustness;Lips;Visualization;face forgery detection;spatial-temporal artifacts;transformer;knowledge distillation;metric learning},
  doi={10.1109/TCSVT.2024.3524602}}
```
