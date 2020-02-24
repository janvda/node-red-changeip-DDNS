# changeip.com dynamic DNS update

This flow will regularly monitor if your public IP address didn't change (which can happen for some internet service providers after you have rebooted/restarted your router/modem).

If the flow detects that your public IP address has changed it will automatically update the IP address you have registered with [changeip.com](https://changeip.com) for the public hostname (`$changeip_hostname`) you have chosen and a message of successful/unsuccessful update is posted to slack channel with ID `$slack_channel_tweets`.

## Prerequisites

The following 5 environments variables must be set for this flow:

1. **changeip_user** : your changeip email address. It is needed together with your changeip password to change your public IP address.
2. **changeip_password** : changeip password.
3. **changeip_hostname** : your public hostname as chosen in [changeip.com](https://changeip.com) (e.g. `myhomegateway.onmypc.org`)
4. **slack_token** : the API token of your slack Bot (customs integrations)
5. **slack_channel_tweets** : The ID of the slack channel where the flow will post a message when your public IP address has changed.

## Testing

You can test the proper working of the IP address update by :
 1. trigger the `[set test ip address]` inject node.  This will change the public IP address stored in the flow context which forces an update of the public IP address next time we retrieve it (i.e. by next step)
 2. trigger the `[Get IP]` inject node

## Credits

The first part of the flow is based on : https://flows.nodered.org/flow/9559f217b08913702c38
For more information about the service used see: https://whatismyipaddress.com/api

The second part of the flow will update the IP address if changed.
See also https://discourse.nodered.org/t/how-to-change-dynamic-ip-address-changip-com-using-node-red/4164/2