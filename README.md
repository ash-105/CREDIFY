# CREDIFY Framework
This project focuses on automating the fact-checking process for verifying open-domain claims. It utilizes expert-written justification articles to verify the veracity of these claims, aiming to improve the efficiency and accuracy of fact-checking procedures.

# RECTIFY Dataset
The complete  dataset is located in RECTIFY folder in excel file 'Dataset_with_evidences.xlsx'. The dataset consists of open-domain claims with meta-data which can be verified against expert-written justification article. We also provide seperate evidence corpus in file evidence_corpus for further analysis. 


## Environment:
we perform all the experiment on Google colab with python 3.7 installed. Install 


```python
!pip install transformers






# End-to-end CREDIFY Framework
The proposed end-to-end framework CREDIFY consists of three modules : passage retrieval , sentence selection and veracity prediction. The following sections describe the detail of modules for implementing End-to-end experiment. 


**1).Passage Retrieval** : The folder \GitHub Repositary\End-to-end\passage_level  consist of a jupyter file which retrieves the most relevant evidence to claim , at passage level from the evidence corpus. Place the Rectify dataset file in this directory  'Dataset_with_evidences.xlsx'. The model msmacro-DistilBERT will be downloaded from hugging face and retrieves the most relevant passage. The relevant evidence passage will be generated after running this code successfully with name passage_results.xlsx. 

**2).Sentence Selection** : This module of CREDIFY framework after generating the passage level results, will extract the most relevant sentence from the evidence passage. This extracted sentence is our final evidence for predicting claim's veracity. The folder \GitHub Repositary\End-to-end\sentence_level consists of jupyter file. we have also provided our generated passage_results.xlsx which was generated in previous stage. The bert-base-uncased model extracts the most relevant sentence from the passage and stored the results in excel file with name results.xlsx

 **3).Veracity prediction** : Before running this experiment, convert the results.xlsx file into .json format. This format will help in fine-tunning our model. The final results of end-to-end model are provided in this file. 


# Experiments and Evaluation 

We perform experiment on our  modules and compare our methodology with baseline models. The following sections describe the detail for implementing these experiments at module level.

**1).Passage Level Evaluation** 

We also provide gold standard evidence in our dataset . The model retrieves  the top 3 passages from the evidence corpus and use MRR (Mean Reciprocal Rank) for evaluating the performance . We compare the results of this model with baseline models BM25, TF-IDF, and DPR-DistilRoBERTa. The files for performing this experiment are located in folder GitHub Repositary\Experiments\Passage_level_evaluation. 

**2).Veracity Level Evaluation**

In this experiment, we analyze the impact of finetunning on natural language inferencing models. We compare the performance  of these models gold standard evidence sentence  and claim   by fine tunning  and without fine-tunning. The folder  \GitHub Repositary\Experiments\Veracity_level_evaluation contains this experiment. Place the original dataset in this folder before performing this experiment.  


**3). Contrastive Data Augmentation**

This contrastive augmentation technique increases the scale, capturing better insights and generalizing the patterns of negative claims. The file Augmented_Data_Generation_file.ipynb generates the negative claim. The results of the augmented dataset after converting into json formated are provided in aug_results file. The Augmented_entailment.ipynb file in \GitHub Repositary\Experiments\Contrastive Data Augmentation folder performs Entailment classification  with contrastive data augmentation.  












