# notes-bubbleran

# 7.2 Guide
https://hackmd.io/VfEMaBnDRT-EZ1Ow7s07BQ

curl --cert <PATH_TO_END_ENTITY_CLIENT_CERTIFICATE> --key <PATH_TO_END_ENTITY_CLIENT_KEY> --cacert <PATH_TO_CA_CERTIFICATE> --request POST \
https://<eic-host>/auth/realms/master/protocol/openid-connect/token \
--header 'content-type: application/x-www-form-urlencoded' \
--data "grant_type=client_credentials&client_id=<IAM_CLIENT_ID>"


curl --cacert <PATH_TO_CA_CERTIFICATE> --request POST \ https:///auth/realms/master/protocol/openid-connect/token \ --header ‘content-type: application/x-www-form-urlencoded’ \ --data “grant_type=client_credentials&client_id=<IAM_CLIENT_ID>&client_secret=<IAM_CLIENT_SECRET>”
