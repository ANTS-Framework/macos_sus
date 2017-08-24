macOS Software Update Server
============================

Description
------------
This role uses the :code:`defaults` command to manage the CatalogURL
preference in :code:`/Library/Preferences/com.apple.SoftwareUpdate.plist`.

In theory, this preference could be set using a mobileconfig file.
Unfortunately, this will generate the following warning in munki:

*Warning: Cannot efficiently manage Apple Software updates*

See this `github issue <https://github.com/munki/munki/issues/511>`_ for more details and discussion.

Usage
------
Have a look at the default values and use group\_vars to change them according to your liking.
