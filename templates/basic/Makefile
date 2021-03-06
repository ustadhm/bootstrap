# =============================================================================
PROJECT_NAME:=project
.DEFAULT_GOAL:=help
.SILENT:
SHELL:=/usr/bin/bash


# =============================================================================
# 			DEV
# =============================================================================
#
VENV_DIR:=.venv
VENV_BIN:=.venv/bin/
ACTIVATE:=source .venv/bin/activate &&

.PHONY: help setup run lint format test build pre-commit coverage

help:
	echo "Python project\n"

setup:
	test -d $(VENV_DIR) || python3 -m venv $(VENV_DIR)
	poetry install
	$(VENV_BIN)pre-commit install

run:
	python $(PROJECT_NAME)

lint:
	flake8 --show-source .
	bandit -q -r -c "pyproject.toml" .

format:
	black .

test:
	pytest

build:
	poetry build -q

pre-commit:
	pre-commit run --all-files

clean:
	rm -rf $(VENV_DIR)
	find . -type d -name '__pycache__' -exec rm -rf {} +
# =============================================================================
