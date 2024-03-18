.PHONY: python/venv
python/venv: .venv/touchfile

.venv/touchfile:
	test -d .venv || python3 -m venv .venv
	source .venv/bin/activate; pip install -q -r requirements.txt || pip install -q .
	touch .venv/touchfile

.PHONY: python/test/requirements
python/test/requirements: python/venv
	@if [ -f requirements.txt ]; then \
		echo "Installing from requirements.txt"; \
		pip install -q -r requirements.txt; \
	fi
	@if [ -f requirements_test.txt ]; then \
		echo "Installing from requirements_test.txt"; \
		pip install -q -r requirements_test.txt; \
	fi

.PHONY: python/test
python/test: python/test/requirements python/test/unit

.PHONY: python/test/full
test/full: python/test/unit python/test/integration

.PHONY: python/test/unit
python/test/unit: python/test/requirements
	@if [ -d test/unit ]; then \
		echo "Running unit tests"; \
		pytest test/unit -ra -vv; \
	fi

.PHONY: python/test/integration
python/test/integration: python/test/requirements
	@-$(MAKE) python/test/integration/setup;
	@if [ -d test/integration ]; then \
		echo "Running integration tests"; \
		pytest test/integration --tb=no -v; \
	fi
	@-$(MAKE) python/test/integration/teardown;

.PHONY: python/clean
python/clean:
	@rm -fr .pytest_cache
	@rm -f .venv/touchfile
