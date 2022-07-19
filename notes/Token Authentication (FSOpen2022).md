---
attachments: [Clipboard_2022-07-19-19-54-46.png]
tags: [Notebooks/Authentication]
title: Token Authentication (FSOpen2022)
created: '2022-07-19T11:11:27.203Z'
modified: '2022-07-19T12:43:41.837Z'
---

# Token Authentication (FSOpen2022)

## [The Ins and Outs of Token-Based Authentication](https://www.digitalocean.com/community/tutorials/the-ins-and-outs-of-token-based-authentication#toc-how-token-based-works)

Reasons for tokens are:
- stateless and scalable servers
- mobile application ready
- pass auth to other apps
- extra security

### Server-Based Authentication (the traditional way)

HTTP is stateless. If we authenticate a user with a username and password, then on the next request, our application won't know who we are unless we authenticate again.

Server-based authentication allows apps to remember the logged-in user by storing the logged-in user information on the server, usually in memory or stored on the disk. 

#### The problem with server-based authentication

- **Sessions:** more overhead on the server since it will need to create a record every time a user is authenticated
- **CORS:** could run into CORS problems with mobile devices

### How Token-Based Works

Token-based is stateless, no information is stored about the user on the server or in a session. 

A general process of token-based authentication:
1. User Requests Access with Username / Password
2. Application validates credentials
3. Application provides a signed token to the client
4. Client stores that token and sends it along with every request
5. Server verifies token and responds with data

Every request requires the token. This is sent in the HTTP header. The server also needs to accept request from all domains using `Access-Control-Allow-Origin: *`

#### The Benefits of Tokens
- **Stateless and Scalable:** The token itself stores the data about the user. Therefore, the user's request can be sent and handled by any of the servers (load balancing). On the other hand, sessions make it so that a logged-in user is constantly sent to the same server that stored their user information. This can cause heave traffic.

_extra: [The Anatomy of a JSON Web Token](https://www.digitalocean.com/community/tutorials/the-anatomy-of-a-json-web-token)_


## FSOpen Token Authentication

![](@attachment/Clipboard_2022-07-19-19-54-46.png)

Install the `jsonwebtoken` package
```bash
npm i jsonwebtoken
```

Search for the user from the database by the username attached to the request:
```js
const user = await User.findOne({ username })
```

Check the password attached to the request and check if it matches the hashed passwords on the database:
```js
await bcrypt.compare(body.password, user.passwordHash)
```

If the user is not found or the password is incorrect, the server responds with a 401. 
```js
if (!(user && passwordCorrect)) {
    return res.status(401).json({
      error: 'invalid username or password'
  })
};
``` 

If the password _is_ correct, a token is created with `jwt.sign`. The token would contain the username and the user id in a digitally signed form.
```js
const userForToken = {
  username: user.username,
  id: user._id,
}

const token = jwt.sign(userForToken, process.env.SECRET)
```




