COMMIT=`git rev-parse --short HEAD`
JAR=`ls ./target/*.jar`
APP=seshify
REPO?=ahromis/$(APP)
TAG?=latest

  build:
	@docker run -it --rm --name my-maven-project -v /var/run/docker.sock\:/var/run/docker.sock -v "$(PWD)"\:/usr/src/mymaven -w /usr/src/mymaven maven\:3-jdk-8-alpine mvn package

  build-image:
	@echo "Building image with: $(JAR)"
	@docker build $(BUILD_ARGS) -t $(REPO):$(TAG) .
	@echo "Image created: $(REPO):$(TAG)"

  build-dev:
	@echo "Building image with: $(JAR)"
	@docker build $(BUILD_ARGS) -t $(REPO):$(COMMIT) .
	@echo "Image created: $(REPO):$(COMMIT)"
	@docker tag $(REPO):$(COMMIT) $(REPO):dev
	@echo "Image created: $(REPO):dev"

  push:
	@echo "Pushing image: $(REPO):$(TAG)"
	@docker push $(REPO):$(TAG)

  push-dev:
	@echo "Pushing image: $(REPO):$(COMMIT)"
	@docker push $(REPO):$(TAG)
	@echo "Pushing image: $(REPO):dev"
	@docker push $(REPO):dev

  .PHONY: build build-image build-dev push push-dev
