# Constraint-AAAI-2021-Hostility-Detection-in-Hindi-Using-Multilingual-Finetuned-Features
Published research Work at Constraint 2021: Workshop of the prestigious AAAI 2021 (Core A*) conference. 
Publisher: Springer CCIS (Paper - https://link.springer.com/chapter/10.1007/978-3-030-73696-5_19) 

[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/Arko98/Hostility-Detection-in-Hindi-Constraint-2021/blob/main/LICENSE)
[![others](https://img.shields.io/badge/Huggingface-Cuda%2011.1.0-brightgreen)](https://huggingface.co/)
[![others](https://img.shields.io/badge/PyTorch-Stable%20(1.8.1)-orange)](https://pytorch.org/)

# Workshop Details
1) Workshop Name: CONSTRAIN 2021 (Workshop on Combating Online Hostile Posts in Regional Languages during Emergency Situation)
2) Workshop Page: https://constraint-shared-task-2021.github.io/
3) Conference Name: 35th AAAI Conference on Artificial Intelligence 2021 (Core A*)
4) Conference Page: https://aaai.org/Conferences/AAAI-21/

## Authors
1) Arkadipta De (https://github.com/Arko98) [IIT Hyderabad M.Tech in Artificial Intelligence]  [Main and Corresponding Author]
2) Venkatesh Elangovan (https://github.com/venkateshelangovan) [IIT Hyderabad M.Tech in Artificial Intelligence]
3) Kaushal Kumar Maurya (https://github.com/kaushal0494) [IIT Hyderabad PhD in Computer Science and Engineering]
4) Dr. Maunendra Sankar Desarkar (https://www.iith.ac.in/~maunendra/) [Assistant Professor, Computer Science and Engineering Department, IIT Hyderabad]

Contact: 
1) Arkadipta De - ai20mtech14002@iith.ac.in
2) Venkatesh E  - ai20mtech14005@iith.ac.in
3) Kaushal Kumar Maurya - cs18resch11003@iith.ac.in 

## Citation Details
For research purpose, please cite the following
```
@InProceedings{10.1007/978-3-030-73696-5_19,
author="De, Arkadipta
and Elangovan, Venkatesh
and Maurya, Kaushal Kumar
and Desarkar, Maunendra Sankar",
editor="Chakraborty, Tanmoy
and Shu, Kai
and Bernard, H. Russell
and Liu, Huan
and Akhtar, Md Shad",
title="Coarse and Fine-Grained Hostility Detection in Hindi Posts Using Fine Tuned Multilingual Embeddings",
booktitle="Combating Online Hostile Posts in Regional Languages during Emergency Situation",
year="2021",
publisher="Springer International Publishing",
address="Cham",
pages="201--212",
abstract="Due to the wide adoption of social media platforms like Facebook, Twitter, etc., there is an emerging need of detecting online posts that can go against the community acceptance standards. The hostility detection task has been well explored for resource-rich languages like English, but is unexplored for resource-constrained languages like Hindi due to the unavailability of large suitable data. We view this hostility detection as a multi-label multi-class classification problem. We propose an effective neural network-based technique for hostility detection in Hindi posts. We leverage pre-trained multilingual Bidirectional Encoder Representations of Transformer (mBERT) to obtain the contextual representations of Hindi posts. We have performed extensive experiments including different pre-processing techniques, pre-trained models, neural architectures, hybrid strategies, etc. Our best performing neural classifier model includes One-vs-the-Rest approach where we obtained 92.60{\%}, 81.14{\%}, 69.59{\%}, 75.29{\%} and 73.01{\%} F1 scores for hostile, fake, hate, offensive, and defamation labels respectively. The proposed model (https://github.com/Arko98/Hostility-Detection-in-Hindi-Constraint-2021) outperformed the existing baseline models and emerged as the state-of-the-art model for detecting hostility in the Hindi posts.",
isbn="978-3-030-73696-5"
}
```

## Instructions for Fine-Tuning
General Instructions:
a. Run all Code files in Google Colab
b. Use Links to Download or Load the Finetuned Models into Colab Local Directory (These FineTuned Models were used to produce results)

1. Load Provided bin_train.xlxs and bin_validate.xlxs into Coarse-Grained_Finetune (mBERT).ipynb and run. It will return two .npy files 
      a. Train_Probs_Coarse_mBERT.npy
      b. Test_Probs_Coarse_mBERT.npy
    => Note: Already finetuned Model link: https://drive.google.com/drive/folders/1GD-3vX7tV2caTi8k5kF208aeDvqrWNez?usp=sharing

