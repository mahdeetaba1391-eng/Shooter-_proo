name: Build APK

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-22.04

    steps:
    - uses: actions/checkout@v3

    - name: Install dependencies
      run: |
        sudo apt update
        sudo apt install -y python3 python3-pip \
        git zip unzip openjdk-17-jdk \
        build-essential ccache \
        libncurses5 libstdc++6 libffi-dev libssl-dev

    - name: Install buildozer
      run: |
        pip3 install --upgrade pip
        pip3 install buildozer cython

    - name: Build APK
      run: |
        buildozer android debug

    - name: Upload APK
      uses: actions/upload-artifact@v4
      with:
        name: SHOOTER_PRO_PP_APK
        path: bin/*.apk
