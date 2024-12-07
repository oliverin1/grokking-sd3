# Grokking Stable Diffusion 3

This repository contains code for running inference with Stable Diffusion 3 medium without using the StableDiffusion3Pipeline by separating the stages of prompt embedding, latent generation, and decoding from each other. It is meant to prioritize being transparent and easy to experiment on, as calling the original pipeline puts a lot of control out of reach. All code is adapted from the StableDiffusion3Pipeline.

## Installation
Clone the repo and install requirements in a virtualenv
```bash
pip install -r requirements.txt
```

## Usage
1. Run all cells in get_emb.ipynb with is_pos_prompt=False to generate the negative prompt embedding. This will save the embedding to neg_emb.pt by default.
2. Restart kernel and repeat with is_pos_prompt=True to generate the final prompt embedding. This will save the embedding to final_emb.pt.
3. Run all cells in generate_img.ipynb and the image will be displayed.

It is recommended to have a GPU with at least 12 GB VRAM. The scripts were configured to load T5 in 8 bit while keeping everything else in original float16 precision, but everything can be adjusted individually in order to fit smaller GPUs or run more efficiently on larger GPUs.
