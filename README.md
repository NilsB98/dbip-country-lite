# dbip-country-lite

The [DB-IP IP to Country Lite](https://db-ip.com/db/download/ip-to-country-lite) database (MMDB) packaged as an OCI image, so it can be mounted as a Kubernetes [image volume](https://kubernetes.io/docs/tasks/configure-pod-container/image-volumes/).

```
ghcr.io/nilsb98/dbip-country-lite:YYYY-MM
```

The image is `FROM scratch` and contains a single file, `/dbip-country-lite.mmdb`. It can be read by any MaxMind DB reader, which finds the country code at `country.iso_code`.

```yaml
volumes:
  - name: geoip
    image:
      reference: ghcr.io/nilsb98/dbip-country-lite:2026-10
      pullPolicy: IfNotPresent
```

A scheduled workflow publishes each monthly release as a `YYYY-MM` tag (plus `latest`) for `linux/amd64` and `linux/arm64`. To publish a specific month by hand, run the workflow with the `month` input.

## License

The database is © DB-IP.com and licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Anything that uses it must credit DB-IP, for example:

```html
<a href="https://db-ip.com">IP Geolocation by DB-IP</a>
```

This repository only repackages the unmodified file.
