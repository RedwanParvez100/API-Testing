### **Rest Booking API Testing with Postman Newman**
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. The project automatically tests a booking REST API using Newman and generates a test report after execution.

### **Features**
- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone https://github.com/RedwanParvez100/API-Testing.git
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```

### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.
  

## **Testing**

## Test Case Scenarios:

## _**1. create_new_booking**_

### Request URL: https://restful-booker.herokuapp.com/booking/
### Request Method: POST
### Pre-request Script:
```console 
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    console.log(firstName)
    pm.environment.set("first_name",firstName)

    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("last_name",lastName)

    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    console.log(totalPrice)
    pm.environment.set("total_price",totalPrice)

    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    console.log(depositPaid)
    pm.environment.set("deposit_paid",depositPaid)

    const in_date = require('moment')
    const check_in_date = in_date()
    // console.log(check_in_date)
    pm.environment.set("check_in", check_in_date.format("YYYY-MM-DD"))
    // console.log(check_in_date.format("YYYY-MM-DD"))

    const out_date = require('moment')
    const check_out_date = out_date()
    // console.log(check_out_date)
    pm.environment.set("check_out", check_out_date.add(3,'d').format("YYYY-MM-DD"))

    var additionalNeeds = pm.variables.replaceIn("{{$randomProduct}}")
    pm.environment.set("additional_needs",additionalNeeds)
```

 **Request Body:** 
 ```console 
  {
	  "firstname" : "{{first_name}}",
	  "lastname" : "{{last_name}}",
	  "totalprice" : {{total_price}},
	  "depositpaid" : {{deposit_paid}},
	  "bookingdates" : {
           "checkin" : "{{check_in}}",
           "checkout" : "{{check_out}}"
	   },
	   "additionalneeds" : "{{additional_needs}}"
  }
```

**Response Body:**
 ```console 
  {
      "bookingid": 3151,
      "booking": {
          "firstname": "Magnolia",
          "lastname": "Dietrich",
          "totalprice": 559,
          "depositpaid": false,
          "bookingdates": {
               "checkin": "2025-07-26",
               "checkout": "2025-07-29"
           },
           "additionalneeds": "Gloves"
        }
  }
```

## _**2. get_booking_details_by_id**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console
{
     "firstname": "Magnolia",
     "lastname": "Dietrich",
     "totalprice": 559,
     "depositpaid": false,
     "bookingdates": {
         "checkin": "2025-07-26",
         "checkout": "2025-07-29"
     },
     "additionalneeds": "Gloves"
}
```

## _**3. create_a_token_for_authentication**_
### Request URL: https://restful-booker.herokuapp.com/auth
### Request Method: POST
### Pre-request Script: None
### Request Body:
 ```console 
{
	"username": "admin",
	"password": "password123"
}
```
  **Response Body:**
 ```console 
{
    "token": "3262a3098ad8bc5"
}
```

 ## _**4. update_the_booking_details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    console.log(firstName)
    pm.environment.set("first_name",firstName)

    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("last_name",lastName)

    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    console.log(totalPrice)
    pm.environment.set("total_price",totalPrice)

    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    console.log(depositPaid)
    pm.environment.set("deposit_paid",depositPaid)

    const in_date = require('moment')
    const check_in_date = in_date()
    // console.log(check_in_date)
    pm.environment.set("check_in", check_in_date.format("YYYY-MM-DD"))
    // console.log(check_in_date.format("YYYY-MM-DD"))

    const out_date = require('moment')
    const check_out_date = out_date()
    // console.log(check_out_date)
    pm.environment.set("check_out", check_out_date.add(3,'d').format("YYYY-MM-DD"))

    var additionalNeeds = pm.variables.replaceIn("{{$randomProduct}}")
    pm.environment.set("additional_needs",additionalNeeds)
```
 **Request Body:** 
 ```console 
 {
	  "firstname" : "{{first_name}}",
	  "lastname" : "{{last_name}}",
	  "totalprice" : {{total_price}},
	  "depositpaid" : {{deposit_paid}},
	  "bookingdates" : {
           "checkin" : "{{check_in}}",
           "checkout" : "{{check_out}}"
	   },
	   "additionalneeds" : "{{additional_needs}}"
  }
```
**Response Body:**
 ```console 
  {
      "firstname": "Domenico",
      "lastname": "Denesik",
      "totalprice": 924,
      "depositpaid": true,
      "bookingdates": {
          "checkin": "2025-07-26",
          "checkout": "2025-07-29"
      },
      "additionalneeds": "Hat"
}
```

 ## _**5. delete_booking_record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Request Body: None 
**Response Body:**
 ```console 
  Created
```

## Run Command:  
- Run Command for Report: 
```console 
newman run Automated-Testing-of-Rest-Booking-API.postman_collection.json -e Automated-Testing-of-Rest-Booking-API.postman_environment.json -r cli,htmlextra
```

## Newman Report Summary:
![Newman Report Summary](https://github.com/RedwanParvez100/API-Testing/blob/main/Assets/Newman-report-P1.png)
