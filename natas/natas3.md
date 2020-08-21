# Natas3

- Username: natas3
- Password: `sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14`
- URL:      http://natas3.natas.labs.overthewire.org

# Walkthrough

When I visit the webpage I am greeted with the message: 

```
 There is nothing on this page 
```

I see the follow code in the source:

```html
<div id="content">
There is nothing on this page
<!-- No more information leaks!! Not even Google will find it this time... -->
</div>
```

Because they mention Google finding, I think to look at the `robots.txt` file.

```txt
User-agent: *
Disallow: /s3cr3t/
```

I visit: `/s3cr3t/`

I see a file `users.txt`

```
natas4:Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ
```

# Password

`Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ`
