# Zabbix-ntfy
Mediatype to add support for ntfy.sh services

Seems like no-one added support for ntfy.sh into zabbix, so I spent some time to get it working myself.
Might aswell share it. Pull requests are welcome.

## Setup
Download the zbx_ntfy.yaml file, go to *Alerts -> Mediatypes* and click **Import**.

Go to: *Administration -> Macros* and create Macros:

- `{$NTFY.URL}` The URL to send NTFY requests to. Just `https://ntfy.sh` if using the main instance.
- `{$ZABBIX.URL}` The URL to your Zabbix instance to include a clickable link in the notification (optional).
- `{$NTFY.USER}` The username of the NTFY account to use (optional - basic authentication).
- `{$NTFY.PASS}` The password of the NTFY account to use (optional - basic authentication).
- `{$NTFY.TOKEN}` The token created for the NTFY account to use (optional - token authentication).
  
> If you use a token instead of user/pass, leave the `{$NTFY.USER}` and `{$NTFY.PASS}` macros empty.

Enable a trigger action to use the NTFY Media Type: *Alerts -> Actions -> Trigger Actions*

Go to *Users -> Users* and add the ntfy.sh Media Type to your user. The *Send To* field is the ntfy topic;
So if you want your messages to be sent on ntfy to the "zabbix" topic, then enter "zabbix" here

## Customization
### Message Priority
Priorities are, by default, based on the Zabbix Triggers priority. To adjust the levels, go to *Alerts -> Media Types -> ntfy.sh* and adjust the `Priority_*` parameters to your liking. These options match the [NTFY API](https://docs.ntfy.sh/publish/#message-priority).

