library identifier: 'ARM-PIt-libraries@master',
retriever: modernSCM(
  [
    $class: 'GitSCMSource',
    credentialsId: 'cedb6908-8b3d-49a3-9137-a086e65920c3',
    remote: 'git@github.com:ARM-PIt/jenkins-shared-library.git',
    traits:  [[$class: 'jenkins.plugins.git.traits.BranchDiscoveryTrait']]
  ]
)

properties(
  [
    parameters(
      [
        choice(
          name: 'build_type',
          defaultValue: 'weekly',
          choices: ['adhoc','nightly','weekly'].join('\n'),
          description: 'Which build type is this? (adhoc, nightly, weekly)',
        )
      ]
    )
  ]
)

pipelineChrootToDockerToRegistry project_git_url: "git@github.com:ARM-PIt/raspbian-buster-lite-armhf.git", 
project_git_branch: "master",
distro: "raspbian",
build_type: "${build_type}",
image_name: "raspbian-buster-lite-armhf",
registry_path: "armpits",
registry_url: "https://docker.io",
apt_url: "http://raspbian.raspberrypi.org/raspbian",
apt_key_url: "http://raspbian.raspberrypi.org/raspbian.public.key",
apt_options: "buster main contrib non-free rpi",
rpifw_git_url: "https://github.com/ARM-PIt/rpi-firmware-essentials.git",
rpifw_git_branch: "5.4.51-v7l",
rpifw_git_checkout_dir: "rpi-firmware-essentials",
rpiul_git_url: "https://github.com/raspberrypi/userland.git",
rpiul_git_branch: "master",
rpiul_git_checkout_dir: "userland"
