- Mastercard:
    - Risk_Based_Authentication.pdf

     1. P10. Not only does it raise customer
        satisfaction thanks to the streamlined
        payments process, it also reduces the
        merchant’s liability for unauthorised
        CNP transactions. The combination of
        both technologies also enables more
        transactions to be successfully completed
        because the bank can now automatically
        approve some transactions which,
        previously, would have triggered
        a 3-D Secure challenge. 



- EMVCo:
  - CReq timeout:P68
    -  once the authentication as defined in [Req 326].b has completed or the timer as defined in [Req 326].a has expired, do the following: ...
    -  Step 16 ACS: 
       -  [Req126]If the Cardholder abandons the challenge during the processing of Step 12 through Step 14, then the ACS sets the **Challenge Cancelation Indicator** to the appropriate value in the RReq message. Refer to Annex A for specific values.
    -  Step 18 RRes 3DS Server:
       -  [Req132]Receive the RReq message or Error Message from the DS and Validate as defined in Section 5.9.9. If the message is in error the 3DS Server ends processing.
