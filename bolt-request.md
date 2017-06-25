# Bolt Request

A Bolt request is a regular HTTP request containing some expected custom headers.

Custom headers:

* [X-Bolt-App-Token](#x-bolt-app-token)

## X-Bolt-App-Token

Not all requests to Bolt server need to have the `X-Bolt-App-Token` header; only critical/sensitive requests \(where the origin of the request is important\) need to include this header. Bolt uses this header to identify your app as the origin of the request. Bolt then denies or grants the request only if your app has the right to make that request. An example of such an endpoint is `POST: /api/apps` which is used to install new apps. Bolt needs to be sure that your app is a system app, and the `X-Bolt-App-Token` header is the starting point of that security check.

To be safe though, it doesn't hurt to include the `X-Bolt-App-Token` in all your requests to Bolt but ensure you don't send such requests to other apps so that other apps don't use your app token to impersonate your app.

## X-Bolt-Locale

## X-Bolt-API-Ver

## X-Bolt-Perm-Token

## X-Bolt-User-Token

## X-Bolt-User-Name



