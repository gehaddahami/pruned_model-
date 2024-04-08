the baseline model is adapted from https://github.com/Xilinx/brevitas-radioml-challenge-21.git 

the pruning step is done in the following steps: 
1- all layers except for the first and last layers are pruned by zero-ing the weights that has the least magnitude (the l2 norm in this case) (unstructured pruning) 

2- running the inference directly after pruning the weights will result in a poor accuracy (lower than 10% in some cases), hence retraining is necessary

3- retraining the model for 20 epochs will restore the accuracy to a range close to the un-pruned model 

4- to avoid updating the weights during the training (backward step) a mask is applied to keep all the zero values of the weight even after the backward step  


finally, this work related to pruning is not final yet and might be further modified 
