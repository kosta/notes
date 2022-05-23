# Notes

Just some random notes.

## gsutil

Can [print an access token](https://cloud.google.com/sdk/gcloud/reference/auth/print-access-token) to be used in e.g. curl like this:

(replace $bucket and $path, $path must url-escape slashes etc.)

```sh
curl 'https://storage.googleapis.com/storage/v1/b/$bucket/o/$path' -H "Authorization: Bearer $(gcloud auth print-access-token)"
```
