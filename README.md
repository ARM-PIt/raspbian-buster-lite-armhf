## Raspbian Buster Lite

https://hub.docker.com/r/armpits/raspbian-buster-lite-armhf

This is a minimal Raspbian Buster image built from a chroot using debbootstrap with this [Jenkins pipeline](https://github.com/ARM-PIt/jsl-test/blob/master/vars/pipelineChrootToDockerToRegistry.groovy). Raspberry Pi firmware assets are added from [this repository](https://github.com/ARM-PIt/rpi-firmware-essentials) and userland includes are added from the [official repository](https://github.com/raspberrypi/userland).

#### Firmware and Userland

The firmware utilities (/usr/bin/vcgencmd) are functional provided the container is given sufficient access to the relevant host devices (/dev/video10 /dev/video11 /dev/video12 /dev/vchiq /dev/vc-mem etc), as are tools such as v4l2-ctl. The rpi-firmware-essentials repository is branched by the latest stable kernel release for Raspbian and taken into the build by a parameter in the [Jenkinsfile](https://github.com/ARM-PIt/raspbian-test/blob/master/Jenkinsfile#L37). The interfaces directory from the rpi userland project was added as it was quite small and contains useful tools for compiling other rpi multimedia projects.

#### Build Process

As this build is coming from a Jenkins pipeline, there is no Dockerfile. Providing full transparency is tricky; however, all sources cited here are used in building and maintaining this image, no more no less.  Feel free to check out the Jenkins shared library mentioned here.  This is the code used for every build.

#### Sources

https://github.com/ARM-PIt/jenkins-shared-library

https://github.com/ARM-PIt/rpi-firmware-essentials

https://github.com/raspberrypi/firmware

https://github.com/raspberrypi/userland

http://raspbian.raspberrypi.org/raspbian.public.key
