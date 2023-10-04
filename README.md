# Seamless M4T for Linux
### Seamless M4T Linux installation Guide

This installation guide has been tested on Debian 12 Bookworm on a Lenovo Legyon 4 Core i7, 16GB RAM, SSD 1TB, Nvidia GTX 1055 3GB Laptop. 

It contains the fundamental steps to be able to launch the Meta Seamless M4T project, I encountered several problems along the way and that's why I developed this guide so that you can jump over the obstacles. 

## Things I found and didn't work for me: 

The Traductor model uses 2 models seamlessM4T_large (10GB), and seamlessm4T_medium (6GB)



The [seamlessM4T_large](https://github.com/facebookresearch/seamless_communication/blob/3d7e25d2b0d77ddef080f5152660956333a8c3cb/demo/app.py#L307) 
model doesn't work on my PC, it runs out of RAM LOL, so I modified this line to change and use the medium model, if you modify that line it should look like this:

```python
translator = Translator(
    model_name_or_card="seamlessM4T_medium",
    vocoder_name_or_card="vocoder_36langs",
    device=device,
    dtype=torch.float16 if "cuda" in device.type else torch.float32,
)
```

So, if the process ends and is not able to start the APP then you will have to change it before running the Gradio App, locate the line of code that I left you above and change it in your project (seamless_communication/demo/app.py)


## Recommended requirements

* **Nvidia Card with Drivers installed**
* Debian 12|11, Ubuntu 22.04
* [Miniconda 3](https://docs.conda.io/projects/miniconda/en/latest/index.html#quick-command-line-install)

* Computer >= 15GB RAM, Multi Core


## Start Process:
### install debian libs

```
sudo apt update -y && sudo apt install git ffmpeg -y

```

### Prepare Conda Environment with Python 3.10

```
conda create -n mt4 python=3.10
conda activate mt4

```

### Download sources
```
git clone https://github.com/facebookresearch/seamless_communication
cd seamless_communication

```

### install requirements

```
pip install .
conda install -y -c conda-forge libsndfile
conda install -c conda-forge libsndfile==1.0.31

```

### launch App M4T Gui

```
cd demo
pip install -r requirements.txt
python app.py share=True

```
