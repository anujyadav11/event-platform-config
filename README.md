# Event platform config

Shared Spring Cloud Config configuration for the real-time event streaming platform.

## Required environment variables

Set `JWT_SECRET` to the same strong value for `auth-service` and `api-gateway`.
It must contain at least 32 bytes for the HS256 signing key. The config deliberately
has no fallback secret, so neither service can start with a known credential.

`PRICING_SERVICE_URL` may be set when `order-service` cannot reach pricing at
`http://localhost:8089` (for example, `http://pricing-service:8089` in a container network).

For production, set `TRACING_SAMPLING_PROBABILITY` to the intended trace sample
rate; the default is `0.1`.
