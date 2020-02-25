# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.1.3] - 2020-02-25

### Changed
Rename ceph-bootstrap to ceph-salt (PR#114)
Migrate ceph-bootstrap-qa to sesdev (part 2) (PR#112)
provision: remove which RPM from test environment (PR#113)
ceph_salt_deployment: disable system update and reboot (PR#117)
seslib: by default, a mgr for every mon (PR#111)

## [1.1.2] - 2020-02-17

### Added
Implement "vagrant box list" and "vagrant box remove" (PR#69)
Allow user to specify custom private key file for remote libvirt (PR#71)
spec: add Fedora-specific Requires (PR#77)
Pillar is now automatically configured by ceph-bootstrap (PR#78)
Implement "sesdev scp" feature (PR#101)
Implement "sesdev create caasp4" feature (PR#103)

### Fixed
Revamp --num-disks handling (PR#65)
Miscellaneous spec file cleanups and bugfixes (PR#72)
several fixes for octopus/ses7 deployment (PR#76)
Remove any orphaned images after destroy (PR#81)
seslib: fix Ceph repos for ses5, ses6, ses7 (PR#83)
tools/run_async: decode stderr bytes (PR#88)
libvirt/network: autostart networks per default (PR#93)
Fix NTP issue that was causing SES5 deployment to fail (PR#108)

### Changed
ceph_bootstrap_deployment: "ceph-bootstrap -ldebug deploy" (PR#68)
Increase chances of getting the latest ses7 packages (PR#84)
ceph_bootstrap_deployment: log cephadm and ceph-bootstrap version (PR#86)
ceph_bootstrap: restart salt-master after ceph-bootstrap installation (PR#87)
seslib: add SES7 Internal Media when --qa-test given (PR#90)

## [1.1.1] - 2020-01-29
### Added
- Octopus and SES7 deployment with ceph-bootstrap (PR #28)
- Implement --repo-priority / --no-repo-priority (PR #19)
- Add option for predefined libvirt networks (PR #39) 
- qa: initial qa integration (PR #46)

### Fixed
- When deploying ses5 with explicit --roles, do not add openattic (PR #23)
- Enable display of manpages (PR #33)
- ceph_bootstrap_deployment.sh: Also set -e (PR #35)
- vagrant: generate random serial number for each attached disk (PR #50)
- ceph_bootstrap_deployment: ensure minions are responding (PR #52)

### Changed
- Add node info to SSH tunnel command (PR #27)
- Display amount of deployed VMs in status output (PR #31)
- Enable linter via travis (PR #38)
- ceph-bootstrap: 'ceph-salt-formula' moved to 'ceph-bootstrap' (PR #44)
- ceph_bootstrap: use "ceph-bootstrap deploy" command to run ceph-salt formula
  (PR #62)

## [1.1.0] - 2019-11-27
### Added
- Add Github Action to publish to OBS (PR #10).
- SUMA deployment in `octopus` version (PR #14).

### Fixed
- Handle Ctrl+C on deployment creation (PR #8)
- seslib: fixed 100% cpu usage when deploying cluster (PR #16).

### Changed
- Updated README.md on how to use an editable Python venv (PR #15).
- cli: `list` subcommand now shows the version of each deployment (PR #12).
- octopus and ses7 versions now use the OBS repo filesystems:ceph:master:upstream that
  is updated in a daily basis (PR #13).

## [1.0.3] - 2019-11-15
### Added
- README instructions about libvirt configuration (PR #4)

### Changed
- CLI subcommand `info` replaced by `show`.

### Fixed
- fix typo in `sesdev start --help` command (PR #6)

## [1.0.2] - 2019-11-15
### Fixed
- setup.py: missing libvirt engine template directory (PR #3)

## [1.0.1] - 2019-11-14
### Changed
- The OBS repo URL of sesdev package in README.md

### Fixed
- setup.py: missing template directories (PR #2)

## [1.0.0] - 2019-11-14
### Added
- `--libvirt-(user|storage-pool)` options to CLI.
- `--stop-before-deepsea-stage` option to CLI.
- `--cpus` option to CLI.
- `--ram` option to CLI.
- `--disk-size` option to CLI.
- `--repo` option to CLI.
- `--vagrant-box` option to CLI.
- openSUSE Leap 15.2 distro.
- SLES-15-SP2 distro.
- SES7 deployment based on SLES-15-SP2 (no Ceph cluster deployment yet).
- SES5 deployment based on SLES-12-SP3.
- SES6 deployment based on SLES-15-SP1.
- Octopus deployment based on Leap 15.2 (DeepSea is working 90%)
- Installation instructions to the README.md.
- openATTIC service tunneling support.
- Deployment description with `sesdev info <deployment_id>`.

### Changed
- Use `libvirt_use_ssh` instead of `libvirt_use_ssl` to configure SSH access.
- Vagrantfile template refactoring to support different deployment tools.
  Currently only DeepSea is implemented.
- Code refactoring to support other VM engines besides libvirt.
- CLI creation command changed to include the SES version we want to deploy.
  Now the command looks like `sesdev create <version> [options] <deployment_id>`.
- List deployments now return the status and the name of the nodes in each deployment.

### Fixed
- remove `qemu_use_session` vagrant-libvirt setting when packaging for Fedora 29.
- Use `RSA#exportKey` method to work with version 3.4.6 of pycrytodomex.
- Fixed type of `stop-before-stage` setting.
- Fix ssh command when libvirt is located in the localhost.
- Fix accepting salt-keys step in deployment by polling `salt-key -L`.
- Fix deployment status when `vagrant up` was never run.
- Only create deployment directory and files after rendering Vagranfile without errors.

## [0.2.2] - 2019-10-30
### Changed
- replaced `pycryptodome` library by `pycryptodomex`

### Fixed
- fix Fedora python rpm build macros in the specfile
- fix Fedora dependencies naming
- added buildrequires fdupes to spec file
- add buildrequires python3-rpm-macros for fedora in spec file
- add buildrequires python-rpm-macros for fedora in spec file
- fixed library dependencies
- explicitly set `qemu_use_session = false` in Vagrantfile to always use a system connection
- openSUSE requires python3-setuptools to run sesdev

## [0.2.1] - 2019-10-29
### Fixed
- fixed `Source` and `Release` attributes in spec file

## [0.2.0] - 2019-10-29
### Added
- `--version` option to print the installed version.

### Changed
- version in `setup.py` is now parsed from `sesdev.spec`.

### Fixed
- `yaml.FullLoader` does not exist in older versions of PyYAML.
- unreleased link from CHANGELOG.md was pointing to keepchangelog repo.

## [0.1.0] - 2019-10-29
### Changed
- sesdev.spec: fixed sesdev dependencies
- sesdev.spec: fixed source URL
- sesdev.spec: set version number to 0.1.0

## [0.0.1] - 2019-10-29
### Added
- `sesdev` CLI tool with the following features:
  - create/destroy nautilus cluster based on openSUSE Leap 15.1.
  - ssh access to the nodes of the cluster.
  - port forwarding (ssh tunnel) of dashboard service.
- RPM spec file.
- Minimal README with a few usage instructions.
- The CHANGELOG file.

[unreleased]: https://github.com/SUSE/sesdev/compare/v1.1.3...HEAD
[1.1.3]: https://github.com/SUSE/sesdev/releases/tag/v1.1.3
[1.1.2]: https://github.com/SUSE/sesdev/releases/tag/v1.1.2
[1.1.1]: https://github.com/SUSE/sesdev/releases/tag/v1.1.1
[1.1.0]: https://github.com/SUSE/sesdev/releases/tag/v1.1.0
[1.0.3]: https://github.com/SUSE/sesdev/releases/tag/v1.0.3
[1.0.2]: https://github.com/SUSE/sesdev/releases/tag/v1.0.2
[1.0.1]: https://github.com/SUSE/sesdev/releases/tag/v1.0.1
[1.0.0]: https://github.com/SUSE/sesdev/releases/tag/v1.0.0
[0.2.2]: https://github.com/SUSE/sesdev/releases/tag/v0.2.2
[0.2.1]: https://github.com/SUSE/sesdev/releases/tag/v0.2.1
[0.2.0]: https://github.com/SUSE/sesdev/releases/tag/v0.2.0
[0.1.0]: https://github.com/SUSE/sesdev/releases/tag/v0.1.0
[0.0.1]: https://github.com/SUSE/sesdev/releases/tag/v0.0.1
