# Docker Build and BuildSpec Example

This repository contains examples of Dockerfiles and AWS CodeBuild BuildSpec YAML files for building Java applications using the Corretto 8 runtime.

## Repository Structure

- `Dockerfile`: A sample Dockerfile for building a Java application.
- `buildspec.yml`: A BuildSpec file for AWS CodeBuild to automate the build process.

## BuildSpec YAML Overview

The `buildspec.yml` file is structured into several phases:

```yaml
version: 0.2
phases:
  install:
    runtime-versions:
      java: corretto8
  pre_build:
    commands:
    - echo In the pre_build phase...
  build:
    commands:
    - echo Build started on `date`
  post_build:
    commands:
    - echo Build completed on `date`
    - mvn package
    - mv target/bootdocker.jar bootdocker.jar
artifacts:
  files:
  - bootdocker.jar
  discard-paths: yes
