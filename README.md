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
