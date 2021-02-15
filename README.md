Jitsi
=========

Installs Jitsi-Meet

Requirements
------------

None

Role Variables
--------------

this is only a selection of variables, full list is in _defaults/main.yml_ .

|Variable|Description|required|default|
|---|---|---|---|
|jitsi_hostname|Hostname of Jitsi|X||
|jitsi_external_ip| External IP of Jitsi|X| |
|jitsi_external_port| External IP of Jitsi| | 443|
|jitsi_optimal_browsers|browsers we allow for jitsi||chrome, chromium, nwjs, electron, safari|
|jitsi_unsupported_browsers| list of unsupported browsers (they cannot join!) ||firefox|
|jitsi_tls_cert|TLS Cert| (X) needs change when letsencrypt ist not used |/etc/letsencrypt/live/{{ jitsi_hostname }}/fullchain.pem|
|jitsi_tls_privkey| TLS Cert Privkey| (X) needs change when letsencrypt ist not used |/etc/letsencrypt/live/{{ jitsi_hostname }}/privkey.pem|
|jitsi_authentication_enabled|Enables authentication over XMPP backend||False (everyone can use your server for meetings!) |
|jitsi_users|List of users (see below)|(X) Without effect when jitsi authentication disabled||
|jitsi_turncredentials_secret|Secret string for TURN (set on install; 16 chars, alphanumeric)|X||
|jitsi_jicofo_secret|(Undocumented) Secret string for jicofo XMPP login (set on install; 8 chars, alphanumeric)|X||
|jitsi_jicofo_password|(Undocumented) Secret string for jicofo (set on install; 8 chars, alphanumeric)|X||
|jitsi_jigasi_secret|(Undocumented) Secret string for jicofo XMPP login (set on install; 8 chars, alphanumeric)|X||
|jitsi_jigasi_password|(Undocumented) Secret string for jicofo (set on install; 8 chars, alphanumeric)|X||
|jitsi_videobridge_secret|(Undocumented) Secret string for jicofo XMPP login (set on install; 8 chars, alphanumeric)|X||
|jitsi_videobridge_password|(Undocumented) Secret string for jicofo (set on install; 8 chars, alphanumeric)|X||
|jitsi_jibri_password|(Undocumented) Secret string for jibri (set on install; 8 chars, alphanumeric)|X||
|jitsi_footer_powered_by_name | your url ||jitsi|
|jitsi_footer_powered_by_url | your url || https://jitsi.org |
|jitsi_footer_powered_dataprotection_text | your dataprotection policy (linktext) |||
|jitsi_footer_powered_dataprotection_url | your dataprotection policy (url) |||
|jitsi_footer_powered_imprint_text | your imprint (linktext) |||
|jitsi_footer_powered_imprint_url | your imprint (url) |||
|jitsi_support_url | custom support page of your organisation || https://community.jitsi.org |
|jitsi_sip_server| SIP Server |X||
|jitsi_sip_account| SIP account (without server) |X||
|jitsi_sip_password| SIP account password |X||
|jitsi_sip_default_room| Default SIP Room ||siptest|
|jitsi_sip_enabled| Should SIP be enabled ||yes|
|jitsi_jibri_enabled| Should Jitsi Broadcasting Infrastructure be enabled | |True (set to False to disable recordings) |
|jitsi_jibri_recording_directory| Where to save Jibri recordings | | /var/recordings|

If ```jitsi_sip_enabled``` is set to ```no``` Jigasi will be installed anyways, but the service will be disabled and configs 
won't be templated. This also works when Jigasi had already a working config. In any case ```jitsi_jigasi_password``` and 
```jitsi_jigasi_secret``` have to be set.
DON'T ENABLE JIGASI WHILE AUTHENTICATION IS DISABLED!

Dependencies
------------

none.


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: jitsi, tags: jitsi }

License
-------

MIT

Author Information
------------------

Tim Jonathan Heske <tjheske@inwx.de>
