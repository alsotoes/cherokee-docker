IMAGE       = cherokee
REPO        = headup
COMMIT_HASH = $(shell git rev-parse --short HEAD)
TAGS        = alpine-$(COMMIT_HASH)

all: build tag

build:
	podman build --progress=plain --tag "$(IMAGE)" .
tag:
	$(foreach tag, $(TAGS), podman image tag "$(IMAGE)" "$(REPO)/$(IMAGE):$(tag)";)

.PHONY: all build tag
