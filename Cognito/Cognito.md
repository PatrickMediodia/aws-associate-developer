- gives users an identity to interact with our web or mobile application
![[Pasted image 20240501221114.png]]

give users an identity to interact with our web or mobile application
    - this is different from IAM which manages the users in AWS
        - cognito users are the users of your web or mobile applications which sit outside of AWS
    - that is why it is called cogito, gives identity to users we don't know about yet

User Pool
    - sign in functionalkity for app users
    - integrates well with API gateway & application load balancer (I haven't tried this yet)

    - serverless database of users for you web and mobile applications
    - what can you do?
        - simple login (email/password)
        - reset password
        - email and phone number verfication
        - MFA
        - federated identities (Facebook, Google, SAML)
    - other features
        - block users if their credentials are compromised elsewhere
            - scans web for compromised credentials and will let your user know
    - login sends back a JWT
        - 

Identitfy Pools (Federated Identity)
    - provide temporary credentials to users so they can access AWS resources directly
    - integrates with AWS identity pools as an identity provider

Show tour around the console
    - show the user po

NOTE: YOU CAN USE EACH SERVICE INDEPENDENTLY
    - you could only use User Pools are your identity provider
    - and if you already have an identity provider, you could just use identity pools

SAML (?)