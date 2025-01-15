.PHONY: python/venv
python/venv:
	uv venv

.PHONY: python/build
python/build:
	uv build

.PHONY: lint
lint::
	uvx ruff check

.PHONY: test
test::
	pytest

.PHONY: coverage
coverage:: test
	open -a "Google Chrome" htmlcov/index.html
