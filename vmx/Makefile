NUM_IMAGES=$(shell ls *.tgz 2>/dev/null| wc -l)
IMAGE=$(shell ls *.tgz 2>/dev/null)
VERSION=$(shell echo $(IMAGE) | sed -e 's/.\+[^0-9]\([0-9][0-9]\.[0-9][A-Z][0-9]\+\.[0-9]\+\)[^0-9].*$$/\1/')
-include ../makefile.include

usage:
	@echo "Usage: put the Juniper vMX .tgz file in this directory and run:"
	@echo "  make docker-image"

no-image:
	@echo "ERROR: you have no .tgz file"

more-than-one-image:
	@echo "ERROR: you have more than one .tgz file"

incorrect-version-string:
	@echo "ERROR: the .tgz file doesn't seem to contain a valid version number"
	@echo "       expecting [0-9][0-9].[0-9]R[0-9]+.[0-9]+"

docker-build:
	@echo "Building docker image using $(IMAGE) as $(REGISTRY)vr-vmx:$(VERSION)"
	docker build -t $(REGISTRY)vr-vmx:$(VERSION) .
