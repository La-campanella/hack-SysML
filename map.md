## Papers
### Parallelism
#### Pipeline Parallelism
[PipeDream: Generalized Pipeline Parallelism for DNN Training](https://cs.stanford.edu/~matei/papers/2019/sosp_pipedream.pdf)(SOSP'19)

[Source Code](https://github.com/msr-fiddle/pipedream)

#### Parallelization Strategies
[Beyond Data and Model Parallelism for Deep Neural Networks](https://arxiv.org/pdf/1807.05358.pdf)
> Defined a more comprehensive search space of parallelization strategies for DNNs called SOAP, which includes strategies to parallelize a DNN in the Sample, Operation, Attribute, and Parameter dimesions. Proposed FlexFlow, a deep learning framework that uses guided randomized search of the SOAP spaceto find a fast parallelization strategy for a specific parallel machine. To accelerate this search, FlexFlow introduces a novel execution simulator that can accurately predict a parallelizaiton strategy's performance.

### Network
[GradientFlow: Optimizing Network Performance for Distributed DNN Training on GPU Clusters](https://arxiv.org/pdf/1902.06855.pdf)(cs.DC 2019)

> Proposed a communication backend named GradientFlow for distributed DNN training. First we integrate ring-based all-reduce, mixed-precision training, and computation/communication overlap. Second, we propose lazy allreduce to improve network throughput by fusing multiple communication operations into a singe one, and design coarse-grained sparse communication to reduce network traffic by transmitting important gradient chunks.

### Resource Management

[Optimus on top of K8s](https://i.cs.hku.hk/~cwu/papers/yhpeng-eurosys18.pdf)

### Parameter Server
[Scaling Distributed Machine Learning with the Parameter Server](https://www.cs.cmu.edu/~muli/file/parameter_server_osdi14.pdf)(2013?)

## Course：
###  [CS231n: Convolutional Neural Networks for Visual Recognition](http://cs231n.stanford.edu/)
>  This course is a deep dive into the details of deep learning architectures with a focus on learning end-to-end models for these tasks, particularly image classification. During the 10-week course, students will learn to implement and train their own neural networks and gain a detailed understanding of cutting-edge research in computer vision. Additionally, the final assignment will give them the opportunity to train and apply multi-million parameter networks on real-world vision problems of their choice. Through multiple hands-on assignments and the final course project, students will acquire the toolset for setting up deep learning tasks and practical engineering tricks for training and fine-tuning deep neural networks.
> 

### [CSE 599W: Systems for ML](http://dlsys.cs.washington.edu/schedule)
> System aspect of deep learning: faster training, efficient serving, lower
memory consumption

有不少结合TVM的部分，比如 Memory Optimization, Parallel Scheduing, 其中我感兴趣的部分：

#### [Introduction to Deep Learning](http://dlsys.cs.washington.edu/pdf/lecture1.pdf)
##### Evolution of ConvNets:

LeNet(1998)
Alexnet(2012)
GoogleLeNet(2014): Multi-indepent pass way (Sparse weight matrix)

Inception BN (2015): Batch normalization

Residual Net(2015): Residual pass way

Convolution = Spatial Locality + Sharing

ReLU: y = max(x, 0). 

Why ReLU?

* Cheap to compute
* It is roughly linear

Dropout Regularization: Randomly zero out neurons with probability 0.5

Why Dropout? Overfitting prevention.

Batch Normalization: Stabilize the Magnitude.

* Subtract mean
* Divide by standard deviation
* Output is invariant to input scale!
  - Scale input by a constant
  - Output of BN remains the same


Impact:
* Easy to tune learning rate . ?
* Less sensitive initialization. ?

#### [Lecture 1：Distributed Training and Communication Protocols](http://dlsys.cs.washington.edu/pdf/lecture11.pdf)

#### [Lecture 3: Overview of Deep Learning System](http://dlsys.cs.washington.edu/pdf/lecture3.pdf)
Computational Graph Optimization and Execution

Runtime Parallel Scheduing / Networks


#### [Lecture 5: GPU Programming](http://dlsys.cs.washington.edu/pdf/lecture5.pdf)

### https://ucbrise.github.io/cs294-ai-sys-sp19/
[AI-Sys Spring 2019](https://ucbrise.github.io/cs294-ai-sys-sp19/)(UC Berkeley)

## Books：

### Deep Learning
[Deep Learning](https://www.deeplearningbook.org/): Ian Goodfellow and Yoshua Bengio and Aron Courville
> intended to help students and practitioners enter the field of machine learning in general and deep learning in particular. The online version of the book is now complete and will remain available online for free.

## OpenSource Frameworks
### [Weld](https://www.weld.rs/)(Standford)
Fast rust parallel code generation for data analytics frameworks. Developed at Standford University.
> Weld is a language and runtime for improving the performance of data-intensive applications. It optimizes across libraries and functions by expressing the core computations in libraries using a common intermediate repersentation, and optimizing across each framwork.
> Modern analytics applications combine multiple functions from different libraries and frameworks to build complex workflows.
> Weld's take on solving this problem is to lazily build up a computation for the entire workflow, and then optimizingn and evaluating it only when a result is needed.
 
看起来就是解决掉用不同的库和框架来构建复杂工作流时的效率问题。通过引入一层中间表达，然后再实现到不同的框架里来做联合优化。

Paper: [Weld: Rethinking the Interface Between Data-Intensive Applications.](https://arxiv.org/abs/1709.06416)
> To address this problem, we propose Weld, a new interface between data-intensive libraries that can optimize across disjoint libraries and functions. Weld can be integrated into existing frameworks such as Spark, TensorFlow, Pandas and NumPy without chaning their user-facing APIs.

Related research papers: [PipeDream: General Pipeline Parallelism for DNN Training](https://cs.stanford.edu/~matei/papers/2019/sosp_pipedream.pdf) (SOSP'19)

### Table Data Storage
[Reverb is an efficient and easy-to-use data storage and trasport system designed for machine learning research](https://github.com/deepmind/reverb)(DeepMind, 2021-4-22)

> Used an an experience replay system for distributed reinforcement learning algorithms
