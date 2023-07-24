# Instructions for setting up lab machines to run Tensorflow with GPUs

You will need to do this once for every different machine you use. E.g. if you log out and log back into the same machine with the same account, everything should still be there. If you change machines, it will not. 

1.  Sign in using your university username and password

2. Open “Zenworks” software. This has lots of packages IT have pre-authorised for us to install
 *  Search Cuda
 *  Install “Nvidia Cuda Toolkit 11.2”
 *  This will take about ~15-20 minutes
 *  Your computer screen will flash black temporarily when the install is complete

3. Whilst this is completing, you can follow the next steps

4. Install Anaconda Navigator 
 *  https://www.anaconda.com/
 *  Download and run the .exe file 

5. Launch Anaconda Navigator

6. Environments -> Create -> Make a new environment, give it a name

7. Click on the PLAY arrow next to your new environment and select "Run Terminal". This will open up a separate terminal window 

8. We need to install some packages

* ``pip install tensorflow``
* ``conda install jupyter``
* ``conda install cudnn --update-all``

## Testing

Launch a new terminal window **in your environment** as above

1. Run the Jupyter notebook (by executing the code ``jupyter notebook`` in the terminal) in this repo (``Test GPU.ipnb``) (Code- > Download as Zip) and run the code. If you can train the model in there, you're good to go!

2. ``nvidia-smi`` to launch the nvidia console. You should have CUDA 11.2 installed. When you are running code, the GPU usage should go up!

# Instructions for setting up lab machines to run PyTorch with GPUs

## Step 1: Install cuda
Go to the applications bar

Select and open ‘ZENworks Application’

* Search for ‘cuda’

* Double click on NVIDIA cuda_11.7 (the icon with the nvidia logo) to install on the lab machine (this may take about 20 mins)

## Step 2: Install anaconda

Navigate to https://www.anaconda.com/

* Download the installer for windows (should be on the main page)

* Run the installer on the machine once it has downloaded

## Step 3: Launch anaconda prompt

* Launch anaconda prompt (search for it in taskbar)

* Create new environment with instructions here: https://git.arts.ac.uk/tbroad/AI-4-Media-22-23/blob/main/setup%20instructions/Setup-Conda-Enviroment.md

* In your environment follow next steps 4a or 4b

## Step 4a: Install tensorflow

* In your conda environment run: python -m pip install "tensorflow<2.11" --user

* To verify the install run: python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"

## Step 4b: Install PyTorch

* In your conda environment run: pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117 --user

* To verify the install run: python -c 'import torch; print(torch.cuda.is_available())'

## Step 5: Run your code!

* Download the code onto your machine from github or elsewhere, you should then be able to run it using your the GPU in the machine. Tensorflow should(?) do this automatically (though you may want to verify this). In PyTorch you will need to move you data and your neural network model to the device ‘cuda’.

## Step 6: Verify it is actually using the GPU

* In a different command prompt run: nvidia-smi

* This will show you how much GPU memory is currently being used. If you run it before you run the code and after you should see a significant increase!
