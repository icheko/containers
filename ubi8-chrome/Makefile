.PHONY : all

BUILD_TAG           = ubi8-chrome
DOCKER_OR_PODMAN   := $(shell which podman || which docker)

build:
	$(DOCKER_OR_PODMAN) build \
		--tag $(BUILD_TAG) \
		--file Dockerfile .

run-bash: build
	$(DOCKER_OR_PODMAN) run -it --rm -u root --entrypoint /bin/bash $(BUILD_TAG)

list-packages: build
	$(DOCKER_OR_PODMAN) run -t --rm --entrypoint /bin/bash $(BUILD_TAG) -c "dnf list installed"