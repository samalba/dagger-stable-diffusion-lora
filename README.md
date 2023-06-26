# 🌸 Fine-tuning Stable Diffusion using [LoRA](https://github.com/cloneofsimo/lora) with Dagger

A Stable Diffusion LoRA pipeline using [Dagger](https://dagger.io): pipelines as (python) code

* Go to [lambdalabs.com](https://lambdalabs.com), or any other GPU provider of your choice (the instructions below were tested on Lambda)
* Get an instance (e.g. A100 or A10). Min GPU memory is 16GB, tested on 24GB
* Hit up Jupyter (or SSH in, but Jupyter makes viewing the outputs easier :-))

## 🐋 New terminal, add user to docker group

```
sudo adduser ubuntu docker
```
```
sudo su - ubuntu
```

## 🐍 Install newer Python

```
sudo add-apt-repository ppa:deadsnakes/ppa
```
Press enter to install the PPA.

```
sudo apt install -y socat python3.10-venv
```
```
python3.10 -m virtualenv venv
```
```
. venv/bin/activate
```
```
curl -sS https://bootstrap.pypa.io/get-pip.py | python3.10
```

## 🚀 Install Dagger CLI

```
( cd /usr/local ; curl -L https://dl.dagger.io/dagger/install.sh | sudo sh )
```

## ⚙️ Check out repo and configure it

```
git clone https://github.com/lukemarsden/dagger-stable-diffusion-lora
```
```
cd dagger-stable-diffusion-lora
```

```
pip install -r requirements.txt
```
```
cp config.yml.sample config.yml
```

Now open config.yml in the Jupyter editor and change anything you like.

## 🚂 Train some LoRAs!

```
dagger run python lora.py
```

Now go and have lunch while you train some LoRAs :-)

...

Welcome back, check out outputs/inferences to see the results!

# 🏃 Observe the dagger cache making things faster

Now uncomment some of the prompts or brands in the config.yml and re-run, note how the Dagger cache saves you from having to redo any work that it's already done!

# 💸 Remember to shut down your GPU if you like keeping your money!
