# Docker for Android SDK 29

Docker for Android SDK 29 with preinstalled build tools and emulator image

> Edit from [mindrunner/docker-android-sdk](https://github.com/mindrunner/docker-android-sdk)

**Installed Packages**
```bash
# sdkmanager --list
  Path                              | Version | Description                       | Location
  -------                           | ------- | -------                           | -------
  build-tools;29.0.3                | 29.0.3  | Android SDK Build-Tools 29.0.3    | build-tools/29.0.3/
  emulator                          | 30.0.5  | Android Emulator                  | emulator/
  patcher;v4                        | 1       | SDK Patch Applier v4              | patcher/v4/
  platform-tools                    | 29.0.6  | Android SDK Platform-Tools        | platform-tools/
  platforms;android-29              | 4       | Android SDK Platform 29           | platforms/android-29/
  system-images;a...gle_apis;x86_64 | 9       | Google APIs Intel x86 Atom_64 ... | system-images/a...le_apis/x86_64/
  tools                             | 26.0.1  | Android SDK Tools 26.0.1          | tools/
```

**Usage**

- Interactive way
  ```bash
  $ docker run -it --rm --privileged androidsdk/android-29:latest bash
  # check installed packages
  $ sdkmanager --list
  # create and run emulator
  $ avdmanager create avd -n first_avd --abi google_apis/x86_64 -k "system-images;android-29;google_apis;x86_64"
  $ emulator -avd first_avd -no-window -no-audio &
  $ adb devices
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```

  To connect the emulator using `adb` on the docker host machine, start the container with `--net=host`.
  You could also use [`scrcpy`](https://github.com/Genymobile/scrcpy) to do a screencast of the emulator.

- Non-interactive way
  ```bash
  # check installed packages
  $ docker run -it --rm androidsdk/android-29:latest sdkmanager --list
  # list existing emulators
  $ docker run -it --rm androidsdk/android-29:latest avdmanager list avd
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```