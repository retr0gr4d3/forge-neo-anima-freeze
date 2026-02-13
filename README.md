<h1 align="center">Forge Neo - Retro's Branch</h1>

<p align="center"><sup>
[ You are on Retro's branch. Click Neo to switch back to the original. ]<br>[ <a href="https://github.com/retr0gr4d3/forge-neo-anima-freeze/tree/neo#forge-neo-anima-freeze---neo">Neo</a> | Retro ]
<br>

<p align="center"><img src="html\ui.webp" width=512 alt="UI"></p>

<p align="center"><sup>
Personal branch of <b>"Neo"</b>, frozen on commit <a href="https://github.com/Haoming02/sd-webui-forge-classic/commit/7465c0e9c2c2c1a093673ed8be3fc53049dd35a4">7465c0e</a>.<br>
This branch is based on release 2.13 of Haoming02's Forge Neo. Dedicated to my own customisations and preset configurations.

<blockquote><i>
<b>"Neo"</b> mainly serves as an continuation for the `latest` version of Forge, which was built on <a href="https://github.com/gradio-app/gradio">Gradio</a> `4.40.0` before lllyasviel became too busy... Additionally, this fork is focused on optimization and usability, with the main goal of being able to run the latest models without any bloatwares.<br>
<p align="right">- <b>Haoming02</b><br>
</i></blockquote>

<hr>

<details>
<summary>[Features]</summary>

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
<details>
<summary>[Commandline Arguments]</summary>

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
<details>
    <summary>[Installation Methods]</summary>

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

> [!Tip]
> Did you know you can import this into Stability Matrix?

- Install following the UV method above
  - Ensure the python version you use matches one that is available in SM
  - At the time of writing, the latest `Python 3.13` in SM is `3.13.5`
- Move the folder for it into SM's Data/Packages/ directory
  - It will show up in SM as an "Unknown Package" with an import button
- Click the import button, then tell it:
  - What package it is
  - What commit version
  - What version of python the package was set up with

<hr>

Experiencing issues? Please try installing a fresh installation from Haoming02's original repo if you encounter errors. Check out the [Wiki](https://github.com/Haoming02/sd-webui-forge-classic/wiki) that Haoming02 provides as it may contain the solution to your problem.

<hr>

<p align="center">
Special thanks to: <b>AUTOMATIC1111</b>, <b>lllyasviel</b>, <b>comfyanonymous</b>, <b>kijai</b>, <b>city96</b> and <b>Haoming02</b> <br>
along with the rest of the contributors <br>
for their invaluable efforts in the open-source image generation community.
</p>
