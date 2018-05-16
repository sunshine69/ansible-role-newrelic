newrelic-apm
=================

Description
------------

To install newrelic agent for various application and system


Requirements
------------


Role Variables
--------------

- `xvt_public_repo_url` - The xvt public repo -
  Default: "https://s3-ap-southeast-2.amazonaws.com/xvt-public-repo/pub"

- `win_newrelic_apm` - Required. Default value is below. This also document the field syntax.
  List of items to install.

```
win_newrelic_apm:
  - msi: "newrelic-infra.msi"
    base_url: "{{ xvt_public_repo_url }}"
    install_dir: "C:\Program Files\New Relic\newrelic-infra"
    create_file: "newrelic-infra.exe"
    newrelic_license_key: "{{ newrelic_license_key }}"
    newrelic_custom_attributes: "{{ newrelic_labels|default({}) }}"
    config_file_name: "newrelic-infra.yml"
    service_name: "newrelic-infra"

```

Fields descriptions:

- `msi` - Required - The installer msi file we download and run msiexec.exe

- `base_url` - Required - Default is the value of `xvt_public_repo_url`
  The base url we can download (exclude the msi file name above)

- `install_dir` - Required -
  The directory that the msi installer created. This is discovered by running the installer manually.

- `create_file` - Required - The file created after we run the installer so we wont run it again.
- `newrelic_license_key` - Optional - Default to `newrelic_license_key`
- `newrelic_custom_attributes` - Optional - The atributes, label we add into nee=wrelic config.

- `config_file_name` - Required
  The newrelic config file name. Run the installer to find out for each newrelic type.

- `service_name` - Required - The window service name.


Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: xvt-system-common
           system_common_ntp_service: chrony

License
-------

BSD

Author Information
------------------

XVT DevOps
