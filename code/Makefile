BASE_IMAGE_VERSION=0.11.0
SIESTA_VERSION=4.1-b3
SIESTA=siesta-$(SIESTA_VERSION)

all: image clean

image:
	wget -N https://launchpad.net/siesta/4.1/4.1-b3/+download/$(SIESTA).tar.gz
	docker build --no-cache -t aiida_siesta_code:$(BASE_IMAGE_VERSION) \
	--build-arg aiida_base=$(BASE_IMAGE_VERSION) \
	--build-arg siesta_version=$(SIESTA_VERSION) \
	.

clean:
	rm ./$(SIESTA).tar.gz
