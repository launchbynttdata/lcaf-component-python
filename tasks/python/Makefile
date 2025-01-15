.PHONY: python/venv
python/venv:
	uv venv

.PHONY: python/build
python/build:
	uv build

lint::
	uvx ruff check

test::
	pytest
