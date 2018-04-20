####mnist01####
The outcome of the original code is 0.8766.
1. I change the number of layers. I compared the original one hidden layer with the two hidden layer and no hidden layer. The outcome of two hidden layer is 0.8722, for no hidden layer is 0.8710. So I found it¡¯s no good to change the number of layers.  
  
2. I changed the standard deviation in Line 24.
Standard Deviation 	Outcome
0.05	0.7884
0.2	0.8840
0.3	0.4213
The best one is around 0.2.
3. I changed the bias in Line 30. I tried 0.5, 1.0 and 1.5, they didn¡¯t make a big difference. But I find setting it as 0.0001 makes the outcome better, it¡¯s 0.8805.
4. I changed the learning rate in Line 51.
Learning Rate	Outcome
0.25	0.8592
1.0	0.8942
1.5	0.8057
1.7	0.6218
The 1.0 is good.
5. I tried lower down the number of examples in one batch in Line 54. 
Example numbers in one batch	Outcome
90	0.8781
80	0.8792
1	0.3749
I found that a little bit lower helps.
6. I make the weight update steps higher, the higher, the outcome is better. So I set it as 10000, not taking too much running time. 
7. I tried change the number of nodes in the hidden layer to 784, it¡¯s 0.8748, didn¡¯t make good outcome.
So finally I chose the standard deviation in Line 24 is 0.2, the bias in Line 30 is 0.0001, the learning rate in Line 51 is 1.0, the number of examples in one batch in Line 54 is 80, the weight update steps is 10000, the final outcome is 0.9364.


####Script1####
I did the following tests: 

Original Gradient
test accuracy:  0.894

Using sigmoid(not good)
test accuracy:  0.8645

Add dropouts for the first layer (good)
test accuracy:  0.916

#Add regularization
test accuracy:  0.8917
0.1	test accuracy:  0.4777
0.0001	test accuracy:  0.1028

Only one layer with dropouts (similar to add dropouts for both layers)
test accuracy:  0.9185

keep_prob=0.001 (bad)
test accuracy:  0.1028

stddev=0.2 (bad)
test accuracy:  0.1028

stddev=0.04 (bed)
test accuracy:  0.9151

Bias=0.00001 (not good)
test accuracy:  0.8834


Node=4096 and two layer dropouts (good)
test accuracy:  0.9252

Add convolutional layer (bad)

So finally I use two layers and add dropouts for both layers, and increase the node numbers.
?
####Script2####
I did the following tests: 

Original Adam
test accuracy:  0.9091

Add dropouts (not good)
test accuracy:  0.9076

Adam delete dropouts (not good)
test accuracy:  0.9038

Node = 4096 (good)
test accuracy:  0.9143

Use sigmoid (bad)
test accuracy:  0.8554

So finally I use two layers and add dropouts for both layers, and increase the node numbers.
?
####Script3####
Gradient + convolutional (bad and slow)
Finally I add Learning Rate Decay and Regularization


####Script4####
use MomentumOptimizer, but not everytime works well
test accuracy:  0.9247 



####Script5####
I tried Adam combined  with two convolutional layers (too slow but good)
test accuracy:  0.957


