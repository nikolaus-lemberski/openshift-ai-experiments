# Serving models from Hugging Face


## S3 endpoint

Create a bucket in ODF.

```bash
oc apply -f k8s/bucketclaim.yml
```

Internal endpoint is "http://s3.openshift-storage.svc", get external with

```bash
oc get route s3 -n openshift-storage
```

Get AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY:

```bash
oc get secret modelstorage -n modelstorage -o jsonpath='{.data.AWS_ACCESS_KEY_ID}' | base64 --decode
oc get secret modelstorage -n modelstorage -o jsonpath='{.data.AWS_SECRET_ACCESS_KEY}' | base64 --decode
```
