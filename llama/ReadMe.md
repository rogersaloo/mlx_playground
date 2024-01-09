## Description 

## Need to change the architectuire to the arm architecture in order to run on the mlx on Apple silicon. `CONDA_SUBDIR=osx-arm64 conda create -n AppleMLX python=3.11`

## Instalation
1. install the environment with the arm architecture `CONDA_SUBDIR=osx-arm64 conda create -n AppleMLX python=3.11`
2. activate the environment `conda activate AppleMLX`
3. Install tranformers `pip install transformers`
4. Next, download and convert the model. If you do not have access to the model weights you will need to request access from Meta:
    - Request Llama v1
    - Request Llama v2
[!TIP] Alternatively, you can also download a few converted checkpoints from the [MLX Community](https://huggingface.co/mlx-community) organization on Hugging Face and skip the conversion step.
You can download the [TinyLlama](https://huggingface.co/TinyLlama/TinyLlama-1.1B-Chat-v1.0) models directly from Hugging Face.


- Convert the weights with:
`python convert.py --torch-path <path_to_torch_model>`


- To generate a 4-bit quantized model use the -q flag:
`python convert.py --torch-path <path_to_torch_model> -q`

For TinyLlama use
`python convert.py --torch-path <path_to_torch_model> --model-name tiny_llama`
By default, the conversion script will make the directory mlx_model and save the converted weights.npz, tokenizer.model, and config.json there.


