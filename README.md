# Detect AI-Generated Text Competition

## Problem Statement

The problem statement for this project can be found [here](https://www.kaggle.com/competitions/llm-detect-ai-generated-text/overview/description).

## Dataset

The original dataset is available on Kaggle: [Dataset Link](https://www.kaggle.com/competitions/llm-detect-ai-generated-text/data).


### Extended Dataset

To address the imbalance issue in the original dataset, additional AI-generated essays were added. The extended dataset can be found [here](https://www.kaggle.com/datasets/thedrcat/daigt-proper-train-dataset).

After identifying the imbalance, an undersampling technique was applied, resulting in a balanced dataset with 44,087 samples for each label '1' and '0'.

# Deep Neural Network Architecture

## Model Summary

```plaintext
Model: "model_1"
__________________________________________________________________________________________________
 Layer (type)                Output Shape                 Param #   Connected to                  
==================================================================================================
 input_2 (InputLayer)        [(None, 2500)]               0         []                            
                                                                                                  
 embedding_1 (Embedding)     (None, 2500, 32)             3081536   ['input_2[0][0]']             
                                                                                                  
 conv1d_1 (Conv1D)           (None, 2496, 128)            20608     ['embedding_1[0][0]']         
                                                                                                  
 flatten_1 (Flatten)         (None, 80000)                0         ['embedding_1[0][0]']         
                                                                                                  
 batch_normalization_2 (Bat  (None, 2496, 128)            512       ['conv1d_1[0][0]']            
 chNormalization)                                                                                 
                                                                                                  
 dense_2 (Dense)             (None, 64)                   5120064   ['flatten_1[0][0]']           
                                                                                                  
 dropout_2 (Dropout)         (None, 2496, 128)            0         ['batch_normalization_2[0][0]'
                                                                    ]                             
                                                                                                  
 batch_normalization_3 (Bat  (None, 64)                   256       ['dense_2[0][0]']             
 chNormalization)                                                                                 
                                                                                                  
 global_max_pooling1d_1 (Gl  (None, 128)                  0         ['dropout_2[0][0]']           
 obalMaxPooling1D)                                                                                
                                                                                                  
 dropout_3 (Dropout)         (None, 64)                   0         ['batch_normalization_3[0][0]'
                                                                    ]                             
                                                                                                  
 concatenate_1 (Concatenate  (None, 192)                  0         ['global_max_pooling1d_1[0][0]
 )                                                                  ',                            
                                                                     'dropout_3[0][0]']           
                                                                                                  
 dense_3 (Dense)             (None, 1)                    193       ['concatenate_1[0][0]']       

### Model Accuracy
![model accuracy](https://github.com/ojaswi18/LLM-Detect-AI-Generated-Text/assets/102872838/27655658-d008-4bc0-ada3-386d727a9ba7)


### Model Loss
![model loss](https://github.com/ojaswi18/LLM-Detect-AI-Generated-Text/assets/102872838/b2cffd35-db56-47a5-b00b-b3bd8548250d)



##This gave an accuracy of 82.3% on the test data of Kaggle.
 
