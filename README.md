## certbot-httpreq project

[![PyPI pyversions](https://img.shields.io/pypi/pyversions/certbot-httpreq.svg)](https://pypi.org/project/certbot-httpreq/)
[![PyPI version shields.io](https://img.shields.io/pypi/v/certbot-httpreq.svg)](https://pypi.org/project/certbot-httpreq/)
[![Documentation Status](https://readthedocs.org/projects/certbot-httpreq/badge/?version=latest)](https://certbot-httpreq.readthedocs.io/)

certbot-httpreq is a free and open-source, we develop it to customize and send authenticator and installer certbot requests through HTTP protocol.

## Table of contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [Configuration](#configuration)

## <a name="installation"></a>Installation

`pip install certbot-httpreq`

## <a name="usage"></a>Usage

```
certbot \
  --agree-tos \
  --text \
  -a certbot-httpreq:auth \
  -i certbot-httpreq:installer \
  --certbot-httpreq:auth-config /etc/letsencrypt/certbot-httpreq.yml \ # not required
  --certbot-httpreq:installer-config /etc/letsencrypt/certbot-httpreq.yml \ # not required
  run
```

Configuration file must be placed in /etc/letsencrypt/certbot-httpreq.yml or be specified with arguments --certbot-httpreq:auth-config and --certbot-httpreq:installer-config.

## <a name="configuration"></a>Configuration

You can customize authenticator HTTP requests for perform and cleanup phases and also installer HTTP requests for deploy phase.

```
# authenticator
perform:
  ### perform HTTP URI ###
  uri: http://localhost
  ### perform HTTP path ###
  path: /
  ### perform HTTP method: PUT or POST ###
  method: PUT
  ### perform HTTP format: json or form-urlencoded ###
  format: json
  ### parameter name in HTTP query string for challenge string
  param\_challenge: ~
  ### parameter name in HTTP body for validation string
  param\_validation: ~
  ### perform HTTP custom headers
  headers: {}
  ### perform HTTP connection timeout
  timeout: ~
  ### perform HTTP SSL verify
  verify: ~
cleanup:
  ### cleanup HTTP uri ###
  uri: http://localhost
  ### cleanup HTTP path ###
  path: /
  ### cleanup HTTP method: DELETE, PUT or POST ###
  method: DELETE
  ### cleanup HTTP format: json or form-urlencoded ###
  format: json
  ### parameter name in HTTP query string for challenge string
  param\_challenge: ~
  ### cleanup HTTP custom headers
  headers: {}
  ### cleanup HTTP connection timeout
  timeout: ~
  ### cleanup HTTP SSL verify
  verify: ~

# installer
deploy:
  ### deploy HTTP URI ###
  uri: http://localhost
  ### deploy HTTP path ###
  path: /
  ### deploy HTTP method: POST or PUT or PATCH ###
  method: POST
  ### deploy HTTP format: json or form-urlencoded ###
  format: json
  ### deploy HTTP custom headers
  headers: {}
  ### deploy HTTP connection timeout
  timeout: ~
  ### deploy HTTP SSL verify
  verify: ~
```
