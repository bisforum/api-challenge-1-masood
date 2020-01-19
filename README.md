# How to run
1. This is a maven project, please make sure you have it on your machine. If not, please follow this link: https://maven.apache.org/install.html 

2. Open the project in your IDE (I use IntelliJ IDEA) and right click on the APITest.FruitShop.java file and Run the test

Everything else should work. 

I have also added a recorded video file of my screen, just in case (media.io_masood-api-test.mp4).

# Problems:

During doing the task, I have faced 2 main problems as follow:  

 1. "POST /customers/{id}/orders/" is not defined well in the Swagger file (see: https://api.predic8.de/shop/docs#!/customers/postShopCustomersIdOrders).

* **Details**:
Based on the Swagger file, it is not clear how to create an Order for a customer. I think the body of the request is missing.
if I run the exact curl which is provided in the Swagger file I get the following response:

       >> curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' 'https://api.predic8.de:443/shop/customers/456/orders/' -v
**Response:** 

     Trying 148.251.48.131...
     TCP_NODELAY set
     Connected to api.predic8.de (148.251.48.131) port 443 (#0)
     TLS 1.2 connection using TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
     Server certificate: *.predic8.de
     Server certificate: Sectigo RSA Domain Validation Secure Server CA
     Server certificate: USERTrust RSA Certification Authority
    > POST /shop/customers/456/orders/ HTTP/1.1
    > Host: api.predic8.de
    > User-Agent: curl/7.54.0
    > Content-Type: application/json
    > Accept: application/json
    >
    * Empty reply from server
    * Connection #0 to host api.predic8.de left intact
    curl: (52) Empty reply from server
	
**Solution:**  
Talk with the developers of the API and clarify how to call the endpoint exactly.  

2. I was not able to make an invalid GET /categories/id API call. All of the calls which I made returned 200.
Example of calls which tried: 

`curl -X GET 'https://api.predic8.de:443/shop/categories/ff' -v
curl -X GET --header 'Accept: application/json' 'https://api.predic8.de:443/shop/categories/  ' -v
curl -X GET --header 'Accept: application/json' 'https://api.predic8.de:443/shop/categories/dsdsds23232$$##' -v
`

**Solution:**  
Talk with the Product Owner/Developers and clarify what input could generate 401 error code?

**Improvements**  
If I would have more time I would move the endpoint URLs to a property files.
Also in case the number of test increases, I would do some refactoring and separate the data layers and test prepration layers from the tests itself.
