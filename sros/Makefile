NUM_IMAGES=$(shell ls *.qcow2 2>/dev/null| wc -l)
IMAGE=$(shell ls *.qcow2 2>/dev/null)
VERSION=$(shell echo $(IMAGE) | sed -e 's/.\+[^0-9]\([0-9][0-9]\.[0-9]\.[A-Z][0-9]\+\(-[0-9]\+\)\?\)[^0-9].*$$/\1/')
-include ../makefile.include

all: docker-image

usage:
	@echo "Usage: put the Nokia VSR qcow2 image in this directory and run:"
	@echo "  make docker-image"

no-image:
	@echo "ERROR: you have no .qcow2 image"

more-than-one-image:
	@echo "ERROR: you have more than one .qcow2 image"

incorrect-version-string:
	@echo "ERROR: the .vmdk file doesn't seem to contain a valid version number"
	@echo "       expecting [0-9][0-9].[0-9].[A-Z][0-9]+"

docker-build:
	@echo "Building docker image using $(IMAGE) as $(REGISTRY)vr-sros:$(VERSION)"
	docker build -t $(REGISTRY)vr-sros:$(VERSION) .
