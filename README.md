## Towards Efficient Machine Unlearning with Data Augmentation:<br>  Guided Loss-Increasing (GLI) to Prevent the Catastrophic Model Utility Drop

* This repository provides PyTorch implementations of our proposed <b>Guided Loss-Increasing (GLI)</b> method, along with other state-of-the-art (SOTA) methods in machine unlearning.
* This work has been accepted to the **CVPR 2024** workshop on [FAIR, DATA-EFFICIENT, AND TRUSTED COMPUTER VISION (TCV2)](https://fadetrcv.github.io/2024/).
<br>
<p align="center"><img src="https://github.com/Dasol-Choi/GLI/blob/main/resources/gli_model.png" width=80%/></p>

## Authors
[Dasol Choi](https://github.com/Dasol-Choi), [Soora Choi](https://github.com/SooraChoi), [Eunsun Lee](https://github.com/eunsun111), [Jinwoo Seo](https://github.com/dukong1), [Donbin Na](https://github.com/ndb796)

## Abstract
> Machine unlearning algorithms aim to make a model forget specific data that might be used in the training phase.
To solve this problem, various studies have adopted loss-increasing methods.
For example, some unlearning methods have presented data augmentation methods to generate synthesized images that maximize loss values for <b>images to be forgotten</b>.
In contrast, some unlearning methods directly update the model in the direction of increasing loss for the images to be forgotten.
In this paper, we first revisit these loss-increasing methods and analyze their limitations.
We have found that these simple loss-increasing strategies can be effective in the aspect of the <b>forgetting score</b>, however, can hurt the <b>original model utility</b> unexpectedly, we call this phenomenon <b>catastrophic model utility drop</b>.
In this paper, we propose a novel data augmentation method, Guided Loss-Increasing (GLI), that restricts the direction of the data update to resolve the utility drop issue.
Our extensive experiments show our method shows superior (1) model utility and (2) forgetting performance compared to the previous state-of-the-art (SOTA) methods.
Furthermore, we demonstrate Jensen–Shannon divergence can be utilized to robustly evaluate the forgetting score.
All the datasets, source codes, and trained model weights will be available publicly after the paper is accepted.

## Concept of Machine Unlearning
* Machine unlearning is a process focused on selectively forgetting specific data or knowledge from a trained model, ensuring that the model behaves as if it had never encountered the deleted information, a critical aspect in maintaining data privacy and compliance.
<p align="center"><img src="https://github.com/Dasol-Choi/GLI/blob/main/resources/unlearning_concept.png" width=55%/></p>

## Dataset
### MUFAC and MUCAC
We utilize [MUFAC & MUCAC](https://github.com/ndb796/MachineUnlearning), Task-Agnostic Machine Unlearning BenchMark Dataset
* <b>MUFAC (Machine Unlearning for Facial Age Classifier)</b>: A multi-class age classification dataset based on AI HUB, featuring over 13,000 Asian facial images with annotations for age groups and personal identities, ideal for machine unlearning research.
* <b>MUCAC (Machine Unlearning for Celebrity Attribute Classifier)</b>: A multi-label facial attribute classification dataset based on CelebA, expanded to 30,000 images and enriched with personal identity annotations to support unlearning algorithms.

### Dataset Configuration
<br>
<p align="center"><img src="https://github.com/Dasol-Choi/GLI/blob/main/resources/dataset_config.png" width=55%/></p>

## Evaluation Metrics
In our study, we employ a comprehensive evaluation protocol to assess machine unlearning performance, focusing on two main aspects:
*  <b>Classification Accuracy for Model Utility</b><br>
: We measure the classification accuracy of the unlearned model, $\theta_{unlearned}$, on the test set. This metric helps us determine how well the model retains its utility for the original task after the unlearning process.
* <b>MIA for Forgetting Metric</b><br>
: To evaluate the effectiveness of unlearning, we use the membership inference attack (MIA) as a forgetting metric. This involves training a logistic regression model on loss values from both the training forget dataset and the unseen dataset. The forgetting score is calculated as $\text{abs}(0.5 - M)$, where $M$ is the accuracy of the MIA model, with lower scores indicating better forgetting.
* <b>Final Score for Comprehensive Performance</b><br>
: The final score combines the test accuracy and the forgetting score to provide a holistic measure of performance. It's calculated as $\{\textit{Test Acc} + (1 - \textit{Forgetting Score} * 2)\} / 2$, balancing the trade-off between retaining model utility and effectively forgetting the target data.

## Models Performance
> Detailed performance comparisons of various state-of-the-art unlearning methods and our GLI applied to our MUFAC and MUCAC datasets, using a ResNet18 model trained from scratch.
<p align="center"><img src="https://github.com/Dasol-Choi/GLI/blob/main/resources/performance.png" width=100%/></p>

## Citation
<pre>
@inproceedings{choi2024towards,
  title={Towards Efficient Machine Unlearning with Data Augmentation: Guided Loss-Increasing (GLI) to Prevent the Catastrophic Model Utility Drop},
  author={Choi, Dasol and Choi, Soora and Lee, Eunsun and Seo, Jinwoo and Na, Dongbin},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={93--102},
  year={2024}
}
</pre> 
