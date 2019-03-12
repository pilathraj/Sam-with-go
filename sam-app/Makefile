# Go parameters
GOCMD=go
GOBUILD=$(GOCMD) build
GOCLEAN=$(GOCMD) clean
GOTEST=$(GOCMD) test
GOGET=$(GOCMD) get
BINARY_NAME=hello-world
BINARY_UNIX=$(BINARY_NAME)-unix
GO_UNIX_OS = linux

# Lambda path
LAMBDAZIP = "D:\go\bin\build-lambda-zip.exe"
S3Name?=pr-s3-dev

.PHONY: deps clean build test

local: deps clean build test dev
all: deps clean build test dev deploy
deploy: package cloudformation

deps:
	$(GOGET) -u github.com/aws/aws-lambda-go/...

clean:
	$(GOCLEAN)
	rm -rf ./hello-world/hello-world
	rm -rf main-sam.zip

test:
	$(GOTEST) -v ./...

build:
	cd hello-world && export GOOS=$(GO_UNIX_OS) && $(GOBUILD) -o $(BINARY_NAME)
dev:
	sam local start-api

package:
	#Zip binary file alone
	${LAMBDAZIP} -o main-sam.zip ./hello-world/hello-world
	#sam package --output-template-file packaged.yaml --s3-bucket ${S3Name}
	aws s3 cp main-sam.zip s3://$(S3Name)/

cloudformation:
	sam deploy --template-file packaged.yaml --stack-name sam-app --capabilities CAPABILITY_IAM
