# Installation in MacOS

First, install the required openexr library.

```sh
brew install openexr
```

Second, create the python environment and install the dependencies.

```sh
# If you still have problems with openexr, check the installed version of openexr and imath and change the paths accordingly.
export CFLAGS="-I/opt/homebrew/Cellar/openexr/3.2.1/include/OpenEXR -I/opt/homebrew/Cellar/imath/3.1.9/include/Imath -std=c++11"
export LDFLAGS="-L/opt/homebrew/Cellar/openexr/3.2.1/lib -L/opt/homebrew/Cellar/imath/3.1.9/lib"

conda create -n octo python=3.10
conda activate octo
pip install -e .
pip install -r requirements-macos.txt
```

For Apple Silicon,
```sh
pip install --upgrade jax-macos
```

Test the installation by finetuning on the debug dataset:
```sh
python scripts/finetune.py --config.pretrained_path=hf://rail-berkeley/octo-small --debug
```
On Apple M2 Ultra, the script runs at around 5 seconds per iteration. Because jax-metal only supports float32, the model is converted to float32 and takes up about 100 GB of memory. If you have less than 100 GB of memory, you can try to reduce the batch size by adding `--config.batch_size=4` to the command line.
