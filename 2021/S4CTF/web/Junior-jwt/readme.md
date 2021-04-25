# Junior JWT

--------

### **Description**

Just one of [them](http://junior-jwt.peykar.io/)!

[Files](https://github.com/nimilioum/WriteUps/blob/main/2021/S4CTF/web/Junior-jwt/junior-jwt_263b5c9dfde1cb164297e918fe179e2a606af1a7.txz)

---

### **Approach**

Well, the app uses JWT obviously! If we encode the jwt cookie
we will get this :

    {"typ":"JWT","alg":"RS256"}{"role":"guest","iat":1619352812,"nbf":1619352812}

According to the source code we need to change the role to "admin"
to get the flag. We have the public key but not the private key.

According to this [article](https://medium.com/@netscylla/json-web-token-pentesting-890bc2cf0dcd),
if we were able to change the alg to HS256 instead of RS256 we could use the
public key for signing our own JWT token. Awesome!

We can use [cyberchef](https://gchq.github.io/CyberChef/#recipe=JWT_Sign('secret','HS256'))
in order to sing our payload :

    {"role":"admin","iat":1619352812,"nbf":1619352812}
and pass the public key as key to sign.

Then, All we need is copy the output to our jwt token and reload the page.

    ok, you got that: S4CTF{7h3r3__iS_s733L_a_bUnch3__0u7_th3r3!!!}

Ta-daa, We got the flag!

---

### Flag 

S4CTF{7h3r3__iS_s733L_a_bUnch3__0u7_th3r3!!!}
