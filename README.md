# Ansible Role to deploy loki

This role can be used to deploy [loki](https://github.com/grafana/loki) on
Linux distributions with the *systemd* service manager. It's meant to
complement the [`patrickjahns.promtail`](https://galaxy.ansible.com/patrickjahns/promtail)
role.

## Compatibility

This role is compatible with systemd-based Linux distributions.

## Role Variables

The variables to control loki's configuration file merely provide a minimal
set of options for simple setups.
[Data retention](https://grafana.com/docs/loki/latest/operations/storage/retention/)
is configured per default with the table manager.

| Variable name                     | Description                                                                                                        |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| `loki_arguments`                  | arguments to pass to loki binary                                                                                   |
| `loki_data_retention_period`      | the period after which data is dismissed, e.g. `12h`, `3d`, `42w`                                                  |
| `loki_ingester`                   | a mapping with [`ingester`](https://grafana.com/docs/loki/latest/configuration/#ingester) settings                 |
| `loki_install_logcli`             | whether `logcli` shall be installed too                                                                            |
| `loki_log_level`                  | logging level                                                                                                      |
| `loki_schema_configs`             | a list of [`period_config`](https://grafana.com/docs/loki/latest/configuration/#period_config) settings            |
| `loki_server_http_listen_port`    | listen port for loki                                                                                               |
| `loki_server_http_listen_address` | listen address for loki                                                                                            |
| `loki_storage_config`             | a mapping with [`storage_config`](https://grafana.com/docs/loki/latest/configuration/#storage_config) settings     |
| `loki_system_user`                | user for running loki                                                                                              |
| `loki_system_group`               | group for running loki                                                                                             |
| `loki_version`                    | the loki version to deploy; if your play also defines a `promtail_version` it overrides whatever values is defined |

See the `defaults/main.yml` for default values and loki's
[configuration reference](https://grafana.com/docs/loki/latest/configuration/)
for details.
