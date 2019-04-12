# Customer RESTful API
This RESTful Customer API allows user to:
  - List all customers
  - Create a new customer
  - Update a customer
  - Delete a customer
  
 ## Design
 RAML was used to design the Customer API Specification
 https://anypoint.mulesoft.com/designcenter/
 
 ## Development
 Tool: Anypoint Studio
 
 Create the **customer-rest-api** project by converting from the RAML Customer API Specification
 
 ## Consideration
 There are considerations while developing the API but haven't been applied due to the time constrain
  - Address should be in a seperate table because a customer can have more than one addresses
  - Limit the number of record returning from get all customers API
 
 ## Running
 Oracle DB was chosing because I have it ready on my pc.
 
 To run this service on Oracle. First need to create the Customer table and SEQUENCE using these scripts
 
 <pre>
 CREATE TABLE "MVC_BANK"."CUSTOMER" 
   (	
    "ID" NUMBER(10,0) NOT NULL ENABLE, 
	  "FIRSTNAME" VARCHAR2(250 BYTE), 
	  "LASTNAME" VARCHAR2(250 BYTE), 
    "ADDRESSLINE1" VARCHAR2(50 BYTE), 
	  "ADDRESSLINE2" VARCHAR2(50 BYTE), 
	  "SUBURB" VARCHAR2(50 BYTE), 
	  "CITY" VARCHAR2(250 BYTE), 
    "COUNTRY" VARCHAR2(250 BYTE), 
	  CONSTRAINT "CUSTOMER_REST_PK" PRIMARY KEY ("ID")
    );

 CREATE SEQUENCE customer_seq
    MINVALUE 1
    START WITH 1
    INCREMENT BY 1
    CACHE 20;
 </pre>
 
 ## Running command
 ###### POST
 <pre>
 URL: http://localhost:8081/api/customer
 
 Sample input
 {
  "firstName": "First",
  "lastName": "Last",
  "addressLine1": "Unit 3",
  "addressLine2": "123 Sample Street",
  "suburb": "Mt Eden",
  "city": "Auckland",
  "country": "New Zealand"
  }
 </pre>
 
 ###### PUT
 <pre>
 URL: http://localhost:8081/api/customer/{id}
 
 Sample input
 {
  "firstName": "First",
  "lastName": "Last",
  "addressLine1": "Unit 3",
  "addressLine2": "123 Sample Street",
  "suburb": "Mt Eden",
  "city": "Auckland",
  "country": "New Zealand"
  }
 </pre>
 
 ###### DELETE
 <pre>
 URL: http://localhost:8081/api/customer/{id}
 </pre>
 
 ###### GET (all customer)
 <pre>
 URL: http://localhost:8081/api/customer
 </pre>
 
  ###### GET
 <pre>
 http://localhost:8081/api/customer/{id}
 </pre>
