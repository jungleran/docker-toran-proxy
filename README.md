# Docker Toran Proxy

## Quick start

```bash
docker run --name toran-proxy -d \
    -p 8080:80 \
    cedvan/toran-proxy:1.1.6
```
Go in your browser to **localhost:8080**

## Save data

```bash
docker run --name toran-proxy -d \
    -v /opt/toran-proxy:/var/www \
    cedvan/toran-proxy:1.1.6
```

## Enabled HTTPS

```bash
docker run --name toran-proxy -d \
    -p 8443:443
    -e "TORAN_PROXY_HTTPS=true" \
    -v /opt/toran-proxy/certs:/var/www/certs \
    cedvan/toran-proxy:1.1.6
```
Add **toran-proxy.key** and **toran-proxy.crt** in folder **certs**

## Toran Proxy Options

*Please refer the docker run command options for the `--env-file` flag where you can specify all required environment variables in a single file. This will save you from writing a potentially long docker run command. Alternately you can use fig.*

Below is the complete list of available options that can be used to customize your toran proxy installation.

- **TORAN_PROXY_HOST**: The hostname of the toran proxy server. Defaults to `localhost`
- **TORAN_PROXY_HTTPS**: Set to `true` to enable https support, Defaults to `false`. **Do not forget to add the certificates files**
- **TORAN_PROXY_PACKAGIST**: Enabled packagist proxy repository. Possible configuration options are `proxy` and `false`. Defaults to `proxy`
- **TORAN_PROXY_SYNC**: Snchronization mode. Possible configuration options are `lazy`, `all` and `new`. Defaults to `lazy`
    - `lazy` : Every archive is built on demand when you first install a given package's version
    - `new` : Tags newer than the oldest version you have used will be pre-cached as soon as they are available
    - `all` : All releases will be pre-cached as they become available

## Toran Proxy License

By default, Toran proxy license is for personal use.
You can add a license from the Toran proxy interface