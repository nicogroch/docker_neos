.PHONY: help build pull up stop rm backup

# Set directory of this Makefile to a variable to use later.
MAKEPATH := $(abspath $(lastword $(MAKEFILE_LIST)))
PWD := $(dir $(MAKEPATH))

# This will output the help for each task.
# Thanks to https://marmelab.com/blog/2016/02/29/auto-documented-makefile.html.
help: ## This help.
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

# Set help target as default target
.DEFAULT_GOAL := help

build: ## Buildes the Docker images.
	docker-compose build

pull: ## Pulls the Docker images.
	docker-compose pull

up: ## Spins up the Docker containers.
	docker-compose up -d

stop: ## Stops running Docker containers.
	docker-compose stop

rm: stop ## Stops and removes Docker containers.
	docker-compose rm

backup: stop ## Stops running Docker containers and makes a backup of the Docker Data Volumes.
	tar cfvz backup.tar.gz volumes/
