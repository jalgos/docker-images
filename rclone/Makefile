IMAGE=docker.pkg.github.com/jalgos/docker-images/rclone:1.48.0

.PHONY: build push

build:
	docker build -t $(IMAGE) .

push:
	docker push $(IMAGE)

default: build