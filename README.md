# mumble-web

This role installs and configures [mumble-web](https://github.com/Johni0702/mumble-web).
The [webrtc version](https://github.com/Johni0702/mumble-web/tree/webrtc) is used.

## Requirements

Debian.

## Role Variables

| Name       | Required/Default | Description                                 |
| ---------- | :--------------: | ------------------------------------------- |
| mumble_web |    _required_    | See [Mumble web config](#mumble-web-config) |

## Mumble web config
The dict mumble_web can have the following entries:

| Name        |   Required/Default    | Description                                                                                                                                                                                                  |
| ----------- | :-------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| build_base  |        `/tmp`         | The base folder for building mumble-web                                                                                                                                                                      |
| deploy_path | `/var/www/mumble-web` | The path to install mumble-web into                                                                                                                                                                          |
| version     |      _required_       | The sha256 hash of the commit in [mumble-web](https://github.com/Johni0702/mumble-web) to use.                                                                                                               |
| checksum    |      _required_       | Checksum of the downloaded archive from github.                                                                                                                                                              |
| reinstall   |        `false`        | Whether to reinstall mumble-web even if the same version is already installed.                                                                                                                               |
| config      |         `{}`          | The local config for mumble-web. This should be dict. It is translated to a javascript config file. See [config.js](https://github.com/Johni0702/mumble-web/blob/webrtc/app/config.js) for possible options. |

## Example

```yml
mumble_web:
  build_base: /var/tmp/
  version: 95dbf255e103e100ecd9e8abf56c68d6315fa918
  checksum: sha256:5ead2f664b7690a4a1a4c65b1e88b854e8e1c2c036915814fd7af9921121dcd7
  config:
    connectDialog:
      address: false
      port: false
    settings:
      voiceMode: ptt
      vadLevel: 0.5
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Tim Neumann (neumantm)](https://github.com/neumantm) _tim.neumann@stuvus.uni-stuttgart.de_
