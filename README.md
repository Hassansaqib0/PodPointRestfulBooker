**Introduction**

This API is all about Booking  and the purpose of this collection is to trigger requests which will:

1)Check health check 

2)Create authentication
 
3)Get booking id’s 

4)Create bookings

5)Update booking fully or partially 

6)Delete booking   


**Note**:
 For the Restful-Booker collection in the collection settings in the tabs  ‘Pre-request script’ and ‘variable’ tab I have made some changes as below : 
1) In the Pre-request script I have written a Java script which will get the token from the response of the request ‘Create Auth token’  and pass it to the variable created in ‘Variables’ tab ‘NewToken’ and ‘req’, by this in the applicable requests like (Update, Partial and Delete) you will not need to update token because it will be updated automatically.

![2022-08-15 11_19_29-](https://user-images.githubusercontent.com/111247381/184618755-8b34ffc3-baab-4b13-a17d-ad94f064156e.png)



2) For the Create booking request I have added a Java script in the 'Test' tab which will get the 'bookingid' from the response and  with this i  have also created a new variable called 'BookingId' in the colletion settings 'variables' tab, by this for the requests Get booking, update booking , Partial booking and Delete booking you would not need to enter the bookingid in the parameter as the 'id' parameter will be updated automatically

![bookiing id](https://user-images.githubusercontent.com/111247381/184616321-3ef25aa8-dbc5-4726-a00e-40834dc1ee50.png)



4) In the Variables tab I have also created a variable ‘BookingUrl’ which will replace the Url in all requests. 
5) For all the requests all the headers , parameters and request body has already been configured for your convenience. 



**Setup**

Pre-requisite : 

Please make sure to download all the files by following below steps : 

1) in the https://github.com/Hassansaqib0/PodPointRestfulBooker page 
click on code then click on download zip, this will download all the files in this repository
drag this folder to desktop so we can import the Restful-booker.json collection later in the steps


Now please follow the below steps to import and setup the postman collection configured for Restful booker : 
1)	On your system please open postman application
2)	Once the Postman application is opened look for import button which should be at the top left  corner of the app
![1111](https://user-images.githubusercontent.com/111247381/184608371-5b9fd32a-b768-4347-81da-7516f833e6d3.png)


3)	Once you locate the ‘Import’ button then please click on it
4)	After clicking on the ‘Import’ button a pop up will be displayed where at the top please choose the option ‘File’ 
5)	After choosing the ‘File’ option please click on the ‘upload files’ button
6)	 A file explorer window will open then from left hand side of the window please click on the option ‘desktop’ , after clicking on the desktop then on the right hand side of the window please click on the file ‘Restful-booker.json; and then click on ‘Open’
![22](https://user-images.githubusercontent.com/111247381/184608636-5ff2ab3f-707b-4692-9db5-cfeffece3042.png)


8)	Once you click ‘Open’ then in the Postman application you will see the file you have selected and on the bottom of the pop up you will see the option ‘Import’, please click the ‘import’ button
9)	Once you click on the ‘import’ button then you will see a message on the postman application stating ‘Postman collection import has been successful’
10)	In the postman application on the left hand side you would now see the imported file ‘Restful-booker’ file, incase if you don’t see the file then please click on the options ‘Collections’ which is on the top left hand side of the application .




Once you have successfully imported the collection then please follow the below steps on how to use and trigger the Restful booker collection requests and please follow the below **sequence** for triggering requests
1)	In the postman application once you click on the Restful-booker file then it will open the drop down with all the requests already configured  as shown in the screenshot 

![33](https://user-images.githubusercontent.com/111247381/184609220-8ce620a7-b779-4ea8-b629-72fc008f87f0.png)


2)	Health check – Before we test the requests we need to make sure the API itself it up and running so in this when we send the request we should see the response ‘Created’ with 201 status code

3)	Create Auth token – The purpose of  this Post request is to return a token then to be used in other requests
Click on the ‘Send’ button for the Post request ‘Create auth token’ and in the response you will get the token with status code 200 

4)	Getting booking id’s – The purpose of this GET request is to to bring returns all the booking ids which already have been created. 
Click on the ‘Send’ button on the GET request ‘Getting booking id’s’ and in the response this will return all the book id’s which already has been created, here we can go to parametes tab and also select different parameters which will bring different such results based on the parameters  e.g. 

{{BookingUrl}}/booking?firstname=Sally

{{BookingUrl}}/booking?firstname=Sally&lastname=Brown

{{BookingUrl}}/booking?firstname=Sally&lastname=Brown&checkout=2014-10-23

{{BookingUrl}}/booking?checkout=2014-10-23



5)	Create Booking – the purpose of this Post request is to create new bookings.
as the request body has already been configured once this request is send then in response we get the new booking id with the rest of the body with status code 200  

6)	Get booking request – the purpose of this request is to return any booking information
we can use any booking id in the parameter 'id' from the request get booking id but because of the changes i have done the booking id will be automatically be updated which was created in the above step so clicking on the send button it will return the booking which we have already created with status code 200 

7)	Update booking request – the purpose of this PUT request is to update the existing data or if there is not data then its creates a new one so for this we can again use any booking id but in the parameter the value of the id would have been automatically updated so we just need to update the request as below and in the response we will get status code 200, see the screenshot below

![put parametere](https://user-images.githubusercontent.com/111247381/184613082-b67d68df-f605-4550-9f4f-ebcc6f2fa26e.png)



![update booking](https://user-images.githubusercontent.com/111247381/184612134-c4a8d062-19ec-4ce5-b9a9-7fcec79adb63.png)



8)	Partial Update booking request – the purpose of this PATCH request is to rather then updating the full request body it updates the partial body which needs to be updated so for this example we can change firstname  to “Pod” ,lastname to “point” and totalprice to 165 then if you click send then in the response you would see fields changed with status code 200 , the value of 'id' in the parameter section will be updated automatically


![patch](https://user-images.githubusercontent.com/111247381/184613511-d01da408-5851-4b9b-ad05-3e1606544bb3.png)





9)	Delete request – the purpose of this request is to delete any resource in the server so for this the value of id will be updatd automatically or you can add any id yourself by clicking on send this will delete it with the response ‘Created’ with status code 201



Troubleshooting : 

1) If the below requests do not work or give out 404 error then please before triggering these requests frist trigger the 'create booking' request as that will get the booking id and pass to the other requests where needed

Get booking 

Update booking

Partical update 

Delete booking

2) For the below requests in the header section a token is auotmatically updated incase if the requests gives error please trigger the 'create auth token' requet which update the variable in for these requests, alternatively we can also use authorization header by clicking on the check box in the header setion and unchecking the cookie header

Update booking

Partical update 

Delete booking
 







