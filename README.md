# github actions for mbed application

[![BuildTest](https://github.com/OUXT-Polaris/build-mbed-app-action/actions/workflows/buildtest.yaml/badge.svg)](https://github.com/OUXT-Polaris/build-mbed-app-action/actions/workflows/buildtest.yaml)

## How to use

```
name: BuildTest

on:
  schedule:
    - cron: 0 0 * * *
  pull_request:
  workflow_dispatch:
  push:
    branches:
      - master
      
jobs:
  publish:
    runs-on: ubuntu-latest
    container: ghcr.io/armmbed/mbed-os-env
    steps:
      - uses: actions/checkout@v3
        with:
          repository: ARMmbed/mbed-os-example-blinky
      - uses: OUXT-Polaris/build-mbed-app-action@master
        with:
          target_board: DISCO_L475VG_IOT01A
          toolchain: GCC_ARM
```

## Arguments

| name         | required | default | description       |
| ------------ | -------- | ------- | ----------------- |
| target_board | true     |         | target board name |
| toolchain    | false    | GCC_ARM | compile toolchain |

## How it works

This action use [composite action](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action) in github actions.
This actions works in [this docker image](https://github.com/ARMmbed/mbed-os/pkgs/container/mbed-os-env).