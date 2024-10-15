#python #utils

### Установка
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

### Autocompition
```bash 
mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry
```
Добавить в плагины `.zshrc`:
```bash
plugins(
	poetry
	...
	)
```


### Usage
#### project init
```bash
poetry new poetry-demo
```

#### Initialising a pre-existing project
```bash
cd pre-existing-project
poetry init
```

#### Add dependencie
```bash
poetry add pendulum
```

#### Poetry run
To run your script simply use `poetry run python your_script.py`. Likewise if you have command line tools such as `pytest` or `black` you can run them using `poetry run pytest`.

If managing your own virtual environment externally, you do not need to use `poetry run` or `poetry shell` since you will, presumably, already have activated that virtual environment and made available the correct python instance. For example, these commands should output the same python path:

```shell
conda activate your_env_name
which python
poetry run which python
poetry shell
which python
```

#### Dependencies installation
```bash
poetry install
```