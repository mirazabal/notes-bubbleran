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



curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request GET 'https://<eic-host>/app-lifecycle-management/v3/apps/<APP_ID>' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <access-token>'



curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request PUT 'https://<eic-host>/app-lifecycle-management/v3/apps/<APP_ID>/mode' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <access-token>' \
-d '{"mode": "ENABLED"}'


curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request POST 'https://<eic-host>/app-lifecycle-management/v3/app-instances' \
--header 'accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <access-token>' \
-d '{
  "appId": "<APP_ID>"
}'


curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request POST 'https://<eic-host>/app-lifecycle-management/v3/app-instances/<APP_INSTANCE_ID>/deployment-actions' \
--header 'accept: application/json' \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer <access-token>" \
-d @- <<EOF
{
  "type": "DEPLOY",
  "additionalData": {
    "componentInstances": [
      {
        "name": "$RAPP_NAME",
        "properties": {
          "timeout": 5,
          "userDefinedHelmParameters": {
            "platformCaCertSecretName": "<PLATFORM_CA_CERT_SECRET>",
            "platformCaCertFileName": "<PLATFORM_CA_CERT_FILENAME>",
            "eicHostUrl": "https://<eic-host>",
            "appSecretName": "<APP_MTLS_SECRET>",
            "logEndpoint": "<LOG_ENDPOINT>",
            "appKeyFileName": "<APP_PRIVATE_KEY>",
            "appCertFileName": "<APP_CERTIFICATE>",
            "kafkaCaCertSecretName": "<KAFKA_CA_CERT_SECRET>"
          }
        }
      }
    ]
  }
}
EOF


curl --cacert <PATH_TO_CA_CERTIFICATE> --location --request GET 'https://<eic-host>/app-lifecycle-management/v3/app-instances/<APP_INSTANCE_ID>' \
--header 'accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <access-token>'




