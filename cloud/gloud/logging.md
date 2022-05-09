Here're some examples of queries to logging service:

Find in `gae_app` resource for `api-coupon` module all records withing timestamp range:
```
resource.type="gae_app"
resource.labels.module_id="api-coupon"
timestamp>="2021-12-17T12:00:00Z" AND timestamp<="2021-12-17T12:30:00Z"
```