  - name: Set up Python
    uses: actions/setup-python@v5
    with:
      python-version: '3.11'

  - name: Install dependencies
    run: |
      python -m venv .venv
      source .venv/bin/activate
      pip install --upgrade pip
      pip install -r requirements.txt

  - name: Lint backend
    run: |
      source .venv/bin/activate
      pip install flake8
      flake8 app

  - name: Run FastAPI tests
    run: |
      source .venv/bin/activate
      # Uncomment if you have pytest/unit tests
      # pytest
