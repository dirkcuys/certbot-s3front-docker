Docker image to run certbot with the [certbot-s3front](https://github.com/dlapiduz/certbot-s3front) plugin. This is useful if you are running a site using AWS Cloudfront and want to use a LetsEncrypt SSL certificate.

## Building the image

```
docker build . -t certbot-s3front
```

## Running the image

Put your AWS_ACCESS_KEY_ID & AWS_SECRET_ACCESS_KEY in a file called env.list

```
echo AWS_ACCESS_KEY_ID=YOUR_ID >> env.list
echo AWS_SECRET_ACCESS_KEY=YOUR_KEY >> env.list
```

Run certbot,

```
docker run --rm --name lets-encrypt -it \
    -v ./letsencrypt/:/etc/letsencrypt \
    --env-file env.list \
    certbot-s3front \
        --init \
        --agree-tos \
        -a certbot-s3front:auth \
        -i certbot-s3front:installer \
        --certbot-s3front:auth-s3-bucket YOUR_AWS_S3_BUCKET \
        --certbot-s3front:installer-cf-distribution-id YOUR_AWS_CLOUDFRONT_DISTRIBUTION_ID \
        -d YOUR_DOMAIN
```

Be sure to replace YOUR_AWS_S3_BUCKET, YOUR_AWS_CLOUDFRONT_DISTRIBUTION_ID and YOUR_DOMAIN with the appropriate values.
