# GCloud

## Basic actions

Change project from `Cloud Shell`:

```bash
gcloud config set project $PROJECT_ID
```

## Environment variables

`GCP_PROJECT`

Set the current GCP project ID.

`GOOGLE_CREDENTIALS`

Content of the creds file, can be set by using:

```bash
  export GOOGLE_CREDENTIALS=$(cat $CRED_FILE_PATH)
```

`GOOGLE_CLOUD_KEYFILE_JSON`

Path to the authentification JSON key file.
