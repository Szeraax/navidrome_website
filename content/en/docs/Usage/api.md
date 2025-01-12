---
title: "API"
linkTitle: "API"
date: 2025-01-11
description: >
  How to use the Navidrome API
---

> Write a short markdown page for the ND docs on the API. Focus on the ND subsonic user (u) + salk (s) + token (t) query params and the native auth/JWT authentication. Provide at least 1 example of each with curl and link to the ND subsonic compatibility doc as well as the subsonic and opensonic API docs.

# **Navidrome API: Subsonic and JWT Authentication**

Navidrome supports both Subsonic API authentication and native JWT (JSON Web Token) authentication. This document provides an overview of how to use these authentication methods, focusing on the Subsonic user (u), salt (s), and token (t) query parameters, as well as JWT authentication. Examples using `curl` are provided for each method.

## **Subsonic API Authentication**

Navidrome is compatible with the

[Subsonic API](http://www.subsonic.org/pages/api.jsp)

v1.16.1, which allows users to authenticate using a combination of user (u), salt (s), and token (t) query parameters. This method is particularly useful for Subsonic clients that need to interact with Navidrome.

### **Subsonic Authentication Parameters**

* **User (u)**: The username of the Navidrome user.
* **Salt (s)**: A random string used to enhance security.
* **Token (t)**: A hashed value combining the user's password and the salt.

### **Example with curl**

To authenticate using the Subsonic API, you can use the following curl command:

~~~bash
curl "http://your-navidrome-server/rest/ping.view?u=yourusername&s=randomsalt&t=hashedtoken&v=1.16.1&c=yourclient"
~~~

Replace `yourusername`, `randomsalt`, and `hashedtoken` with your actual username, a random salt, and the hashed token, respectively. The `v` parameter specifies the API version, and `c` is the client identifier.

For more details on Subsonic API compatibility, visit the [Subsonic API Compatibility](https://www.navidrome.org/docs/developers/subsonic-api/) page.

## **JWT Authentication**

Navidrome also supports JWT authentication, which is a more modern and secure method for authenticating users. JWTs are compact, URL-safe tokens that can be used to verify the identity of a user.

### **Example with curl**

To authenticate using JWT, you first need to obtain a token. Once you have the token, you can use it in your requests as follows:

~~~bash
curl -H "Authorization: Bearer your_jwt_token" "http://your-navidrome-server/api/your-endpoint"
~~~

Replace `your_jwt_token` with the actual JWT you have obtained. This method is straightforward and leverages the security benefits of JWTs.

## **Additional Resources**

* For more information on the Subsonic API, visit the [Subsonic API Documentation](http://www.subsonic.org/pages/api.jsp).
* To explore extensions and additional features, check out the [OpenSubsonic](https://opensubsonic.netlify.app/) documentation.

By understanding and utilizing these authentication methods, you can effectively integrate Navidrome into your applications and services, ensuring secure and efficient access to your personal music streaming service.
