# PEPred: A machine Learning-based Approach for Peptide function Prediction

This is a Peptide function prediction tool based on a machine learning approach that relies mainly on non-covalent interaction data of single chain protein in a protein complex.

GitHub Repository for [https://github.com/greenGM/PEPred](https://github.com/greenGM/PEPred)

[![Repository](https://img.shields.io/badge/View%20on-GitHub-blue.svg)](https://github.com/greenGM/PEPred)

## Dependencies:
  |     Name      | version            |
  | ------------- | ------------------ |
  | R             | 4.3.3 or higher    |
  | tidyverse     | 2.0.0 or higher    |
  | caret         | 6.0-94 or higher   |


## data genereation 

1. The descriptors were generated by using the following programs：

   Propy3 (version 1.1.1, https://pypi.org/project/propy3/)    (18 descriptors)
   Peptides (version 0.3.2, https://pypi.org/project/peptides/)     (132 descriptors)

3. All descriptors must be generated and follow the order in descriptors explanation.csv.
       
## How to use this tool:

1. Download all files.

2. Open in Rstudio or R.

3. Enter the following code：
   
     R
   
     load(".RData")
  
     library(tidyverse)
  
     library(caret)
  
     unknown <- read.csv("yourfile.csv",header = F,col.names = name)#Import your data; better without column name, if you have, please set "header = T".
   
     (Note: the first column of your data should start from the fi, not be the protein's name.)
  
     unknownS <-  predict(preprocessParams, unknown)
  
     unknownprediction <- data.frame(name=unknown$youproteinname, #the nameor the sequence infor of your peptide.
   
                                  preclass=predict(fit.C50.Tsmote,unknownS),
   
                                  preprob=predict(fit.C50.Tsmote,unknownS,type = 'prob' ))
                                  
     write.csv(unknownprediction,'PEPred.csv')
   

     (Note: Please adjust the above code to suit your needs.)

## Result explanation：
The result will be returned as a csv file.

     name--the name of the candidate nanobody.

     preclass-- Final predicted function.

     preprob.function--the probability of the predicted function. 


