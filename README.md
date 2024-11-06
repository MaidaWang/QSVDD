# PyTorch Implementation of Quantum SVDD
This repository provides a [PyTorch](https://pytorch.org/) implementation of the *Quantum SVDD* method presented in our 2024 paper ”A Practical Quantum Anomaly Detection Method with Enhanced Expressivity on Quantum Processors”.


## Citation and Contact
You find a PDF of the A Practical Quantum Anomaly Detection Method with Enhanced Expressivity on Quantum Processors paper at 
[http://].

If you use our work, please also cite the paper:
```

```

If you would like to get in touch, please contact [maida.wang.24@ucl.ac.uk](mailto:maida.wang.24@ucl.ac.uk).


## Abstract
Quantum computing has gained attention for its potential to address computational challenges. 
Its integration with emerging computing paradigms has contributed to quantum machine learning development. 
However, whether algorithms for real-world tasks can effectively operate on current quantum hardware, exhibiting quantum advantage, remains a critical question in quantum machine learning. 
In this work, we propose Quantum Support Vector Data Description (QSVDD) for practical anomaly detection. 
We introduce the concept of expressivity in our theoretical analysis, deriving a covering number bound to characterize the model's performance. 
Simulation results indicate that QSVDD demonstrates favorable recognition capabilities compared to classical baselines, 
achieving an average accuracy of over 90\% on benchmarks using ten qubits with significantly fewer trainable parameters. 
Furthermore, we first develop an implementation pipeline for QSVDD and conduct experiments on quantum processors, 
achieving an accuracy above 80\% with four qubits. 
This work aims to advance the application of quantum machine learning in anomaly detection, 
highlighting its feasibility in the noisy intermediate-scale quantum era.


## Installation
This code is written in `Python 3.8` and requires the packages listed in `requirements.txt`.

Clone the repository to your local machine and directory of choice:
```
git clone https://github.com/MaidaWang/QSVDD.git
```

To run the code, we recommend setting up a virtual environment, e.g. using `virtualenv` or `conda`:

### `virtualenv`
```
# pip install virtualenv
cd <path-to-Quantum-SVDD-directory>
virtualenv myenv
source myenv/bin/activate
pip install -r requirements.txt
```

### `conda`
```
cd <path-to-Quantum-SVDD-directory>
conda create --name myenv
source activate myenv
while read requirement; do conda install -n myenv --yes $requirement; done < requirements.txt
```


## Running simulations

We currently have implemented the MNIST ([http://yann.lecun.com/exdb/mnist/](http://yann.lecun.com/exdb/mnist/)) and 
CIFAR-10 ([https://www.cs.toronto.edu/~kriz/cifar.html](https://www.cs.toronto.edu/~kriz/cifar.html)) datasets and 
FashionMNIST datasets.

Have a look into `main.py` for all possible arguments and options.

### MNIST example
```
cd <path-to-Quantum-SVDD-directory>

# activate virtual environment
source myenv/bin/activate  # or 'source activate myenv' for conda

# create folder for experimental output
mkdir log/mnist_test

# change to source directory
cd src

# run simulation
python main.py mnist mnist_LeNet ../log/mnist_test ../data --objective one-class --lr 0.0001 --n_epochs 150 --lr_milestone 50 --batch_size 200 --weight_decay 0.5e-6 --pretrain True --ae_lr 0.0001 --ae_n_epochs 150 --ae_lr_milestone 50 --ae_batch_size 200 --ae_weight_decay 0.5e-3 --normal_class 1;
```
This example trains a Quantum SVDD model where digit 3 (`--normal_class 3`) is considered to be the normal class. Autoencoder
pretraining is used for parameter initialization.

### CIFAR-10 example
```
cd <path-to-Quantum-SVDD-directory>

# activate virtual environment
source myenv/bin/activate  # or 'source activate myenv' for conda

# create folder for experimental output
mkdir log/cifar10_test

# change to source directory
cd src

# run simulation
python main.py cifar10 cifar10_LeNet ../log/cifar10_test ../data --objective one-class --lr 0.0001 --n_epochs 150 --lr_milestone 50 --batch_size 200 --weight_decay 0.5e-6 --pretrain True --ae_lr 0.0001 --ae_n_epochs 350 --ae_lr_milestone 250 --ae_batch_size 200 --ae_weight_decay 0.5e-6 --normal_class 3;
```
This example trains a Quantum SVDD model where cats (`--normal_class 3`) are considered to be the normal class. 
Autoencoder pretraining is used for parameter initialization.

## Experiments
We have already run QSVDD on several different quantum devices, including IBM, Zuchongzhi, and VQS. We also plan to implement this method on more chips in the future.
Nevertheless, it is not possible to provide any specific codes for the hardware until such time as the relevant parties have given their approval.
If any academic organization has hardware and would like to run the algorithm on their hardware, they can contact the authors.


## License
UCL
