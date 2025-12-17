---
description: Learn how to work around routing and hostname limitations on Ibexa Cloud using Fastly Forwarded Host.
---

# Routing and hostname limitations

When hosting on [[[= product_name_cloud =]]](ibexa_cloud.md), you may encounter platform limitations that affect [large multisite deployments](multisite.md) or projects with many domains.
[[= product_name_cloud =]] is built on Upsun infrastructure, with the following constraints:

- **TLS certificate hostname limit** - Let's Encrypt, the default certificate provider, allows a maximum of 100 hostnames per certificate.
- **Routing configuration size limit** - Upsun has a [128 KB limit on routing configuration size](https://fixed.docs.upsun.com/define-routes.html#route-limits), which large multisite installations with extensive routing rules can exceed.

## Available workarounds

If you encounter these limitations, you can consider the following solutions:

- [Simplify routing configuration](https://fixed.docs.upsun.com/define-routes.html#route-limits) by moving redirect routes to the application or collapse multiple route definitions into regular expression-based patterns
- [Use third-party TLS certificates](https://fixed.docs.upsun.com/domains/steps/tls.html) supporting more than 100 hostnames
- Use Fastly with the [`ibexa/fastly-forwarded-host` package][#ibexa-fastly-forwarded-host-package] to use Fastly as a CDN proxy layer in front of your [[= product_name_cloud =]] application

## `ibexa/fastly-forwarded-host` package

When user requests arrive at Fastly with the original hostname (for example, `site1.example.com`), Fastly forwards the request to your Upsun origin with the Upsun domain as the actual `Host` header and the original hostname in the `X-Forwarded-Host` header.
The `ibexa/fastly-forwarded-host` packag reads the `X-Forwarded-Host` header and sets the uses it for SiteAccess matching, URL generation, and routing decisions.
As a result, your application responds as if it received the request directly from the original hostname.

### Installation

Run the following command to install the package:

```bash
composer require ibexa/fastly-forwarded-host
```

Then, ensure that the bundle is enabled in your `config/bundles.php` file:

```php
<?php

return [
    // ...
    Ibexa\Bundle\FastlyForwardedHost\IbexaFastlyForwardedHostBundle::class => ['all' => true],
];
```

### Fastly configuration

Start by cloning your Fastly configuration by using the [Fastly CLI](fastly.md#quick-introduction-to-fastly-cLI).

#### Add domains

Add all required domains to your Fastly service.
You can add more than 100 domains.
Configure TLS certificates for your domains through Fastly.

#### Configure an override host

In the service configuration's hosts section, add or edit your origin host and set the **Override host** value to your Upsun domain, for example, `main-bvxea6i-mi7gjf6c2ascg.eu-5.platformsh.site` for production or `staging-bvxea6i-mi7gjf6c2ascg.eu-5.platformsh.site` for staging.

Use the Upsun environment URL as the origin host.
You can find this in your Upsun console or by running [`ibexa_cloud url`](https://cli.ibexa.co/) in your project.

See [Specifying an override host](https://www.fastly.com/documentation/guides/full-site-delivery/domains-and-origins/specifying-an-override-host/) for more information.

#### Add VCL snippets

Add the following VCL code to both `vcl_miss` and `vcl_pass` subroutines:

```vcl
if (req.http.Fastly-SSL) {
    set bereq.http.X-Forwarded-Proto = "https";
}

set bereq.http.X-Forwarded-Host = req.http.host;
```

#### Activate and test

Once all configuration changes are complete, activate the new Fastly configuration.
Purge the Fastly cache to ensure clean deployment, and test your domains to verify they're routing correctly.

With this configuration complete, Fastly handles all domain routing, eliminating Upsun size and hostname constraints.

