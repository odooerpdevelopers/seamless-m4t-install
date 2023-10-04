# seamless-m4t-install
Seamless M4T Linux installation Guide


## install debian libs

```
sudo apt update -y && sudo apt install git ffmpeg -y

```

## Prepare Conda Environment with Python 3.10

```
conda create -n mt4 python=3.10
conda activate mt4

```

## Download sources
```
git clone https://github.com/facebookresearch/seamless_communication
cd seamless_communication

```

## install requirements

```
pip install .
conda install -y -c conda-forge libsndfile
conda install -c conda-forge libsndfile==1.0.31

```

## launch App M4T Gui

```
cd demo
pip install -r requirements.txt
python app.py share=True

```
