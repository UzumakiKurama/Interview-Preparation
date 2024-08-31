# Cookies

A cookie (also known as a web cookie or browser cookie) is a small piece of data a server sends to a user's web browser. The browser may store cookies, create new cookies, modify existing ones, and send them back to the same server with later requests. Cookies enable web applications to store limited amounts of data and remember state information; by default the HTTP protocol is stateless.

Cookies are mainly used for three purposes:

+ Session management: User sign-in status, shopping cart contents, game scores, or any other user session-related details that the server needs to remember.
Personalization: 
+ User preferences such as display language and UI theme.
+ Tracking: Recording and analyzing user behavior.

```js
console.log(document.cookie);
// logs "yummy_cookie=choco; tasty_cookie=strawberry"

document.cookie = "yummy_cookie=blueberry";

console.log(document.cookie);
// logs "tasty_cookie=strawberry; yummy_cookie=blueberry"

```

## How Cookies are set in browser ? 
Cookies are set through a collaboration between the web server and your browser. Here's a breakdown of the process:

1. Server Sends a Cookie: When you visit a website, the web server may choose to send you a cookie. It does this by including a <span style="background-color: white;color: black">&nbsp;Set-Cookie&nbsp;</span> header in the HTTP response that it sends back to your browser. This header contains information about the cookie, such as its name, value, expiry time, and other attributes.

2. Browser Receives and Stores:  Your browser receives the Set-Cookie header along with the rest of the response. If the cookie is valid (e.g., not expired), the browser stores it internally. These cookies are typically stored in a special file on your device.



# Web Storage API 
WebStorage API is a bunch of tools built into the web browsers that allow websites to store data on the client side. This data is usually stored in a key-value fashion like a object. There 2 types of web storages :- 

1. LocalStorage :-  Data stored here will persist even after the browser tab/browser is closed and will still be there when browser is reopened. This type of data can be usefull to store website performances or login information.

2. SessionStorage :- Data stored here will get deleted once your current browsing session is closed. This type of storage could be usefull when we want to track information related to items in cart.

```js
localStorage.setItem("user-name", "Abhijeet Behera");
localStorage.getItem("user-name");
// Same for sessionStorage
```

    Cookies and local storage serve different purposes. Cookies are primarily for reading server-side, local storage can only be read by the client-side.

    Apart from being an old way of saving data, Cookies give you a limit of 4096 bytes (4095, actually) — it's per cookie. 
    
    Local Storage is as big as 10MB per domain localStorage is an implementation of the Storage Interface. It stores data with no expiration date, and gets cleared only through JavaScript, or clearing the Browser Cache / Locally Stored Data — unlike cookie expiry.