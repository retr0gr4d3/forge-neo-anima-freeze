<h1 align="center">SD WebUI Forge - Neo - Anima Release Freeze</h1>

<p align="center"><sup>
[ You are on the Neo branch. Click Retro to switch. ]<br>[ Neo | <a href="https://github.com/retr0gr4d3/forge-neo-anima-freeze/tree/retro#forge-neo-anima-freeze---retro">Retro</a> ]
<br>

<p align="center"><img src="html\ui.webp" width=512 alt="UI"></p>


<blockquote><i>
<b>"Neo"</b> mainly serves as an continuation for the `latest` version of Forge, which was built on <a href="https://github.com/gradio-app/gradio">Gradio</a> `4.40.0` before lllyasviel became too busy... Additionally, this fork is focused on optimization and usability, with the main goal of being able to run the latest models without any bloatwares.<br>
<p align="right">- <b>Haoming02</b><br>
</i></blockquote>

My fork of "**Neo**" is a feature freeze of commit [7465c0e](https://github.com/Haoming02/sd-webui-forge-classic/commit/7465c0e9c2c2c1a093673ed8be3fc53049dd35a4), the addition of Anima. This branch will remain at the release of `2.13` as a baseline for any branches made within this repo. The main goal of this branch is to have a continually working environment without fear of config files being forcefully deleted by new features. The other branch of this repo is dedicated to my own customisations and preset configuration.

> [!Caution]
> A lot of the original information has been reworded or removed from this README. <br>
> Check upstream for a complete breakdown of features.

## Features

<details>
<summary>Click here for an overview of features as of Feb. 2026</summary>

<br>

> Most base features of the original [Automatic1111 Webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) should still function
#### New Features

- [X] Support [Anima](https://huggingface.co/circlestone-labs/Anima)
- [X] Support [Flux.2-Klein](https://huggingface.co/black-forest-labs/FLUX.2-klein-4B)
- [X] Support [Z-Image](https://huggingface.co/Tongyi-MAI/Z-Image)
- [X] Support [Wan 2.2](https://github.com/Wan-Video/Wan2.2)
- [X] Support [Qwen-Image](https://huggingface.co/Qwen/Qwen-Image) / [Qwen-Image-Edit](https://huggingface.co/Qwen/Qwen-Image-Edit-2509)
- [X] Support [Flux Kontext](https://huggingface.co/black-forest-labs/FLUX.1-Kontext-dev)
- [X] Support Multi-Image Inputs for **Qwen-Image-Edit** and **Flux-Kontext**
- [X] Support [Nunchaku](https://github.com/nunchaku-tech/nunchaku) (`SVDQ`) Models
- [X] Support [Lumina-Image-2.0](https://huggingface.co/Alpha-VLLM/Lumina-Image-2.0)
- [X] Support [Chroma1-HD](https://huggingface.co/lodestones/Chroma1-HD)
- [X] Support [uv](https://github.com/astral-sh/uv) package manager
- [X] Support [SageAttention](https://github.com/thu-ml/SageAttention), [FlashAttention](https://github.com/Dao-AILab/flash-attention), `fp16_accumulation`, `torch._scaled_mm`
- [X] Support loading upscalers in `half` precision
- [X] Support running tile composition on GPU
- [X] Support `.avif`, `.heif`, and `.jxl` image formats
- [X] Implement Triton Kernel for `matmul` in `torch.int8`
- [X] Implement Seed Variance Enhancer
- [X] Implement RescaleCFG
- [X] Implement MaHiRo
- [X] Implement [Epsilon Scaling](https://github.com/comfyanonymous/ComfyUI/pull/10132)
- [X] Rewrite Preset System
- [X] Update `spandrel`

#### Removed Features

- [X] SD2
- [X] SD3
- [X] Forge Spaces
- [X] Hypernetworks
- [X] CLIP Interrogator
- [X] Deepbooru Interrogator
- [X] Textual Inversion Training
- [X] Most built-in Extensions
- [X] Some built-in Scripts
- [X] Some Samplers
- [X] Sampler in RadioGroup
- [X] Unix `.sh` launch scripts

#### Optimizations

- [X] **[Comfy]** Rewrite the Backend *(`memory_management.py`, `ModelPatcher`, `attention.py`, etc.)*
- [X] No longer `git` `clone` any repository on fresh install
- [X] Fix memory leak when switching checkpoints
- [X] Speed up launch time
- [X] Improve timer logs
- [X] Remove unused `cmd_args`
- [X] Remove unused `args_parser`
- [X] Remove unused `shared_options`
- [X] Remove legacy codes
- [X] Fix some typos
- [X] Fix automatic `Tiled VAE` fallback
- [X] Pad conditioning for SDXL
- [X] Remove redundant upscaler codes
- [X] Improve `ForgeCanvas`
- [X] Optimize upscaler logics
- [X] Optimize certain operations in `Spandrel`
- [X] Speed up model loading
- [X] Improve memory management
- [X] Improve color correction
- [X] Update the implementation for `MultiDiffusion`
- [X] Update the implementation for `uni_pc` and `LCM` samplers
- [X] Update the implementation of LoRAs
- [X] Revamp settings
- [X] Check for Extension updates in parallel
- [X] Move `embeddings` folder into `models` folder
- [X] ControlNet Rewrite
- [X] Disable Refiner by default
- [X] No longer install `bitsandbytes` by default
- [X] Lint & Format
- [X] Update `Pillow`
- [X] Update `protobuf`
- [X] Update to latest PyTorch
- [X] No longer install `open-clip` twice
- [X] Update some packages to newer versions
- [X] Update recommended Python to `3.13.12`
- [X] Many more... :tm:
</details>

## Commandline

<details>
<summary>Click here for commandline arguments</summary>

<br>

> These flags can be added after the `set COMMANDLINE_ARGS=` line in the `webui-user.bat` *(separate each flag with space)*
> Use `python launch.py --help` to see all available flags

- `--xformers`: Install the `xformers` package to speed up generation

- `--port`: Specify a server port to use. Defaults to `7860`

- `--api`: Enable [API](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/API) access

- Add `--cuda-malloc`, `--cuda-stream`, `--pin-shared-memory` to slightly improve the model loading; in certain situations, they may cause `OutOfMemory` errors instead...

- `--uv`: Replace the `python -m pip` calls with `uv pip` to massively speed up package installation. Requires **uv** to be installed

- `--uv-symlink`: Same as above; but additionally pass `--link-mode symlink` to the commands. Significantly reduces installation size (`~7 GB` to `~100 MB`). Using `symlink` means it will directly access the packages from the cache folders; refrain from clearing the cache when setting this option

- `--model-ref`: Points to a central `models` folder that contains all your models. Said folder should contain subfolders like `Stable-diffusion`, `Lora`, `VAE`, `ESRGAN`, etc. This simply **replaces** the `models` folder, rather than adding on top of it

- `--forge-ref-a1111-home`: Point to an Automatic1111 installation to load its `models` folders **i.e.** `Stable-diffusion`, `text_encoder`, etc.

- `--forge-ref-comfy-home`: Point to a ComfyUI installation to load its `models` folders **i.e.** `diffusion_models`, `clip`, etc.

- `--forge-ref-comfy-yaml`: Point to the ComfyUI `extra_model_paths.yaml` to load its configurations **i.e.** `base_path`, `checkpoints`, etc.

- `--sage`: Install the `sageattention` package to speed up generation, this will also attempt to install `triton` automatically

- `--flash`: Install the `flash_attn` package to speed up generation

- `--nunchaku`: Install the `nunchaku` package to inference SVDQ models

- `--bnb`: Install the `bitsandbytes` package to do low-bits (`nf4`) inference

- `--onnxruntime-gpu`: Install the `onnxruntime` with the latest GPU support

- `--fast-fp8`: Use the `torch._scaled_mm` function when the model type is `float8_e4m3fn`

- `--fast-fp16`: Enable the `allow_fp16_accumulation` option

- `--autotune`: Enable the `torch.backends.cudnn.benchmark` option, although this can be slow

</details>

## Installation

<details>
    <summary>Instructions for those who need them</summary>

<br>

1. Install **[git](https://git-scm.com/downloads)**
2. Clone the Repo
3. Setup the environment using **only one** of these two methods:

<details>
<summary>3a. Using UV</summary>

- Install **[uv](https://github.com/astral-sh/uv#installation)**
- Set up **venv**
    ```bash
    cd sd-webui-forge-neo
    uv venv venv --python 3.13 --seed
    ```
- Add the `--uv` flag to `webui-user.bat`

</details>
<details>
<summary>3b. Install Python [deprecated method]</summary>

- Get **[Python 3.13.12](https://www.python.org/downloads/release/python-31312/)**
    - Remember to enable `Add Python to PATH`

</details>

4. **(Optional)** Configure [Commandline](#commandline)
5. **(Optional)** Check out [Extra Installations](https://github.com/Haoming02/sd-webui-forge-classic/wiki/Extra-Installations) in Haoming02's wiki for how to install `git`, `uv`, and `FFmpeg`.
6. Launch the WebUI via `webui-user.bat`
7. During the first launch, it will automatically install all the requirements
8. Once the installation is finished, the WebUI will start in a browser automatically

</details>

## Attention Functions

> [!Caution]
> Nowadays the native PyTorch `scaled_dot_product_attention` is usually as fast, and also more stable.

<details>
    <summary>Commandline options</summary>

<br>

> Do **not** just blindly install all of these.
> The `--xformers`, `--flash`, and `--sage` args are only responsible for installing the packages, **not** whether its respective attention is used *(this also means you can remove them once the packages are successfully installed)*. To skip a specific attention, add the respective disable arg such as `--disable-sage`. **Forge Neo** tries to import the packages and automatically choose the first available attention function in the following order:
1. `SageAttention`
2. `FlashAttention`
3. `xformers`
4. `PyTorch`
5. `Basic`


</details>

## Regarding Issues

> [!Tip]
> Please try and install a fresh installation from Haoming02's original repo if you encounter errors. <br>
> Check out the [Wiki](https://github.com/Haoming02/sd-webui-forge-classic/wiki) that Haoming02 provides as it may contain the solution to your problem.

<hr>

<p align="center">
Special thanks to: <b>AUTOMATIC1111</b>, <b>lllyasviel</b>, <b>comfyanonymous</b>, <b>kijai</b>, <b>city96</b> and <b>Haoming02</b> <br>
along with the rest of the contributors <br>
for their invaluable efforts in the open-source image generation community.
</p>
