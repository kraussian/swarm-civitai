# Swarm-CivitAI

## Summary

Convert metadata from [SwarmUI](https://github.com/mcmonkeyprojects/SwarmUI) for automatic recognition when uploading to [CivitAI](https://civitai.com)

## Background

[SwarmUI](https://github.com/mcmonkeyprojects/SwarmUI) looks like the only way to use local [Flux](https://github.com/black-forest-labs/flux) at the moment, but of course CivitAI only recognizes image formats created with [Automatic1111 WebUI](https://github.com/AUTOMATIC1111/stable-diffusion-webui).  
So to force CivitAI to recognize metadata from images generated with SwarmUI, I've written a script to convert SwarmUI metadata format to Automatic1111 format.

## How to Use

### Prerequisites

* Python (ideally v3.10 and above)
* SwarmUI (of course)

### Step: Setup config file to point to model folders

1. Open `SwarmUI_cfg.json` in a text editor
2. Change the values of `model_folder` and `unet_model_folder` to the actual locations on your PC where these model files are stored
**NOTE** SwarmUI doesn't look for FLUX models in the same folder as Stable Diffusion checkpoints. They're expected to be in the `unet` folder instead
**!! IMPORTANT !!** Change any backslashes (`\`) to forward slashes (`/`) when entering the model paths

For example, let's say your Stable Diffusion checkpoint models are stored in `C:\sd\models\Stable-Diffusion`, FLUX models in `C:\sd\models\unet`, VAE models in `C:\sd\models\VAE` and LoRA models in `C:\sd\models\Lora`.  
Then change the `SwarmUI_cfg.json` file like so:

```json
{
    "model_folder": "C:/sd/models/Stable-Diffusion",
    "unet_model_folder": "C:/sd/models/unet",
    "vae_folder": "C:/sd/models/VAE",
    "lora_folder": "C:/sd/models/Lora"
}
```

### Usage Instructions

1. Download the latest release, and unzip to a new folder
2. Drag & Drop the images you want to convert to the `converter.bat` file
3. That's it! The converted images will be saved in the same folder as the original, with `_a1111` appended to the file name

Now you can upload the converted images to Civitai, and all parameters and models (including LoRAs) used by the image will automagically be filled in by Civitai upon upload.
