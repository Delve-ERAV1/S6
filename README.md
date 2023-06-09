# S6



# <h1 align = "center">PART-1</h1>

# Backpropogation

In this assignment, we have made use of the Gradient Descent to train a Neural Network.
In the image, we have the following main components:

![backpropagation](https://github.com/Delve-ERAV1/S6/assets/11761529/f9cc9998-5d40-4f76-889c-35af134e1d75)

- Inputs ( ![formula](https://render.githubusercontent.com/render/math?math=i_1) and ![formula](https://render.githubusercontent.com/render/math?math=i_2))
- Weights (![formula](https://render.githubusercontent.com/render/math?math=w_1),![formula](https://render.githubusercontent.com/render/math?math=w_2),![formula](https://render.githubusercontent.com/render/math?math=w_3),![formula](https://render.githubusercontent.com/render/math?math=w_4),![formula](https://render.githubusercontent.com/render/math?math=w_5),![formula](https://render.githubusercontent.com/render/math?math=w_6),![formula](https://render.githubusercontent.com/render/math?math=w_7),![formula](https://render.githubusercontent.com/render/math?math=w_8))
- Hidden Neurons (![formula](https://render.githubusercontent.com/render/math?math=h_1),![formula](https://render.githubusercontent.com/render/math?math=h_2))
- Output Neurons (![formula](https://render.githubusercontent.com/render/math?math=o_1), ![formula](https://render.githubusercontent.com/render/math?math=o_2))
- Activated Neurons (![formula](https://render.githubusercontent.com/render/math?math=out_{h1}),![formula](https://render.githubusercontent.com/render/math?math=out_{h2}),![formula](https://render.githubusercontent.com/render/math?math=out_{o1}),![formula](https://render.githubusercontent.com/render/math?math=out_{o2}))
- Error because of outputs (![formula](https://render.githubusercontent.com/render/math?math=E_{1}),![formula](https://render.githubusercontent.com/render/math?math=E_{2}))
- Total Error (![formula](https://render.githubusercontent.com/render/math?math=E_{total}))
- There's no bias!

## Forward Propagation

- We start with our inital inputs as ![formula](https://render.githubusercontent.com/render/math?math=i_1%20=%200.05) and ![formula](https://render.githubusercontent.com/render/math?math=i_2%20=%200.1)
- The outputs we want to acheive are ![formula](https://render.githubusercontent.com/render/math?math=t_1%20=%200.01) and ![formula](https://render.githubusercontent.com/render/math?math=t_2%20=%200.99) 
- The initial weights are ![formula](https://render.githubusercontent.com/render/math?math=w_1%20=%200.15) ,![formula](https://render.githubusercontent.com/render/math?math=w_2%20=%200.2) , ![formula](https://render.githubusercontent.com/render/math?math=w_3%20=%200.25) , ![formula](https://render.githubusercontent.com/render/math?math=w_4%20=%200.3)
- We perform a FORWARD PASS through the network
- The h1 is calulated by: ![formula](https://render.githubusercontent.com/render/math?math=h_{1}%20=%20i_{1}\times%20w_{1}%2Bi_{2}\times%20w_{2})
- Similarly, h2 is calulated by: ![formula](https://render.githubusercontent.com/render/math?math=h_{2}%20=%20i_{1}\times%20w_{3}%2Bi_{2}\times%20w_{4})
- The output of these hidden neurons are given after performing Sigmoid Activation:
- Sigmoid is given as :  ![formula](https://render.githubusercontent.com/render/math?math=\sigma(h)=(1%20/%201%20%2B%20\exp(h)))
- Thus, a_h1 is given by: ![formula](https://render.githubusercontent.com/render/math?math=a_{h1}=\sigma({h_1}))
- And similarly, ![formula](https://render.githubusercontent.com/render/math?math=a_{h2}=\sigma({h_2}))
- Using the same rules, we get outputs as:
- ![formula](https://render.githubusercontent.com/render/math?math=o_1=w_5a_{h_1}%2Bw_6a_{h_2}%20\%20\%20and%20\%20\%20o_2=w_7a_{h_1}%2Bw_8a_{h_2})
- After applying sigmoid: ![formula](https://render.githubusercontent.com/render/math?math=a_{o_1}=\sigma(o_1)\%20\%20and%20\%20\%20a_{o_2}=\sigma(o_2))

## Error Calculation
- The errors are due to the differences in the expected outputs from the neuron and the received outputs
- The output from the output neurons were ![formula](https://render.githubusercontent.com/render/math?math={o_1}%20\%20and%20\%20{o_2}), whereas the expected outputs (i.e., the target values) are ![formula](https://render.githubusercontent.com/render/math?math={t_1}%20\%20and%20\%20{t_2})
- The error is quantified by the squared error of their difference: 
- ![formula](https://render.githubusercontent.com/render/math?math=E_1=(t_1-a_{o_1})^2%20\%20.\%20E_2=(t_2-a_{o_1})^2)
- And total error is ![formula](https://render.githubusercontent.com/render/math?math=E_{total}=E_1%20\%20%2B\%20E_2)

## Weight updates (Back Propogation)
- To update weights, we use Gradient Descent:
![formula](https://render.githubusercontent.com/render/math?math=W_{new}=W_{old}-\eta\nabla{E_{total}})
- Here, ![formula](https://render.githubusercontent.com/render/math?math=W_{new}) is the updated weight after performing a backward pass
![formula](https://render.githubusercontent.com/render/math?math=W_{old}) is the old weight, ![formula](https://render.githubusercontent.com/render/math?math=\eta) is the learing rate and ![formula](https://render.githubusercontent.com/render/math?math=\nabla{E_{total}}) is gradient of the total loss
- To compute these derivatives, we use partial derivatives: 
      - We start from ![formula](https://render.githubusercontent.com/render/math?math=E_{total}) and calculate partial derviative with respect to ![formula](https://render.githubusercontent.com/render/math?math=w_5):
      - ![formula](https://render.githubusercontent.com/render/math?math=E_{1}) is the part of the Error whcih is caused because of ![formula](https://render.githubusercontent.com/render/math?math=w_5) 
          ![formula](https://render.githubusercontent.com/render/math?math=\frac{\partial%20E_1}{\partial%20w_5}%20=%20\frac{\partial%20E_1}{\partial%20a_{o_1}}%20\frac{\partial%20a_{o_1}}{\partial%20o_1}%20\frac{\partial%20o_1}{\partial%20w_5}) (using Chain Rule )
- From this equation, we can calculate ![formula](https://render.githubusercontent.com/render/math?math=\frac{\partial%20E_1}{\partial%20a_{o_1}}%20) as ![formula](https://render.githubusercontent.com/render/math?math=a_{o_1}-t_1)
- And, ![formula](https://render.githubusercontent.com/render/math?math=\frac{\partial%20a_{o_1}}{\partial%20o_1}%20=%20(a_{o_1})(1-a_{o_1}))
- Finally, ![formula](https://render.githubusercontent.com/render/math?math=\frac{\partial%20o_1}{\partial%20w_5}%20=%20a-o_1)
- Using these 4 equations, we come up with the weight update formula:
 ![formula](https://render.githubusercontent.com/render/math?math=W_{5new}%20=%20W_{5old}%20-%20\eta%20\frac{\partial%20E_1}{\partial%20w_5})
- Similarly we calculated weight updtaes for ![formula](https://render.githubusercontent.com/render/math?math=w_6), ![formula](https://render.githubusercontent.com/render/math?math=w_7) and ![formula](https://render.githubusercontent.com/render/math?math=w_8) for the purpose of Back Propogation.

- Back Propogation goes from Outputs to the 1st layer, updating weights in its way. 
- Coming to the 1st layer, the weights ![formula](https://render.githubusercontent.com/render/math?math=w_1),![formula](https://render.githubusercontent.com/render/math?math=w_2), ![formula](https://render.githubusercontent.com/render/math?math=w_3) and ![formula](https://render.githubusercontent.com/render/math?math=w_4) are updated using the formula:
- ![formula](https://render.githubusercontent.com/render/math?math=\frac{\partial%20E_t}{\partial%20w_1}%20=%20\frac{\partial%20E_t}{\partial%20a_{o_1}}%20\frac{\partial%20a_{o_1}}{\partial%20o_1%20}%20\frac{\partial%20o_1}{\partial%20a_{h_1}}%20\frac{\partial%20a_{h_1}}{\partial%20h_1}%20\frac{\partial{h_1}}{\partial{w_1}})
- The above is the Derivative of the Error wrt ![formula](https://render.githubusercontent.com/render/math?math=w_1). We similarly calculated the Partial Derivative wrt ![formula](https://render.githubusercontent.com/render/math?math=w_2), ![formula](https://render.githubusercontent.com/render/math?math=w_3) and ![formula](https://render.githubusercontent.com/render/math?math=w_4).
- Once all the weights were updated, then once again the cycle of forward propagtion and backward propagation repeats as many times as the number of epochs is (We ran for approximately 360 epochs).
## Learing Rate

- The rate at which updation of weights takes place is controlled by the learning rate. Learning rate is the step size to move towards the minimum of a loss function.
- A low learning rate will make the training time longer where as  very high learning rate might miss the local minimum of loss function and diverge.Hence an optimal learning rate needs to be chosen inorder to train the network quickly to attain the best accuracy.
- We noticed a steep decrease in loss as the learning rate was increased from 0.1 to 2.
-  ![formula](https://render.githubusercontent.com/render/math?math=\eta)
- Learning Rate ![formula](https://render.githubusercontent.com/render/math?math=\eta%20=%200.1) :
- ![LR-0 1](https://github.com/Delve-ERAV1/S6/assets/11761529/071b0da6-afa9-47d6-a7fe-5cd79eaf4f7b)
- Learning Rate ![formula](https://render.githubusercontent.com/render/math?math=\eta%20=%200.2) :
- ![LR-0 2](https://github.com/Delve-ERAV1/S6/assets/11761529/412b69e3-c738-4a91-82cd-8d387f28b410)
- Learning Rate ![formula](https://render.githubusercontent.com/render/math?math=\eta%20=%200.5) :
- ![LR-0 5](https://github.com/Delve-ERAV1/S6/assets/11761529/23995a0b-37f4-47aa-bef0-0005bf4e7568)
- Learning Rate ![formula](https://render.githubusercontent.com/render/math?math=\eta%20=%200.8) :
- ![LR-0 8](https://github.com/Delve-ERAV1/S6/assets/11761529/1ce5dba8-2174-4c6a-8f34-a5afbc677d79)
- Learning Rate ![formula](https://render.githubusercontent.com/render/math?math=\eta%20=%201) :
- ![LR-1 0](https://github.com/Delve-ERAV1/S6/assets/11761529/a205e1cb-4e82-41b9-95f2-98d1c938969e)
- Learning Rate ![formula](https://render.githubusercontent.com/render/math?math=\eta%20=%202) :
- ![LR-2 0](https://github.com/Delve-ERAV1/S6/assets/11761529/6605b75d-b686-4001-8648-8cc915c8a147)

# <h1 align = "center">PART-2</h1>

# Training MNIST Dataset with Neural Network with less than 20k parameters and achieve greater than 99.4% accuracy.

## Highlights
<ul>
  <li>Trained with less than 20000 parameters</li>
  <li>Achieved a Test accuracy of greater than 99.4% in less than 20 epochs</li>
</ul>

## Model Construction 

#### Model Architecture
```
----------------------------------------------------------------
        Layer (type)               Output Shape         Param #
================================================================
            Conv2d-1           [-1, 16, 26, 26]             144
              ReLU-2           [-1, 16, 26, 26]               0
       BatchNorm2d-3           [-1, 16, 26, 26]              32
         Dropout2d-4           [-1, 16, 26, 26]               0
            Conv2d-5           [-1, 16, 24, 24]           2,304
              ReLU-6           [-1, 16, 24, 24]               0
       BatchNorm2d-7           [-1, 16, 24, 24]              32
            Conv2d-8           [-1, 32, 22, 22]           4,608
              ReLU-9           [-1, 32, 22, 22]               0
      BatchNorm2d-10           [-1, 32, 22, 22]              64
        Dropout2d-11           [-1, 32, 22, 22]               0
           Conv2d-12           [-1, 16, 22, 22]             528
             ReLU-13           [-1, 16, 22, 22]               0
        MaxPool2d-14           [-1, 16, 11, 11]               0
           Conv2d-15             [-1, 16, 9, 9]           2,304
             ReLU-16             [-1, 16, 9, 9]               0
      BatchNorm2d-17             [-1, 16, 9, 9]              32
        Dropout2d-18             [-1, 16, 9, 9]               0
           Conv2d-19             [-1, 16, 9, 9]           2,304
             ReLU-20             [-1, 16, 9, 9]               0
      BatchNorm2d-21             [-1, 16, 9, 9]              32
        Dropout2d-22             [-1, 16, 9, 9]               0
           Conv2d-23             [-1, 16, 7, 7]           2,304
             ReLU-24             [-1, 16, 7, 7]               0
      BatchNorm2d-25             [-1, 16, 7, 7]              32
        Dropout2d-26             [-1, 16, 7, 7]               0
           Conv2d-27             [-1, 32, 5, 5]           4,608
             ReLU-28             [-1, 32, 5, 5]               0
      BatchNorm2d-29             [-1, 32, 5, 5]              64
        Dropout2d-30             [-1, 32, 5, 5]               0
           Conv2d-31             [-1, 10, 5, 5]             320
        AvgPool2d-32             [-1, 10, 1, 1]               0
================================================================
Total params: 19,712
Trainable params: 19,712
Non-trainable params: 0
----------------------------------------------------------------
Input size (MB): 0.00
Forward/backward pass size (MB): 1.28
Params size (MB): 0.08
Estimated Total Size (MB): 1.35
----------------------------------------------------------------
```
<ul>
While constructing the model, a few techniques were used to surpass our goal of 99.4% validation accuracy. Our model contains 2 blocks with a transition layer in between. 

<li> <p><b>Batch Normalization</b></p>
<p>We apply Batch normalization at every layer to normalize the inputs to the next layer. </p>
</li>
<li> <p><b>Drop-out</b></p>
<p>We apply drop out after batchnorm every time to regularize our input and to prevent our model from overfitting.</p>
</li>
<li> <p><b>Max Pooling</b></p>
<p>Max pooling was applied after we reached a receptive field of 7. At this point, the model captures lines / edges, curves in its entirety and can now combine features into higher level objects. </p>
</li>
<li> <p><b>1x1 Convolution</b></p>
<p>Together with the Max Pooling layer, this makes up our transition layer. This is primarily to reduce the number of channels while effectively combining features from all channels.  </p>
</li>
<li> <p><b>Global Average Pooling</b></p>
<p>This layer is introduced when our channel dimension is 5x5. Not only does this translate convolutional structure to linear structure, it has the added advantage of having less parameters to compute and since it doesn't have to learn anything, it helps avoid overfitting. This is a sort of transition layer. </p>
</li>

</ul>


<p align="center"> <strong>CONV2D_1 -> 28 x 28 x 1  || (3x3x1) x16  || 26 x 26 x 16  </strong> </p>
<p align="center"> <strong>CONV2D_2 -> 26 x 26 x 16 || (3x3x16) x16 || 24 x 24 x 16   </strong> </p>
<p align="center"> <strong>CONV2D_3 -> 24 x 24 x 16 || (3x3x16) x32 || 22 x 22 x 32    </strong> </p>
<p align="center" >TRANSITION LAYER (Minimum Receptive for feature detection has reached)<p>
In Transition layers we are combining the simple features we have extracted in previous convolutions to make complex features/Textures/patterns
<p align="center"> <strong>22x22x32 || (1x1x32)x16 || 22x22x16 </strong> </p>
<p align="center" >Pooling Layer<p>
<p align="center"> <strong> Pool_1 -> 22 x 22 x 16 || MaxPool( 2x2 ) || 11 x 11 x 16</strong> </p>
<p align="center" >CONVOLUTION BLOCK 2<p>
<p align="center"> <strong> 11 x 11 x 16 || (3 x 3 x 16) x 16 || 9 x 9 x 16 </strong> </p>
<p align="center" >Layer with padding 1 <p>
<p align="center"> <strong> 9 x 9 x 16 || (3 x 3 x 16) x 16 || 9 x 9 x 16  </strong> </p>
<p align="center"> <strong> 9 x 9 x 16 || (3 x 3 x 16) x 16 || 7 x 7 x 16</strong> </p>
<p align="center"> <strong> 7 x 7 x16 || (3 x 3 x 16) x 32 || 5 x 5 x 32</strong> </p>
<p align="center" >Final Block <p>
<p align="center"> <strong> 5 x 5 x 32 || (1 x 1  x 32) x 10 || 5 x 5 x 10 </strong> </p>
<p align="center">  Global averge Pooling </p>
<p align="center"> <strong> Output = 1 x 1 x 10 </strong> </p>

### Data Augmentation
- The input images were randomly rotated by 10 degress to introduce slightly more variance and have the model generalize better.

      transforms.RandomRotation(10)

- Input data was also normalized with the mean and standard deviation of the input dataset.

      transforms.Normalize((0.1307,), (0.3081,))
      

      
### Conclusion
The model has achieved 99.4% accuracy with less than 20K parameters and well within 20 epochs by the help of Batch Normalization, Drop out and Global Averge Pooling.
