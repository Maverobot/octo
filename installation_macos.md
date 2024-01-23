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
```bash
pip install --upgrade jax-macos
```
