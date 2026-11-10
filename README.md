[![CI](https://github.com/de-it-krachten/ansible-role-telegraf/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-telegraf/actions?query=workflow%3ACI)


# ansible-role-telegraf

Installs and configures Telegraf, pushing system metrics to InfluxDB 2.x.



## Dependencies

#### Roles
None

#### Collections
None

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- Red Hat Enterprise Linux 10<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- RockyLinux 10
- OracleLinux 8
- OracleLinux 9
- OracleLinux 10
- AlmaLinux 8
- AlmaLinux 9
- AlmaLinux 10
- Debian 12 (Bookworm)
- Debian 13 (Trixie)
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Ubuntu 26.04 LTS
- Fedora 43
- Fedora 44<sup>1</sup>

Note:
<sup>1</sup> : no automated testing is performed on these platforms


## Role Variables
### defaults/main.yml
<pre><code>
telegraf_influx_repo_key_url: "https://repos.influxdata.com/influxdata-archive.key"

telegraf_influx_repo_keyring: "/etc/apt/keyrings/influxdata-archive.gpg"

telegraf_influx_repo_url: "https://repos.influxdata.com/debian"
telegraf_influx_deb_suite: "stable"
telegraf_influx_deb_component: "main"

telegraf_influx_rpm_repo_url: "https://repos.influxdata.com"

telegraf_config_path: "/etc/telegraf/telegraf.conf"

telegraf_interval: 10s

telegraf_enable_sensors: false
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'telegraf'
  hosts: all
  become: 'yes'
  vars:
    molecule_driver: '{{ lookup(''env'', ''MOLECULE_DRIVER_NAME'') }}'
    influxdb_url: http://127.0.0.1:8080
    influxdb_token: token
    influxdb_org: org
    influxdb_bucket: bucket
    influxdb_skip_tls_verify: true
  tasks:
    - name: Include role 'telegraf'
      ansible.builtin.include_role:
        name: telegraf
</pre></code>
