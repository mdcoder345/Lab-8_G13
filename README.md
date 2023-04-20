# Lab-8_G13

Lab - 08: UNIT Testing of the project

Group 13

Date: 20-04-2023

Group Members

ID No | Name
---- | ----
202001133 | DANKHARA MANAN SHAILESHKUMAR
202001163 | SHAH ISHA JATINKUMAR
202001149 | BUCH KAVAN JAYESHBHAI
202001168 | PRAJAPATI SHREYA
202001135 | PATEL DHARVA YOGESHKUMAR
202001148 | BRIJRAJSINH GOHIL
202001137 | MAKWANA KIRTAN DHARMENDRABHAI
202001152 | SANEPARA KHUSHI SURESHBHAI
202001155 | RAMOLIYA HARSH MADHUKANTBHAI

Here, we have used chai and mocha for testing purpose.

Below is the code used for login and registration verification

```
const chai = require('chai');
const chaiHttp = require('chai-http');
const app = require('../index');
const expect = chai.expect;
const should = chai.should();
chai.use(chaiHttp);

describe("User",()=>{
	//login module
	describe("POST /login",()=>{
    	it("it should login user",(done)=>{
        	chai
        	.request(app)
        	.post("/login")
        	.send({
            	username_email:"isha@121",
            	password:"12345"
        	})
        	.end((err,res)=>{
            	res.statusCode.should.equal(200);
            	res.body.should.be.a('object');
            	done();
        	})
    	})
	})
  
	//register module
	describe("POST /register",()=>{
    	it("it should register user",(done)=>{
        	chai
        	.request(app)
        	.post("/register")
        	.send({
            	username:"isha@121new",
            	email:"isha@121new",
            	password:"123",
            	confirmedPassword:"13",
            	age:21,
            	institute:"IIT"
        	})
        	.end((err,res)=>{
            	res.statusCode.should.equal(200);
            	res.body.should.be.a('object');
            	done();
        	})
    	})
	})
})

```

For login testing we have taken two test cases. Both of them is listed below with their respective output.

1. Testcase:
```
username: “i121”
password: “1234”
```

Test Result:

![image](https://user-images.githubusercontent.com/75557009/233430201-57aa59da-f8d2-49fa-a1b4-f98975bd3de1.png)
As we can see that it shows error while login.

2. Testcase:

```
username_email: “isha@121”
password: “12345”
```

Test Result:
![image](https://user-images.githubusercontent.com/75557009/233430673-739a9e7e-43cf-4fbd-8a82-ddcf8e263275.png)
This test case is valid as it doesn't shows any error.

Also, for registration testing we have taken two test cases. Both of them is listed below with their respective output.

1. Testcase:

```
username: “isha@121new”
email: “isha@121new”
password: “123”
cofirmedPassword: “123”
age: 21
Institute: IIT
```

Test Result:
![image](https://user-images.githubusercontent.com/75557009/233431106-a19cab0a-f7c9-4441-aaf8-b0c0c88e2cae.png)
This test case is valid as it doesn't shows any error.

2. Testcase:

```
username: “isha@121new”
email: “isha@121new”
password: “123”
cofirmedPassword: “13”
age: 21
Institute: IIT
```

Test Result:
![image](https://user-images.githubusercontent.com/75557009/233432208-630953a7-c29e-4605-af42-a5be54046547.png)
As we can see that it shows error while registration beacuse of confirmedPassword is not matching password.

Below is the code for verification of added courses and their descriptions.



Here also, we have taken two testcases which are listed below along with their output.

1. Testcase:

```
courseName: “course#1”
courseDescription: “course#1 description”
```

Test Result:

![image](https://user-images.githubusercontent.com/75557009/233434779-96b6512d-6583-4cb9-a6ef-1fac0bd81b7b.png)
This test case is valid as it doesn't shows any error.

2. Testcase:

```
courseName: “”
courseDescription: “course#1 description”
```

Test Result:

![image](https://user-images.githubusercontent.com/75557009/233435354-02e75bba-252e-41de-895a-96b7a5bb41bd.png)
As we can see that it shows error while adding course beacuse of invalid courseName.


