# Purpose

This is a patch to ngx_http_log_module, that provides ability to collect logs before request processing. This is useful when you need to collect request data regardless of response, e.g., for statistical purposes. Use in conjunction with syslog transport to gain guaranteed delivery.

# Changes in configuration

The option "early" added to log configuration:

```
access_log /var/log/nginx-access.log early;
```

# Known issues

Early log handler works in NGX_HTTP_POST_READ_PHASE phase in chain with ngx_http_realip_module, and which runs first is generally UB.
