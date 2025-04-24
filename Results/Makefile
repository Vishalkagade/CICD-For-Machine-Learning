.PHONY: install format train eval update-branch

install:
	@echo "Installing Python dependencies…" 
	pip3 install -r requirements.txt

format:
	@echo "Running Black…" 
	black *.py

train:
	@echo "Starting training…" 
	python train.py

eval:
	@echo "Generating report.md…" 
	echo "## Model Metrics" > report.md
	cat ./Results/metrics.txt >> report.md
	echo "" >> report.md
	echo "## Confusion Matrix Plot" >> report.md
	echo "![Confusion Matrix](./Results/model_results.png)" >> report.md
	cml comment create report.md

update-branch:
	@echo "Updating branch metadata…" 
	git config --global user.name "$(USER_NAME)"
	git config --global user.email "$(USER_EMAIL)"
	git commit -am "Update with new results"
	git push --force origin HEAD:update
