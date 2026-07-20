# Event platform config

Shared Spring Cloud Config configuration for the real-time event streaming platform.

## Required environment variables

Set `JWT_SECRET` to the same strong value for `auth-service` and `api-gateway`.
It must contain at least 32 bytes for the HS256 signing key. The config deliberately
has no fallback secret, so neither service can start with a known credential.

`PRICING_SERVICE_URL` may be set when `order-service` cannot resolve pricing
through Eureka at `http://PRICING-SERVICE` (for example,
`http://pricing-service:8089` in a container network).

For production, set `TRACING_SAMPLING_PROBABILITY` to the intended trace sample
rate; the default is `0.1`.

Set `JPA_SHOW_SQL=true` only while diagnosing database behaviour. SQL logging is
disabled by default and open session in view is disabled for every JPA service.

## Health probes

All services inherit Spring Boot liveness and readiness state indicators from
`application.yml`. Their probe endpoints are `/actuator/health/liveness` and
`/actuator/health/readiness`.
