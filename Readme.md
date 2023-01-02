# Notes

Just some random notes.

## gsutil

Can [print an access token](https://cloud.google.com/sdk/gcloud/reference/auth/print-access-token) to be used in e.g. curl like this:

(replace $bucket and $path, $path must url-escape slashes etc.)

```sh
curl 'https://storage.googleapis.com/storage/v1/b/$bucket/o/$path' -H "Authorization: Bearer $(gcloud auth print-access-token)"
```

## [crane](https://github.com/google/go-containerregistry/tree/main/cmd/crane)

seems useful to e.g. show image sizes or to extract or cat individual files from an image

## macos

### free used ports (e.g. for local load testing)

(from brew siege package)

macOS has only 16K ports available that won't be released until socket
TIME_WAIT is passed. The default timeout for TIME_WAIT is 15 seconds.
Consider reducing in case of available port bottleneck.

You can check whether this is a problem with netstat:

    # sysctl net.inet.tcp.msl
    net.inet.tcp.msl: 15000

    # sudo sysctl -w net.inet.tcp.msl=1000
    net.inet.tcp.msl: 15000 -> 1000

