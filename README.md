# sample-pypi

- I created this repository to learn how to create a Python package and publish it to PyPI.

- This repository uses `poetry` to manage dependencies and packaging.


# poetry

## Get ready

These are the steps to get ready to use `poetry`.

### 1. virtual environment

⛔️ Poetry should always be installed in a dedicated virtual environment to isolate it from the rest of your system. In no case, it should be installed in the environment of the project that is to be managed by Poetry. This ensures that Poetry’s own dependencies will not be accidentally upgraded or uninstalled. (See [reference](https://python-poetry.org/docs/)).

Because of the above:

First we create a virtual environment:

```bash
python -m venv venv
```

Then we activate it:

```bash
source venv/bin/activate
```

### 2. install `pipx` if not installed

First check if you have `pipx` installed. If not, install it with `pip`:

```bash
pip install --user pipx
```

### 3. install `poetry`

Then install `poetry` with `pipx`:

```bash
pipx install poetry
```

If you want to use `poetry` as a command, you can add an alias to your `.bashrc` (or `.zshrc`).

This is what it looks like on my machine:

```bash
alias poetry='/Users/abdullahguser/Library/Application\ Support/pipx/venvs/poetry/bin/poetry'
```

## Use `poetry` to manage dependencies in an existing project

I assume you already have a project that you want to manage with `poetry`. First `cd` into the project directory.

### initialize `poetry`

```bash
poetry init
```

This will create a `pyproject.toml` file in your project directory.

### add dependencies

```bash
poetry add <dependency>
```

This will add the dependency to your `pyproject.toml` file and install it in your virtual environment.

### remove dependencies

```bash
poetry remove <dependency>
```

### install dependencies

```bash
poetry install
```

This will install all the dependencies listed in your `pyproject.toml` file and create a `poetry.lock` file. (You can commit this file to your repository to ensure that all developers use the same versions of the dependencies.)

## Use `poetry` to create a virtual environment for an existing project

If you clone a project that uses `poetry` for dependency management, you can create a virtual environment for it using poetry.

First, if you want this environment to be created under the project directory, set this config:

```bash
poetry config virtualenvs.in-project true
```

Now you can create a virtual environment for the project:

```bash
poetry install
```

This will create a virtual environment for the project and install all the dependencies listed in the `pyproject.toml` file.

If you want to use this new virtual environment, activate it:

```bash
poetry shell
```

To get out of the virtual environment, type `exit` or `deactivate`.

## Building and Publishing Packages with PyPi

First indicate where you want to publish your package:

```bash
poetry config repositories.test-pypi https://test.pypi.org/legacy/
```

Now you can go to this repository and get a token that allows you to publish packages to the repository. Set it in poetry:

```bash
poetry config pypi-token.test-pypi <token>
```

Now you can build your package:

```bash
poetry build
```

To publish your package:

```bash
poetry publish -r test-pypi
```

## Other commands

List virtual environments:

```bash
poetry env list
```

To remove a virtual environment, you can simply delete the directory that contains it.


## References

- [How to Create and Use Virtual Environments in Python With Poetry](https://youtu.be/0f3moPe_bhk)




## TODOs

- [ ] What is the advantage of using `poetry` over `requirements.txt`?
- [ ] How to use test pypi?
