# notes-bubbleran

# 7.2 Guide
https://hackmd.io/VfEMaBnDRT-EZ1Ow7s07BQ

curl --cert <PATH_TO_END_ENTITY_CLIENT_CERTIFICATE> --key <PATH_TO_END_ENTITY_CLIENT_KEY> --cacert <PATH_TO_CA_CERTIFICATE> --request POST \
https://<eic-host>/auth/realms/master/protocol/openid-connect/token \
--header 'content-type: application/x-www-form-urlencoded' \
--data "grant_type=client_credentials&client_id=<IAM_CLIENT_ID>"


curl --cacert <PATH_TO_CA_CERTIFICATE> --request POST \ https://eic.stsn22p1eic08.stsoss.sero.xgic.ericsson.se/auth/realms/master/protocol/openid-connect/token \ --header ‘content-type: application/x-www-form-urlencoded’ \ --data “grant_type=client_credentials&client_id=<IAM_CLIENT_ID>&client_secret=<IAM_CLIENT_SECRET>”


curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request POST 'https://eic.stsn22p1eic08.stsoss.sero.xgic.ericsson.se/app-onboarding/v2/app-packages' \
--header 'Authorization: Bearer <access-token>' \
--header 'accept: application/json' \
--form 'file=@"<PATH_TO_CSAR>/examplerAppPackage.csar"'


curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request GET 'https://eic.stsn22p1eic08.stsoss.sero.xgic.ericsson.se/app-onboarding/v2/onboarding-jobs/<JOB_ID>' \
--header 'Authorization: Bearer <access-token>' \
--header 'accept: application/json'


curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request POST 'https://eic.stsn22p1eic08.stsoss.sero.xgic.ericsson.se/app-lifecycle-management/v3/apps/<APP_ID>/initialization-actions' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <access-token>' \
-d '{"action": "INITIALIZE"}'
