<h3>Image Recognition using a Multilayer Perceptron Neural Network with the Back-Propagation Algorithm</h3>
<hr>
This program is a web application written in Go that makes extensive use of the html/template package.
Navigate to the C:\Users\your-name\ImageMLP\src\backprop\ directory and issue "go run imagemlp.go" to
start the Multilayer Perceptron (MLP) Neural Network server. In a web browser enter http://127.0.0.1:8080/imageMLP
in the address bar.  There are two phases of operation:  the training phase and the testing phase.  During the training
phase, examples consisting of images and the desired class are supplied to the network.  The images
are 256x256 pixel PNG image files that are converted to Go image structures and flattened to a slice.
The network itself is a directed graph consisting of an input layer of nodes, one or more hidden layers of nodes, and
an output layer of nodes.  Each layer of nodes can be arbitrarily deep.  The nodes of the network are connected by weighted
links.  The network is fully connected.  This means that every node is connected to its immediately adjacent neighbor node.  The weights are trained
by first propagating the inputs forward, layer by layer, to the output layer of nodes.  The output layer of nodes finds the
difference between the desired and its output and back propagates the errors to the input layer.  The hidden and input layer
weights are assigned “credit” for the errors by using the chain rule of differential calculus.  Each neuron consists of a
linear combiner and an activation function.  This program uses the hyperbolic tangent function to serve as the activation function.
This function is non-linear and differentiable and limits its output to be between -1 and 1.  <b>The purpose of this program is to classify an
image</b>.
The user selects the MLP training parameters:
<li>Hidden Layers</li>
<li>Layer Depth</li>
<li>Learning Rate</li>
<li>Momentum</li>
<li>Epochs</li>
<br>
<p>
The <i>Learning Rate</i> and <i>Momentum</i> must be less than one.  Each <i>Epoch</i> consists of the number of <i>Training Examples</i>.  
One training example is a flattened signature image and the desired class (0, 1,…, 15).  There are 16 images and therefore 16 classes.
The images are a sequence of 65536 (256*256) 1 or -1 integers that represent the grayscale (black/white) representation of the image.
The 1 represents black and the -1 represents white.  The PNG image files were produced using Microsoft Paint3D.
</p>
<p>
When the <i>Submit</i> button on the MLP Training Parameters form is clicked, the weights in the network are trained
and the Learning Curve (mean-square error (MSE) vs epoch) is graphed.  As can be seen in the screen shots below, there is significant variance over the ensemble,
but it eventually settles down after about 30 epochs. An epoch is the forward and backward propagation of all the 16 training samples.
</p>
<p>
When the <i>Test</i> link is clicked, 64 examples are supplied to the MLP.  It classifies the images.
The test results are tabulated and the actual images are graphed from the flattened images that were supplied to the MLP.
It takes some trial-and-error with the MLP Training Parameters to reduce the MSE to zero.  It is possible to a specify a 
more complex MLP than necessary and not get good results.  For example, using more hidden layers, a greater layer depth,
or over training with more examples than necessary may be detrimental to the MLP.  Clicking the <i>Train</i> link starts a new training
phase and the MLP Training Parameters must be entered again.
</p>

<b>Image Recognition Learning Curve, MSE vs Epoch, 2 Hidden Layer2, Hidden Layer Depth = 15</b>
![image](https://github.com/thomasteplick/imageMLP/assets/117768679/d22e9cc5-6498-476c-97af-fa834b874eff)

<b>Image Recognition Test Results, 2 Hidden Layer2, Hidden Layer Depth = 15</b>
![image](https://github.com/thomasteplick/imageMLP/assets/117768679/b1ffa6c8-49db-4e5d-a749-e97eadb494dc)

![image](https://github.com/thomasteplick/imageMLP/assets/117768679/3b242a67-623a-40a5-ba8e-5624581abe0e)

![image](https://github.com/thomasteplick/imageMLP/assets/117768679/385039e1-eb25-4c66-9130-dd019b74cbbd)