2. Load Provided bin_train.xlxs and bin_validate.xlxs into Coarse-Grained_Finetune (XLMR).ipynb and run. It will return two .npy files 
      a. Train_Probs_Coarse_XLMR.npy
      b. Test_Probs_Coarse_XLMR.npy
    => Note: Already finetuned Model link: https://drive.google.com/file/d/1zJAZBNTgICJdVCUBblMVvICoHN7ivE8c/view?usp=sharing
   Additionally this code will give two more .npy files
      a. Train_Labels.npy (Train Labels from bin_train.xlxs)
      b. Test_Labels.npy (Validation Labels from bin_validate.xlxs)

3. Load The following files into Colab Local Directory
      a. Train_Probs_Coarse_mBERT.npy
      b. Test_Probs_Coarse_mBERT.npy
      c. Train_Probs_Coarse_XLMR.npy
      d. Test_Probs_Coarse_XLMR.npy
      e. Train_Labels.npy
      f. Test_Labels.npy
   And run the code Coarse_Grained_Ensemble_Finetune.ipynb. It will give the following two files - 
      a. Task_1_Pred_Labels.npy (Predicted Labels for bin_validate.xlxs) [0 = non_hostile, 1= hostile]
      b. Task_1_Best.h5 (Ensemble Model's Saved Weights after Finetuning)
   => Note: Already finetuned Model link: https://drive.google.com/file/d/1Jxbh675wwhYGZ_zqGjtrlxILMcXgSxAF/view?usp=sharing

4. Using the Task_1_Pred_Labels.npy we then change the bin_validate.xlxs dataset into four versions (Fake, Hate, Defamation and Offensive).
   Each file has labels as {Fake,Non-Fake}, {Hate,Non-Hate} etc. We provide the files as follows -
      a. fake_train.xlxs and fake_validate.xlxs
      b. hate_train.xlxs and hate_validate.xlxs
      c. offensive_train.xlxs and offensive_validate.xlxs
      d. defamation_train.xlxs and defamation_validate.xlxs 

5. Load fileset a or b or c (from Point 4) in code Fine_Grained_Finetune (Fake,Hate,Offensive).ipynb seperately and run three times separately. 
   It will return one .npy file each time - 
      a. Final_Fake_validation_Pred_Label.npy for Fileset a
      b. Final_Hate_validation_Pred_Label.npy for Fileset b
      c. Final_Offensive_validation_Pred_Label.npy for Fileset c
   => Note: Model link (for fileset a): https://drive.google.com/file/d/1MakVA0Tq2Lw7NVUbPNYMS6-mIC4xoVt8/view?usp=sharing
   => Note: Model link (for fileset b): https://drive.google.com/file/d/1-HQpdByfHOSfK1K_EVDLDUxzAm9yzcYf/view?usp=sharing
   => Note: Model link (for fileset c): https://drive.google.com/file/d/1hZHEIdXI3RDwzJwV0xUiqn9Ux9fhmpqN/view?usp=sharing

6. Load fileset d (from Point 4) in code Fine_Grained_Finetune (Defamation).ipynb run. It will return the following .npy file.
	  a. Final_Defamation_validation_Pred_Label.npy for Fileset d
   => Note: Model link (for fileset d): https://drive.google.com/drive/folders/1lFfOVSikbP-aRWHev_NoEdLYYS38mw6E?usp=sharing

7. Load the four files as below in the Final_Result_Validation.ipynb -
	  a. Final_Fake_validation_Pred_Label.npy
	  b. Final_Hate_validation_Pred_Label.npy
      c. Final_Offensive_validation_Pred_Label.npy
      d. Final_Defamation_validation_Pred_Label.npy
    and run. It will return -
      a. answer.csv (Final Submission File for Validation Dataset)
      b. Shows the Complete Result according to Official Evaluation Script (released by Organizers)
      
## Instructions for Model-Inference
General Instructions:
a. Run all Code files in Google Colab
b. For reproducilibility always load the pretrained models from provided links and do not run training, directly run inference.
c. Use Links to Download or Load the Finetuned Models into Colab Local Directory (These FineTuned Models were used to produce results)
d. Change Paths accordingly

1. Load Provided bin_train.xlxs and Validation.xlxs (for producing Validation Results) / Hindi_Test.xlxs (for producing Test Results) into Coarse-Grained_Finetune (mBERT).ipynb and run. It will return an .npy file 
      a. Test_Probs_Coarse_mBERT.npy
    => Note: Already finetuned Model link: https://drive.google.com/drive/folders/1GD-3vX7tV2caTi8k5kF208aeDvqrWNez?usp=sharing

2. Load Provided bin_train.xlxs and Validation.xlxs (for producing Validation Results) / Hindi_Test.xlxs (for producing Test Results) into Coarse-Grained_Finetune (XLMR).ipynb and run. It will return an .npy file 
      a. Test_Probs_Coarse_XLMR.npy
    => Note: Already finetuned Model link: https://drive.google.com/file/d/1zJAZBNTgICJdVCUBblMVvICoHN7ivE8c/view?usp=sharing

3. Load The following files into Colab Local Directory
      a. Test_Probs_Coarse_mBERT.npy
      b. Test_Probs_Coarse_XLMR.npy
   And run the code Coarse_Grained_Ensemble_Finetune.ipynb. It will give the following file - 
      a. Task_1_Pred_Labels.npy [0 = non_hostile, 1= hostile]
   => Note: Already finetuned Model link: https://drive.google.com/file/d/1Jxbh675wwhYGZ_zqGjtrlxILMcXgSxAF/view?usp=sharing

4. Using Task_1_Pred_Labels.npy we separate the Predicted Hostile Posts from Validation.xlxs and create new data file known as Hostile_Validate.xlxs OR Using Task_1_Pred_Labels.npy we separate the Predicted Hostile Posts from Hindi_Test.xlxs and create new data file known as Hostile_Hindi_Test.xlxs

5. Load Hostile_Validate.xlxs (for producing Validation Results) / Hostile_Hindi_Test.xlxs (for producing Test Results) in code Fine_Grained_Finetune (Fake,Hate,Offensive).ipynb seperately and run three times separately with dataset parameter as (fake,hate,offensive) and Label_name parameter as (Fake,Hate,Offensive)
   It will return one .npy file each time - 
      a. Pred_Fake_Label.npy for dataset = 'fake' and Label_name = 'Fake'
      b. Pred_Hate_Label.npy for dataset = 'hate' and Label_name = 'Hate'
      c. Pred_Offensive_Label.npy for dataset = 'offensive' and Label_name = 'Offensive'
   => Note: Model link (for fake): https://drive.google.com/file/d/1MakVA0Tq2Lw7NVUbPNYMS6-mIC4xoVt8/view?usp=sharing
   => Note: Model link (for hate): https://drive.google.com/file/d/1-HQpdByfHOSfK1K_EVDLDUxzAm9yzcYf/view?usp=sharing
   => Note: Model link (for offensive): https://drive.google.com/file/d/1hZHEIdXI3RDwzJwV0xUiqn9Ux9fhmpqN/view?usp=sharing

6. Load defamation_train.xlxs and Hostile_Validate.xlxs (for producing Validation Results) / Hostile_Hindi_Test.xlxs (for producing Test Results) in code Fine_Grained_Finetune (Defamation).ipynb run. It will return the following .npy file.
	  a. Pred_Defamation_Label.npy for Defamation
   => Note: Model link (for defamation): https://drive.google.com/drive/folders/1lFfOVSikbP-aRWHev_NoEdLYYS38mw6E?usp=sharing

7. Load the files as below in the Final_Result.ipynb -
	  a. Pred_Fake_Label.npy
	  b. Pred_Hate_Label.npy
     c. Pred_Offensive_Label.npy
     d. Pred_Defamation_Label.npy
     e. Task_1_Pred_Labels.npy (from Point 3)
     f. Hostile_Validate.xlxs (for producing Validation Results)  / Hostile_Hindi_Test.xlxs (for producing Test Results)
    and run. It will return -
      a. Result.csv (Final Submission File Validation OR Test)
      b. Shows the Complete Result according to Official Evaluation Script (released by Organizers) (change addresses accordingly)



## Fine-Tuned Released Model Checkpoints

1. mBERT Coarse Grained   :      https://drive.google.com/drive/folders/1GD-3vX7tV2caTi8k5kF208aeDvqrWNez?usp=sharing
2. XLMR  Coarse Grained   :      https://drive.google.com/file/d/1zJAZBNTgICJdVCUBblMVvICoHN7ivE8c/view?usp=sharing
3. Coarse Grained         :      https://drive.google.com/file/d/1Jxbh675wwhYGZ_zqGjtrlxILMcXgSxAF/view?usp=sharing
4. Fine Grained Fake      :      https://drive.google.com/file/d/1MakVA0Tq2Lw7NVUbPNYMS6-mIC4xoVt8/view?usp=sharing
5. Fine Grained Hate      :      https://drive.google.com/file/d/1-HQpdByfHOSfK1K_EVDLDUxzAm9yzcYf/view?usp=sharing
6. Fine Grained Offensive :      https://drive.google.com/file/d/1hZHEIdXI3RDwzJwV0xUiqn9Ux9fhmpqN/view?usp=sharing
7. Fine Grained Defamation:      https://drive.google.com/drive/folders/1lFfOVSikbP-aRWHev_NoEdLYYS38mw6E?usp=sharing

Note: The Dataset can be found at official dataset repository https://github.com/mohit19014/Hindi-Hostility-Detection-CONSTRAINT-2021
