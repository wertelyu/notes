# cookies

> `Cookies` are tiny pieces of data attached to requests that your browser sends. Their most important use is for `authentication` so that a web server can know if you are logged in or not.

There are 2 flags that we can set on a cookie, `HttpOnly` and `Secure`

## HttpOnly

The `HttpOnly` flag is an optional flag that can be included in a `Set-Cookie` header to tell the browser to prevent client side script from accessing the cookie.

```jsx
Set-Cookie: sess=123; path=/; HttpOnly
```

The biggest benefit here is protection against `Cross-Site Scripting`, or `XSS`. If a site has an `XSS` vulnerability then an attacker could exploit this to steal the cookies of a visitor, essentially `taking over` their session and logging in to the victim's account. If a piece of `JavaScript` attempts to read a cookie with the `HttpOnly` flag set, the browser will return an `empty` string instead of the cookie itself.

## Secure

The `Secur`e flag is another optional flag that can be included in a `Set-Cookie` header that instructs the browser that the cookie must only ever be sent over a secure connection.

```jsx
Set-Cookie: sess=123; path=/; Secure
```

Because a session cookie is incredibly sensitive it shouldn't be sent over an insecure connection as it would be trivial for an attacker to intercept it and abuse it. When the `Secure` flag is set the browser will not send the cookie over an insecure connection.

---

# Same-Site Cookies

> The `Same-Site Cookies` [specification](https://tools.ietf.org/html/draft-west-first-party-cookies-07) is still a draft but this new flag offers some very nice protection for our cookies. The main things to gain here are protection against [`Cross-Site Request Forgery](https://scotthelme.co.uk/csrf-protection-in-framework/) (CSRF)` attacks and `Cross-Site Script Inclusion (XSSI)`. `CSRF` relies on an attacker being able to send requests to another site from your browser.
> 

The `Same-Site` flag has two possible values:

## Lax

The `Lax` value for `Same-Site` is a good first step and offers a reasonable level of protection.

```jsx
Set-Cookie: sess=123; path=/; SameSite=Lax
```

With this flag set the browser will provide some protection against things like `CSRF` and `XSSI`, but not full protection, it should only be used as a defense in depth measure. For cross-site requests that use an unsafe `HTTP` method, like `POST`, the browser will not attach the cookie.

## Strict

The `Strict` value offers much more protection but does have some drawbacks.

```jsx
Set-Cookie: sess=123; path=/; SameSite=Strict
```

You can issue the `SameSite` flag without a value and `Strict` will be assumed:

```jsx
Set-Cookie: sess=123; path=/; SameSite
```

The cookie `will not` be attached to any cross-site requests, even for what we might consider to be a safe `HTTP` method like `GET` for a top-level navigation.

You can have 2 cookies: 

One is kind of a `basic` cookie that identifies you as a user and allows you to have the logged-in experience but if you want to do something sensitive like make a purchase or change something in your account you need the second cookie, the `real` cookie that allows you to do important things. The first cookie in this case wouldn't have the `SameSite` attribute set as it's a 'convenience' cookie, it doesn't really allow you to do anything sensitive and if the attacker can make cross-origin requests with that, nothing happens. The second cookie however, the sensitive cookie, would have the `SameSite` attribute set and the attacker can't abuse its authority in cross-origin requests. This is the ideal solution both for the user and for security.

---

# Cookie Prefixes

There are 2 different prefixes that you can add to your cookie.

## __Secure-

This prefix is the more relaxed in terms of the restrictions it applies but is still useful

```jsx
Set-Cookie: __Secure-sess=123; path=/; Secure
```

There are 2 requirements for cookies that have the `__Secure- prefix`:

1. Set with a `Secure` attribute
2. Set from a `URI` whose `scheme` is considered `secure` by the user agent.

## __Host-

The `__Host-` prefix is much more restrictive and offers a few additional protections.

```jsx
Set-Cookie: __Host-sess=123; path=/; Secure
```

There are 4 requirements the browser has to meet for cookies with the `__Host- prefix`:

1. Set with a `Secure` attribute.
2. Set from a URI whose "scheme" is considered "secure" by the user agent.
3. Sent only to the host which set the cookie. That is, a cookie named "__Host-cookie1" set from "[https://example.com](https://example.com/)" MUST NOT contain a "Domain" attribute (and will therefore be sent only to "example.com", and not to "subdomain.example.com").
4. Sent to every request for a host. That is, a cookie named "__Host-cookie1" MUST contain a "Path" attribute with a value of "/".

---

# The Perfect Cookie

```jsx
Set-Cookie: __Host-sess=123; path=/; Secure; HttpOnly; SameSite
```

---

[Tough Cookies](https://scotthelme.co.uk/tough-cookies/)
