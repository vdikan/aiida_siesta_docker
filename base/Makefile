AIIDA_VERSION=0.10.1
AIIDA_EXTRAS=""

all: image

image:
	docker build --no-cache -t aiida_core_base:$(AIIDA_VERSION) \
	--build-arg aiida_version=$(AIIDA_VERSION) \
	--build-arg aiida_extras=$(AIIDA_EXTRAS) \
	.
