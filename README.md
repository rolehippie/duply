# duply

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/duply)
[![General Workflow](https://github.com/rolehippie/duply/actions/workflows/general.yml/badge.svg)](https://github.com/rolehippie/duply/actions/workflows/general.yml)
[![Readme Workflow](https://github.com/rolehippie/duply/actions/workflows/docs.yml/badge.svg)](https://github.com/rolehippie/duply/actions/workflows/docs.yml)
[![Galaxy Workflow](https://github.com/rolehippie/duply/actions/workflows/galaxy.yml/badge.svg)](https://github.com/rolehippie/duply/actions/workflows/galaxy.yml)
[![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/duply)](https://github.com/rolehippie/duply/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/badge/role-rolehippie.duply-blue)](https://galaxy.ansible.com/rolehippie/duply)

Ansible role to install duply as a simple backup solution.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of content

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [duply_default_command](#duply_default_command)
  - [duply_default_day](#duply_default_day)
  - [duply_default_gpg_key](#duply_default_gpg_key)
  - [duply_default_gpg_opts](#duply_default_gpg_opts)
  - [duply_default_gpg_passwd](#duply_default_gpg_passwd)
  - [duply_default_hour](#duply_default_hour)
  - [duply_default_max_age](#duply_default_max_age)
  - [duply_default_max_full](#duply_default_max_full)
  - [duply_default_minute](#duply_default_minute)
  - [duply_default_month](#duply_default_month)
  - [duply_default_variables](#duply_default_variables)
  - [duply_default_verbosity](#duply_default_verbosity)
  - [duply_default_volsize](#duply_default_volsize)
  - [duply_default_weekday](#duply_default_weekday)
  - [duply_profiles](#duply_profiles)
  - [duply_target](#duply_target)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.10`

## Default Variables

### duply_default_command

Default backup command

#### Default value

```YAML
duply_default_command: full+purgeFull --force
```

### duply_default_day

Default day cron entry

#### Default value

```YAML
duply_default_day: '*'
```

### duply_default_gpg_key

Default GnuPG key

#### Default value

```YAML
duply_default_gpg_key: disabled
```

### duply_default_gpg_opts

Default GnuPG options

#### Default value

```YAML
duply_default_gpg_opts: --pinentry-mode loopback
```

### duply_default_gpg_passwd

Default GnuPG password

#### Default value

```YAML
duply_default_gpg_passwd:
```

### duply_default_hour

Default hour cron entry

#### Default value

```YAML
duply_default_hour: '5'
```

### duply_default_max_age

Default max age

#### Default value

```YAML
duply_default_max_age: 1M
```

### duply_default_max_full

Default max full

#### Default value

```YAML
duply_default_max_full: '1'
```

### duply_default_minute

Default minute cron entry

#### Default value

```YAML
duply_default_minute: '5'
```

### duply_default_month

Default month cron entry

#### Default value

```YAML
duply_default_month: '*'
```

### duply_default_variables

Default variables list

#### Default value

```YAML
duply_default_variables: []
```

#### Example usage

```YAML
duply_default_variables:
  - key: aws_access_key_id
    value: S62L74JZVLLKQ5E9077R
  - key: aws_secret_access_key
    value: xmGiLiTMBGzMMwRh+jAYBvn9C7roiuDqVHDF_+RI
```

### duply_default_verbosity

Default verbosity level

#### Default value

```YAML
duply_default_verbosity: '1'
```

### duply_default_volsize

Default volume size

#### Default value

```YAML
duply_default_volsize: '1024'
```

### duply_default_weekday

Default weekday cron entry

#### Default value

```YAML
duply_default_weekday: '*'
```

### duply_profiles

List of profile definitions

#### Default value

```YAML
duply_profiles: []
```

#### Example usage

```YAML
duply_profiles:
  - name: owncloud
    includes:
      - /var/lib/owncloud
  - name: external
    target: ftp://username:p455w0rd@ftp.example.com
    ansible.builtin.command: full+verify+purge --force
    gpg_key: 52DCE5AE1FC80340A33894F5D583668622CDE10E
    gpg_passwd: p455w0rd
    max_age: 1W
    max_full: '7'
    verbosity: '1'
    minute: '0'
    hour: '5'
    day: '*'
    month: '*'
    weekday: '*'
    includes:
      - /var/lib/foo
      - /var/lib/bar
```

### duply_target

Target for backups

#### Default value

```YAML
duply_target:
```

#### Example usage

```YAML
s3://backup.example.com
```

## Discovered Tags

**_duply_**

**_ipsec_**


## Dependencies

- None

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
