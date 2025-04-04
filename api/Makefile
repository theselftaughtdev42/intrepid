install:
	mkdir -p logs
	uv sync
	uv run playwright install
	uv run playwright install-deps

deploy:
	TODO

clean:
	find . -name '*.pyc' -delete
	find . -name '__pycache__' -delete
	rm -rf .coverage

deep-clean: clean
	rm -rf logs/*
	rm -rf htmlcov
	rm -rf intrepid.db

test-cov:
	uv run pytest --cov --cov-report=html .

QA:
	uv run pytest .
	uv run mypy .
	uv run ruff check .

api:
	uv run uvicorn run_api:app --reload

scraper:
	uv run run_scraper.py