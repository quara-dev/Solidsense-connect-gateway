# Motivation

1. We want an [OEM image](https://solidsense-connect.com/index.php/software/#:~:text=Option%20%233%20%E2%80%93%20OEM%20Version) for our solidsense N8 compact gateways. Due to performance issues, we cannot use SolidSense IoT version or SolidSense IoT Wirepas Version (and we don't need them anyway).

2. We learnt about Solidsense-Connect through repository the Solidsense-Connect website [...]

3. We Want to build an [OEM image](https://solidsense-connect.com/index.php/software/#:~:text=Option%20%233%20%E2%80%93%20OEM%20Version) following the guideline on https://github.com/solidsense-connect/Solidsense-connect-gateway

# Work done

1. Cloned repository
2. Checkout latest commit available (branch `meta-solidsense-products-sr`)
3. Follow guidelines and attempt to build an image with `custom` recipe.

> You can find all changes applied to the code base in this single commit: https://github.com/quara-dev/Solidsense-connect-gateway/commit/c63fa8f39d461d8dbabbd9514efe4ceb192a41d6

# Bug description

The build of `custom-quara` kas recipe fails due to `openssl` target failing to install.

## Environment

- `uname -a`:

```text
Linux 5.15.90.1-microsoft-standard-WSL2 #1 SMP Fri Jan 27 02:56:13 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```

- `cat /etc/os-release`: 

```txt
NAME="Ubuntu"
VERSION="20.04.6 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.6 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
```

## Complete log of failed build

```txt
2023-09-20 16:15:31 - INFO     - kas 2.5 started
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-imx8mnc$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - Using /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway as root for repository meta-custom
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common$ git remote set-url origin https://github.com/solidsense-connect/meta-cip-sr-common.git
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - Using /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway as root for repository meta-custom
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - Using /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway as root for repository meta-custom
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common$ git remote set-url origin https://github.com/solidsense-connect/meta-cip-sr-common.git
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git remote set-url origin https://github.com/meta-debian/meta-debian.git
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-openembedded$ git remote set-url origin https://github.com/openembedded/meta-openembedded.git
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-virtualization$ git remote set-url origin https://git.yoctoproject.org/git/meta-virtualization
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git remote set-url origin https://git.yoctoproject.org/git/poky.git
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git remote set-url origin https://github.com/mendersoftware/meta-mender.git
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-readonly-rootfs-overlay$ git remote set-url origin https://github.com/solidsense-connect/meta-readonly-rootfs-overlay
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git cat-file -t warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-openembedded$ git cat-file -t warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-virtualization$ git cat-file -t warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git cat-file -t warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git cat-file -t warrior
2023-09-20 16:15:31 - INFO     - Repository meta-debian already contains warrior as commit
2023-09-20 16:15:31 - INFO     - Repository meta-openembedded already contains warrior as commit
2023-09-20 16:15:31 - INFO     - Repository meta-virtualization already contains warrior as commit
2023-09-20 16:15:31 - INFO     - Repository poky already contains warrior as commit
2023-09-20 16:15:31 - INFO     - Repository meta-mender already contains warrior as commit
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - Using /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway as root for repository meta-custom
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git status -s
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git rev-parse --verify -q origin/warrior
2023-09-20 16:15:31 - INFO     - 21b09c772cca970bf3a5992aa1134d03aa8fcad0
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git checkout -q 21b09c772cca970bf3a5992aa1134d03aa8fcad0 -B warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-openembedded$ git status -s
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-openembedded$ git rev-parse --verify -q origin/warrior
2023-09-20 16:15:31 - INFO     - a24acf94d48d635eca668ea34598c6e5c857e3f8
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-openembedded$ git checkout -q a24acf94d48d635eca668ea34598c6e5c857e3f8 -B warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-virtualization$ git status -s
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-virtualization$ git rev-parse --verify -q origin/warrior
2023-09-20 16:15:31 - INFO     - 6961097ff660eb32860fcd4d8eb29405be4c6766
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-virtualization$ git checkout -q 6961097ff660eb32860fcd4d8eb29405be4c6766 -B warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git status -s
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git rev-parse --verify -q origin/warrior
2023-09-20 16:15:31 - INFO     - d4b57c68b22027c2bedff335dee06af963e4f8a8
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git checkout -q d4b57c68b22027c2bedff335dee06af963e4f8a8 -B warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git status -s
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git rev-parse --verify -q origin/warrior
2023-09-20 16:15:31 - INFO     - 596c249abeb0f57f4a29d10daabae7e2b662b238
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git checkout -q 596c249abeb0f57f4a29d10daabae7e2b662b238 -B warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - Using /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway as root for repository meta-custom
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git checkout -q -B patched-warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git checkout -q -B patched-warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git checkout -q -B patched-warrior
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git apply /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-debian/0001-change-utmp-to-43.patch
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git apply /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-mender/0001-u-boot-remove-debug-option-from-uboot_auto_configure.patch
2023-09-20 16:15:31 - INFO     - Patch applied. (patch path: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-debian/0001-change-utmp-to-43.patch, repo: meta-debian, patch entry: 1)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git add -A
2023-09-20 16:15:31 - INFO     - Patch applied. (patch path: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-mender/0001-u-boot-remove-debug-option-from-uboot_auto_configure.patch, repo: meta-mender, patch entry: 1)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git add -A
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git apply /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/poky/0001-add-unzip.patch
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git commit -a --author kas <kas@example.com> -m msg
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git commit -a --author kas <kas@example.com> -m msg
2023-09-20 16:15:31 - INFO     - Patch applied. (patch path: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/poky/0001-add-unzip.patch, repo: poky, patch entry: 1)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git add -A
2023-09-20 16:15:31 - INFO     - [patched-warrior d4f4b348] msg
2023-09-20 16:15:31 - INFO     - Author: kas <kas@example.com>
2023-09-20 16:15:31 - INFO     - 1 file changed, 1 insertion(+), 1 deletion(-)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git apply /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-debian/0002-use-olddefconfig-instead-of-oldnoconfig.patch
2023-09-20 16:15:31 - INFO     - [patched-warrior 8f487108] msg
2023-09-20 16:15:31 - INFO     - Author: kas <kas@example.com>
2023-09-20 16:15:31 - INFO     - 1 file changed, 1 insertion(+), 2 deletions(-)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git apply /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-mender/0002-add-fsck-check-to-data-partition.patch
2023-09-20 16:15:31 - INFO     - Patch applied. (patch path: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-debian/0002-use-olddefconfig-instead-of-oldnoconfig.patch, repo: meta-debian, patch entry: 2)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git add -A
2023-09-20 16:15:31 - INFO     - Patch applied. (patch path: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/meta-mender/0002-add-fsck-check-to-data-partition.patch, repo: meta-mender, patch entry: 2)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git add -A
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian$ git commit -a --author kas <kas@example.com> -m msg
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-mender$ git commit -a --author kas <kas@example.com> -m msg
2023-09-20 16:15:31 - INFO     - [patched-warrior cb20c586] msg
2023-09-20 16:15:31 - INFO     - Author: kas <kas@example.com>
2023-09-20 16:15:31 - INFO     - 1 file changed, 1 insertion(+), 1 deletion(-)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git commit -a --author kas <kas@example.com> -m msg
2023-09-20 16:15:31 - INFO     - [patched-warrior 3134f231] msg
2023-09-20 16:15:31 - INFO     - Author: kas <kas@example.com>
2023-09-20 16:15:31 - INFO     - 1 file changed, 1 insertion(+), 1 deletion(-)
2023-09-20 16:15:31 - INFO     - [patched-warrior 7364d2dfea] msg
2023-09-20 16:15:31 - INFO     - Author: kas <kas@example.com>
2023-09-20 16:15:31 - INFO     - 1 file changed, 1 insertion(+), 1 deletion(-)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git apply /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/poky/0002-remove-bpf_perf_event_h.patch
2023-09-20 16:15:31 - INFO     - Patch applied. (patch path: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/poky/0002-remove-bpf_perf_event_h.patch, repo: poky, patch entry: 2)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git add -A
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git commit -a --author kas <kas@example.com> -m msg
2023-09-20 16:15:31 - INFO     - [patched-warrior 380a226516] msg
2023-09-20 16:15:31 - INFO     - Author: kas <kas@example.com>
2023-09-20 16:15:31 - INFO     - 1 file changed, 1 insertion(+), 1 deletion(-)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git apply /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/poky/0003-use-olddefconfig-instead-of-oldnoconfig.patch
2023-09-20 16:15:31 - INFO     - Patch applied. (patch path: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-common/patches/poky/0003-use-olddefconfig-instead-of-oldnoconfig.patch, repo: poky, patch entry: 3)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git add -A
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ git commit -a --author kas <kas@example.com> -m msg
2023-09-20 16:15:31 - INFO     - [patched-warrior e33b591d0b] msg
2023-09-20 16:15:31 - INFO     - Author: kas <kas@example.com>
2023-09-20 16:15:31 - INFO     - 1 file changed, 1 insertion(+), 1 deletion(-)
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - Using /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway as root for repository meta-custom
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky$ /tmp/tmpr2d_h18x/get_bb_env /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky$ git rev-parse --show-toplevel
2023-09-20 16:15:31 - INFO     - Using /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway as root for repository meta-custom
2023-09-20 16:15:31 - INFO     - /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build$ /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/bitbake/bin/bitbake -c build core-image-minimal
2023-09-20 16:15:32 - INFO     - NOTE: Your conf/bblayers.conf has been automatically updated.
2023-09-20 16:15:32 - INFO     - WARNING: Host distribution "ubuntu-20.04" has not been validated with this version of the build system; you may possibly experience unexpected failures. It is recommended that you use a tested distribution.
2023-09-20 16:15:32 - INFO     - Loading cache...done.
2023-09-20 16:15:33 - INFO     - Loaded 1107 entries from dependency cache.
2023-09-20 16:16:31 - INFO     - Parsing recipes...done.
2023-09-20 16:16:31 - INFO     - Parsing of 2674 .bb files complete (661 cached, 2013 parsed). 4046 targets, 129 skipped, 0 masked, 0 errors.
2023-09-20 16:16:31 - INFO     - WARNING: No bb files matched BBFILE_PATTERN_sr-imx8mnc '^/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-cip-sr-imx8mnc/'
2023-09-20 16:16:31 - INFO     - NOTE: Resolving any missing task queue dependencies
2023-09-20 16:16:32 - INFO     - 
2023-09-20 16:16:32 - INFO     - Build Configuration:
2023-09-20 16:16:32 - INFO     - BB_VERSION           = "1.42.0"
2023-09-20 16:16:32 - INFO     - BUILD_SYS            = "x86_64-linux"
2023-09-20 16:16:32 - INFO     - NATIVELSBSTRING      = "universal"
2023-09-20 16:16:32 - INFO     - TARGET_SYS           = "aarch64-deby-linux"
2023-09-20 16:16:32 - INFO     - MACHINE              = "imx8mnc"
2023-09-20 16:16:32 - INFO     - DISTRO               = "deby"
2023-09-20 16:16:32 - INFO     - DISTRO_VERSION       = "10.0"
2023-09-20 16:16:32 - INFO     - TUNE_FEATURES        = "aarch64 cortexa53 crc"
2023-09-20 16:16:32 - INFO     - TARGET_FPU           = ""
2023-09-20 16:16:32 - INFO     - meta-cip-common
2023-09-20 16:16:32 - INFO     - meta-cip-sr-common
2023-09-20 16:16:32 - INFO     - meta-cip-sr-imx8mnc  = "custom:26bf745c386f56984c0a9ab0cc888f6255213863"
2023-09-20 16:16:32 - INFO     - meta-debian          = "patched-warrior:cb20c5866a2958e1d0d40716d71b6e4eeeeac171"
2023-09-20 16:16:32 - INFO     - meta-mender-core     = "patched-warrior:3134f2310a220d8af0c1f8197165effbe1c27ff4"
2023-09-20 16:16:32 - INFO     - meta-filesystems
2023-09-20 16:16:32 - INFO     - meta-networking
2023-09-20 16:16:32 - INFO     - meta-oe
2023-09-20 16:16:32 - INFO     - meta-python          = "warrior:a24acf94d48d635eca668ea34598c6e5c857e3f8"
2023-09-20 16:16:32 - INFO     - meta-readonly-rootfs-overlay = "master:c7b8a6fec1da23104299130f3ce17fea22dfda19"
2023-09-20 16:16:32 - INFO     - meta-virtualization  = "warrior:6961097ff660eb32860fcd4d8eb29405be4c6766"
2023-09-20 16:16:32 - INFO     - meta
2023-09-20 16:16:32 - INFO     - meta-poky            = "patched-warrior:e33b591d0b0f0953723c7a0395cb637527baec52"
2023-09-20 16:16:32 - INFO     - 
2023-09-20 16:16:38 - INFO     - Initialising tasks...done.
2023-09-20 16:16:38 - INFO     - Sstate summary: Wanted 1656 Found 0 Missed 1656 Current 26 (0% match, 1% complete)
2023-09-20 16:16:38 - INFO     - NOTE: Executing SetScene Tasks
2023-09-20 16:16:38 - INFO     - NOTE: Executing RunQueue Tasks
2023-09-20 16:16:39 - INFO     - NOTE: Running task 222 of 5112 (/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-kernel/linux-libc-headers/linux-libc-headers-base_git.bb:do_unpack)
2023-09-20 16:16:39 - INFO     - NOTE: Running task 233 of 5112 (/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-kernel/linux-libc-headers/linux-libc-headers-base_git.bb:do_prepare_recipe_sysroot)
2023-09-20 16:16:39 - INFO     - NOTE: Running task 284 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/openssl/openssl_debian.bb:do_fetch)
2023-09-20 16:16:39 - INFO     - NOTE: Running task 301 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/elfutils/elfutils_debian.bb:do_fetch)
2023-09-20 16:16:40 - INFO     - NOTE: recipe linux-libc-headers-base-gitAUTOINC+10adcfb40c-r0: task do_prepare_recipe_sysroot: Started
2023-09-20 16:16:40 - INFO     - NOTE: recipe linux-libc-headers-base-gitAUTOINC+10adcfb40c-r0: task do_unpack: Started
2023-09-20 16:16:40 - INFO     - NOTE: recipe linux-libc-headers-base-gitAUTOINC+10adcfb40c-r0: task do_prepare_recipe_sysroot: Succeeded
2023-09-20 16:16:40 - INFO     - NOTE: recipe elfutils-native-0.176-r0: task do_fetch: Started
2023-09-20 16:16:40 - INFO     - NOTE: Running task 302 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/ncurses/ncurses_debian.bb:do_debian_unpack_extra)
2023-09-20 16:16:40 - INFO     - NOTE: recipe openssl-native-1.1.1n-r0: task do_fetch: Started
2023-09-20 16:16:40 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_debian_unpack_extra: Started
2023-09-20 16:16:40 - INFO     - WARNING: openssl-native-1.1.1n-r0 do_fetch: Failed to fetch URL http://security.debian.org/debian-security/pool/updates/main/o/openssl/openssl_1.1.1n-0+deb10u5.dsc;name=openssl_1.1.1n-0+deb10u5.dsc, attempting MIRRORS if available
2023-09-20 16:16:40 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_debian_unpack_extra: Succeeded
2023-09-20 16:16:40 - INFO     - NOTE: Running task 303 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/ncurses/ncurses_debian.bb:do_debian_patch)
2023-09-20 16:16:40 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_debian_patch: Started
2023-09-20 16:16:41 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_debian_patch: Succeeded
2023-09-20 16:16:41 - INFO     - NOTE: Running task 304 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/ncurses/ncurses_debian.bb:do_patch)
2023-09-20 16:16:41 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_patch: Started
2023-09-20 16:16:41 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_patch: Succeeded
2023-09-20 16:16:41 - INFO     - NOTE: Running task 305 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/ncurses/ncurses_debian.bb:do_prepare_recipe_sysroot)
2023-09-20 16:16:42 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_prepare_recipe_sysroot: Started
2023-09-20 16:16:42 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_prepare_recipe_sysroot: Succeeded
2023-09-20 16:16:42 - INFO     - NOTE: Running task 306 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/ncurses/ncurses_debian.bb:do_configure)
2023-09-20 16:16:42 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_configure: Started
2023-09-20 16:16:43 - ERROR    - ERROR: openssl-native-1.1.1n-r0 do_fetch: Fetcher failure: Fetch command export PSEUDO_DISABLED=1; unset _PYTHON_SYSCONFIGDATA_NAME; export PATH="/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/scripts/native-intercept:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/sysroots-uninative/x86_64-linux/usr/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/scripts:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/bin/x86_64-linux:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/sbin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/sbin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/bitbake/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/hosttools"; export HOME="/tmp/tmp2igb88oy"; /usr/bin/env wget -t 2 -T 30 --passive-ftp --no-check-certificate -P /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/downloads 'http://security.debian.org/debian-security/pool/updates/main/o/openssl/openssl_1.1.1n-0+deb10u5.dsc' --progress=dot -v failed with exit code 8, output:
2023-09-20 16:16:43 - ERROR    - --2023-09-20 14:16:40--  http://security.debian.org/debian-security/pool/updates/main/o/openssl/openssl_1.1.1n-0+deb10u5.dsc
2023-09-20 16:16:43 - ERROR    - Resolving security.debian.org (security.debian.org)... 151.101.2.132, 151.101.66.132, 151.101.194.132, ...
2023-09-20 16:16:43 - ERROR    - Connecting to security.debian.org (security.debian.org)|151.101.2.132|:80... connected.
2023-09-20 16:16:43 - ERROR    - HTTP request sent, awaiting response... 404 Not Found
2023-09-20 16:16:43 - ERROR    - 2023-09-20 14:16:40 ERROR 404: Not Found.
2023-09-20 16:16:43 - ERROR    - 
2023-09-20 16:16:43 - ERROR    - 
2023-09-20 16:16:43 - ERROR    - ERROR: openssl-native-1.1.1n-r0 do_fetch: Fetcher failure for URL: 'http://security.debian.org/debian-security/pool/updates/main/o/openssl/openssl_1.1.1n-0+deb10u5.dsc;name=openssl_1.1.1n-0+deb10u5.dsc'. Unable to fetch URL from any source.
2023-09-20 16:16:43 - ERROR    - ERROR: openssl-native-1.1.1n-r0 do_fetch:
2023-09-20 16:16:43 - ERROR    - ERROR: openssl-native-1.1.1n-r0 do_fetch: Function failed: base_do_fetch
2023-09-20 16:16:43 - ERROR    - ERROR: Logfile of failure stored in: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/temp/log.do_fetch.234264
2023-09-20 16:16:43 - INFO     - NOTE: recipe openssl-native-1.1.1n-r0: task do_fetch: Failed
2023-09-20 16:16:43 - ERROR    - ERROR: Task (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/openssl/openssl_debian.bb:do_fetch) failed with exit code '1'
2023-09-20 16:16:43 - INFO     - NOTE: Running task 307 of 5112 (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/gettext/gettext_debian.bb:do_unpack)
2023-09-20 16:16:43 - INFO     - NOTE: recipe gettext-native-0.19.8.1-r0: task do_unpack: Started
2023-09-20 16:16:46 - INFO     - NOTE: recipe gettext-native-0.19.8.1-r0: task do_unpack: Succeeded
2023-09-20 16:16:50 - INFO     - NOTE: recipe elfutils-native-0.176-r0: task do_fetch: Succeeded
2023-09-20 16:16:58 - INFO     - NOTE: recipe linux-libc-headers-base-gitAUTOINC+10adcfb40c-r0: task do_unpack: Succeeded
2023-09-20 16:17:12 - INFO     - NOTE: recipe ncurses-native-6.1+20181013-r0: task do_configure: Succeeded
2023-09-20 16:17:14 - INFO     - NOTE: Tasks Summary: Attempted 307 tasks of which 297 didn't need to be rerun and 1 failed.
2023-09-20 16:17:14 - INFO     - 
2023-09-20 16:17:14 - INFO     - Summary: 1 task failed:
2023-09-20 16:17:14 - INFO     - virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/openssl/openssl_debian.bb:do_fetch
2023-09-20 16:17:14 - INFO     - Summary: There were 3 WARNING messages shown.
2023-09-20 16:17:14 - INFO     - Summary: There were 4 ERROR messages shown, returning a non-zero exit code.
2023-09-20 16:17:14 - ERROR    - Command "/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build$ /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/bitbake/bin/bitbake -c build core-image-minimal" failed
--- Error summary ---
ERROR: openssl-native-1.1.1n-r0 do_fetch: Fetcher failure: Fetch command export PSEUDO_DISABLED=1; unset _PYTHON_SYSCONFIGDATA_NAME; export PATH="/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/scripts/native-intercept:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/sysroots-uninative/x86_64-linux/usr/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/scripts:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/bin/x86_64-linux:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/sbin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/usr/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/sbin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/recipe-sysroot-native/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/poky/bitbake/bin:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/hosttools"; export HOME="/tmp/tmp2igb88oy"; /usr/bin/env wget -t 2 -T 30 --passive-ftp --no-check-certificate -P /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/downloads 'http://security.debian.org/debian-security/pool/updates/main/o/openssl/openssl_1.1.1n-0+deb10u5.dsc' --progress=dot -v failed with exit code 8, output:
--2023-09-20 14:16:40--  http://security.debian.org/debian-security/pool/updates/main/o/openssl/openssl_1.1.1n-0+deb10u5.dsc
Resolving security.debian.org (security.debian.org)... 151.101.2.132, 151.101.66.132, 151.101.194.132, ...
Connecting to security.debian.org (security.debian.org)|151.101.2.132|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2023-09-20 14:16:40 ERROR 404: Not Found.


ERROR: openssl-native-1.1.1n-r0 do_fetch: Fetcher failure for URL: 'http://security.debian.org/debian-security/pool/updates/main/o/openssl/openssl_1.1.1n-0+deb10u5.dsc;name=openssl_1.1.1n-0+deb10u5.dsc'. Unable to fetch URL from any source.
ERROR: openssl-native-1.1.1n-r0 do_fetch: 
ERROR: openssl-native-1.1.1n-r0 do_fetch: Function failed: base_do_fetch
ERROR: Logfile of failure stored in: /home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/build/tmp/work/x86_64-linux/openssl-native/1.1.1n-r0/temp/log.do_fetch.234264
ERROR: Task (virtual:native:/home/charbonnierg/github/quara-dev/Solidsense-connect-gateway/poky/meta-debian/recipes-debian/openssl/openssl_debian.bb:do_fetch) failed with exit code '1'
```