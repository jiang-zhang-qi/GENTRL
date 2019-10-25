# Introduction
Here I have aimed to explain my understanding about the code in GENTRL and some minor steps for new users who want to run it or understand it.

It is originally forked from [this repo](https://github.com/insilicomedicine/GENTRL).

# Installation

## Step 1 :
Make a new conda environment and install RDKit.
```
conda create -c rdkit -n my-rdkit-env rdkit
```
Then activate this new environment.
```
conda activate my-rdkit-env
```
*Note :*  Make sure that the python3 version is 3.5 and higher and pip3 is installed

## Step 2 :
Inside this environment install GENTRL.
```
cd <Path_to_GENTRL_folder>
python3 setup.py install
```
*Note :* The `setup.py` doesn't install scikit-learn, so if you don't have it installed please install it using 
```
pip3 install scikit-learn

or

python3 -m pip install scikit-learn
```

## Step 3 : (Optional)
Installing MOSES is optional but if you want to run the examples given [here](https://github.com/Bibyutatsu/GENTRL/tree/master/examples) I would recommend you to install it.

**PyPi** (Recommended)
```
pip3 install molsets
```

**Using git repo**
```
git clone https://github.com/molecularsets/moses.git
cd moses
python3 setup.py install
```
*Note :* The moses depend on RDKit so please install it after Step 1.

## Step 4 : (Optional)
Making a new **Kernel** for jupyter notebook is recommended. For making a new kernel please follow these steps.
```
python3 -m pip install ipykernel
python3 -m ipykernel install --user --name rdkit_kernel
```
Now when you open jupyter notebook. Go to **Change Kernel** > **rdkit_kernel**

With these the installation is over and now we are ready to run the examples provided in the Repo.

# Explanation

## pretrain.ipynb
In this notebook the Variational Auto Encoder(VAE) is trained. It encodes the SMILES onto the latent space with a rich prior distribution. To put it simply, in this step the structural properties of each training molecule is transferred to a latent space, and process encodings of molecules are created. So, the model learns about the molecules structural properties and interrelation of structure and rewards.


## train_rl.ipynb
In this notebook the Reinforecement learning of the model takes place. In this step except the learnable prior all other parameters are kept constant and then the latent space is explored for new molecules with higher rewards. So in this step the model learns to generate better molecules on the basis of reward function.

## sampling.ipynb
In this notebook new molecules are generated in the form of SMILES. Using RDKit's Draw module a grid of images of these newly generated molecules is produced as shown below ([Link](https://github.com/Bibyutatsu/GENTRL/blob/master/images/Sampling_big.png) of the whole grid).

![Sampling](https://github.com/Bibyutatsu/GENTRL/blob/master/images/Sampling.jpeg)