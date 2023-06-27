# Stable Diffusion Tutorial
A simple guide I made through the practical process of installing Stable Diffusion with AUTOMATIC1111 web-ui.

Note that this guide is not meant to be technical nor comprehensive, you can see this guide as a recap of the steps I took to install it.

**No shortcuts** 
Trying to cut through some steps or speedrun a YouTube guide probably made you end up here. Give guides a good read before starting. 

## What is the difference?
I do suggest to first try with other guides first! Especially the [official guide in the repository](https://github.com/AUTOMATIC1111/stable-diffusion-webui).

# Linux
I suggest Ubuntu just because it is easier to use, ignore the distro battle and use whatever you like.

You will be able to get a clean install without using the mouse once. 

### Dependencies
```
# Debian-based:
sudo apt install wget git python3 python3-venv
```
```
# Red Hat-based:
sudo dnf install wget git python3
```
```
# Arch-based:
sudo pacman -S wget git python3
```

**Suggested**:
- nano, edit text
- neofetch, look at specs

### Create a directory
`Ctrl+Alt+T` will open up the terminal, then navigate to the folder you want to install Stable Diffusion AUTOMATIC1111 webui in, and create a folder there.

`ls` will list what's inside the currect directory, so you will understand where you are.
`mkdir <directory name>` will create the folder.
`cd <directory name>` will mode you inside the folder.

### Clone repository
`bash <(wget -qO- https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh)`

### Options
`cd` inside the repository.
`nano webui-user.sh` to see all the options you can customize.
This will change based on your specific requirements and system, but with a 3060Ti and CUDA 11.8 I was able to make it work with this setup:
- COMMANDLINE_ARGS
  `export COMMANDLINE_ARGS="--xformers --port 7861"`
- TORCH_COMMAND
  `export TORCH_COMMAND="pip install torch==2.0.0+cu118 torchvision torchaudio transformers==4.25.1 --extra-index-url https://download.pytorch.org/whl/cu118"`
- NO_TCMALLOC
  `export NO_TCMALLOC="True"`

You should be able to find where to write these in the webui-user.sh file.

Ctrl+X to exit nano, y and enter to save. (follow visual instructions)

### Run
You will be back on the repository folder.
Now you can run the webui with:
`bash webui.sh`

The first run will be slow and probably painful.

### Check for NVIDIA drivers to use xformers and speed up image generation
- nvcc --version
- nvidia-smi

## Troubleshoot
It will hardly work on the first try, here are the delicate aspects:
- try removing the xformers flag
- try reinstalling NVIDIA drivers and CUDA
- try adjusting the TORCH_COMMAND to match the correct version for your drivers

If you find weird errors in the terminal while installing or launching, the only way to find a fast fix is to visit [GitHub Issues](https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues) and search for someone with a similar error.

With more than 3.5k issues closed, you will probably find an answer there.

I must include [reddit](https://www.reddit.com/r/StableDiffusion/?f=flair_name%3A%22Tutorial%20%7C%20Guide%22) as a middle ground for beginners to ask and read about similar errors.

Google search is nearly useless lately, but you can certainly try.

**Tip**
You likely need the first and/or last part of the error to troubleshoot.
1. Read all the error message and try to find some keywords
2. Try to search for a fix
3. Try to fix it yourself
4. Ask for a fix

I can't stress point 2 enough, it might seem counterintuitive but searching for an answer is faster than asking and waiting.

Most of the work resides here.

# Windows
Feel free to send the guide here. 

# Why keeping this separate?
Clutter and mostly nooby talk, I wanted to keep this a read-and-follow tutorial, diary-like, that might contain more details or just tips that would not fit in the main repository.

# Will this be up to date? (27 June 2023)
This guide will be updated when I get back working with a live version of AUTOMATIC1111.

I would be glad to accept any suggestion or addition to this guide as the project changes through time. 