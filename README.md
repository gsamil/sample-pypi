# sample-pypi

- I created this repository to learn how to create a Python package and publish it to PyPI.

- This repository uses `poetry` to manage dependencies and packaging.

## `poetry` installation

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

## `poetry` usage

I assume you already have a project that you want to manage with `poetry`. First `cd` into the project directory.

### 1. initialize `poetry`

```bash
poetry init
```

This will create a `pyproject.toml` file in your project directory.

### 2. add dependencies

```bash
poetry add <dependency>
```

This will add the dependency to your `pyproject.toml` file and install it in your virtual environment.

### 3. install dependencies

```bash
poetry install
```

This will install all the dependencies listed in your `pyproject.toml` file and create a `poetry.lock` file. (You can commit this file to your repository to ensure that all developers use the same versions of the dependencies.)


## TODOs

- [ ] What is the advantage of using `poetry` over `requirements.txt`?
- [ ] How to use test pypi?
