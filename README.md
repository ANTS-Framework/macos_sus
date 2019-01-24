macOS Software Update Server
============================

[![Build Status](https://travis-ci.org/ANTS-Framework/macos_sus.svg?branch=master)](https://travis-ci.org/ANTS-Framework/macos_sus)

This role uses the `defaults` command to manage the CatalogURL
preference in `/Library/Preferences/com.apple.SoftwareUpdate.plist`.

In theory, this preference could be set using a mobileconfig file.
Unfortunately, this will generate the following warning in munki:

*Warning: Cannot efficiently manage Apple Software updates*

See this [github issue](https://github.com/munki/munki/issues/511) for details and discussion.

Role Variables
--------------
```yml
# Configure updates over HTTP
# https://github.com/wdas/reposado/blob/master/docs/client_configuration.md#mojave-clients
macos_sus__SUDisableEVCheck_key: "SUDisableEVCheck"
macos_sus__SUDisableEVCheck_val: "false"
# Apple software update server preference domain and key
macos_sus__domain: "/Library/Preferences/com.apple.SoftwareUpdate.plist"
macos_sus__key: "CatalogURL"
# Your base url
macos_sus__server: "http://asus.pretendcorp.com"
# Final url based on OS version
macos_sus__sus_1010: "{{ macos_sus__server }}/content/catalogs/others/index-10.10-10.9-mountainlion-lion-snowleopard-leopard.merged-1.sucatalog"
macos_sus__sus_1011: "{{ macos_sus__server }}/content/catalogs/others/index-10.11-10.10-10.9-mountainlion-lion-snowleopard-leopard.merged-1.sucatalog"
macos_sus__sus_1012: "{{ macos_sus__server }}/content/catalogs/others/index-10.12-10.11-10.10-10.9-mountainlion-lion-snowleopard-leopard.merged-1.sucatalog"
macos_sus__sus_1013: "{{ macos_sus__server }}/content/catalogs/others/index-10.13-10.12-10.11-10.10-10.9-mountainlion-lion-snowleopard-leopard.merged-1.sucatalog"
macos_sus__sus_1014: "{{ macos_sus__server }}/content/catalogs/others/index-10.14-10.13-10.12-10.11-10.10-10.9-mountainlion-lion-snowleopard-leopard.merged-1.sucatalog"
```

Example Playbook
----------------
```yml
- hosts: all_macos
  vars:
    - macos_sus__server: "http://sus.myurl.io"
    - macos_sus__SUDisableEVCheck_val: "true"
  roles:
  - role: macos_sus
```

License
-------

GPLv3

Author Information
------------------
Part of the [ANTS Framework](https://ants-framework.github.io/)
