.PHONY: python/venv
python/venv:
	@uv venv

.PHONY: python/build
python/build:
	@uv build

.PHONY: lint
lint::
	@uvx ruff check

.PHONY: test
test::
	@uv run pytest

.PHONY: coverage
coverage::
	@-uv run pytest
	@open -a "Google Chrome" htmlcov/index.html
