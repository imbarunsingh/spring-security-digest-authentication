                            Digest Authentication
                           ========================

Digest Authentication doesn't require sending the username and password across the wire in plaintext.
The server gives the client a one-time use string (a nonce) that it combines with the username, realm, password and the URI request. The client runs all of those fields through an MD5 hashing method to produce a hash key.
It sends this hash key to the server along with the username and the realm to attempt to authenticate.

Below would be the  Digest Authentication flow :

1.	Client makes request
Note: The username and password is not required for making the call and so no security concerns. 
It is just that hitting the endpoint without any credentials we get a nonce as part of the header response.
2.	Client gets back a nonce from the server and a 401 authentication request
3.	Client sends back the following response array (username, realm, generate_md5_key(nonce, username, realm, URI, password))
4.	The server takes username and realm (plus it knows the URI the client is requesting) and it looks up the password for that username. Then it goes and does its own version of generate_md5_key(nonce, username, realm, URI, password)
5.	It compares the output of generate_md5() that it got with the one the client sent, if they match the client sent the correct password. If they don't match the password sent was wrong.
                           

Running the example
===========================================

You can download the example code from Github. I will be using Postman to run the example. Here are the few steps you need to follow.

1. Open postman and enter url (localhost:9192).

2. Click on Authorization tab below the url and select Digest Auth from Type dropdown.

3. Enter username(spring), realm(Sparta), password(springDigestAuth), algorithm(MD5) and leave nonce as empty. Click Send button.

4. You will get 401 unauthorized as response like below.

![www-authenticate](https://cloud.githubusercontent.com/assets/8202635/26398983/f7a6202a-4098-11e7-9434-dc0b6ada0d6d.JPG)

5. If you see the Headers from the response, you will see "WWW-Authenticate" header. Copy the value of nonce field and enter in the nonce textfield.

6. Click on Send Button. Voila!!! You got the valid response.

![success](https://cloud.githubusercontent.com/assets/8202635/26399096/4726a61a-4099-11e7-9baa-9f50b4bb6ca6.JPG)

This is how we implement Digest Authentication with Spring Security. I hope you find this post informative and helpful.
