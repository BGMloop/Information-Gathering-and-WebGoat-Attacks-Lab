#WebGoat Access Control Lab

WebGoat is a vulnerable web application managed by OWASP, intended to impart lessons on web application security. In every lesson, participants are required to exhibit their comprehension of a security concern by exploiting an actual vulnerability found in the WebGoat applications.The application serves as a pragmatic educational platform, offering users guidance and code to elucidate the lesson.


This lab uses the Kali-20 virtual machine (VM). The credentials are: 
Username: osboxes
Password: osboxes.org

**Introduction**

Web Goat Access Control Vulnerability

In this section, we study an attack using access control vulnerability on a web-based access control mechanism, which is simulated by WebGoat. A tomcat server which is running in the background allows various users to access resources (files and folders on the server).
We use the “Webscarab” tool to intercept the traffic between client (web browser) and tomcat server, and gain unauthorized access to a restricted resource on the server.
Download the VM and setup WebGoat:
  1. Make sure you have Oracle Virtual Box 6.1.x installed in your machine.
  2. Download the Kali VM OVA file from the link given on the lab page.
  3. On your local machine, double-click on the OVA file to import the VM to VirtualBox.
  4. Click “Import” to import the VM. (This may take a few minutes.)
  **(See the screenshot below.)**
![Screen Shot 2025-01-18 at 12 35 59 AM](https://github.com/user-attachments/assets/df23aa99-1c73-40bb-9b95-60b7c18afb7f)


  5. Start the VM login with the following credentials:
     Username: osboxes
     Password: osboxes.org
![Screen Shot 2025-01-18 at 12 37 59 AM](https://github.com/user-attachments/assets/b8fcdde9-199c-487c-975c-ea55d8fefcca)

  7. After logging in, click on the terminal icon as shown below to start the terminal:
**(See the screenshot below.)**
     ![Screen Shot 2025-01-18 at 12 43 46 AM](https://github.com/user-attachments/assets/4d176e8e-47dc-4a00-a177-ad58670e6b68)

  9. Type the command “docker run -p 8080:8080 -t webgoat/webgoat-7.1” and hit enter, as shown below:
**(See the screenshot below.)**
   ![Screen Shot 2025-01-18 at 12 45 00 AM](https://github.com/user-attachments/assets/f9d22e46-637f-4e58-81e3-f5c70193cd0f)

  11. You will get a web server started:
  **(See the screenshot below.)**
   ![Screen Shot 2025-01-18 at 12 46 21 AM](https://github.com/user-attachments/assets/4c78a9e5-4041-4364-a525-9d2033467bd5)

Normally, you should see a message as above, if WebGoat’s tomcat server start successfully. (Sometimes, the notifications as above are not shown, so please proceed with the next command, regardless whether you see the notifications or not.)
Type : “http://127.0.0.1:8080/webgoat/attack” in the browser address bar to start the WebGoat. (OR)
Type : “localhost:8080/WebGoat/login.mvc” in the browser address bar to start the WebGoat. 
Default passwords are shown on the below screenshot:
  **(See the screenshot below.)**
  ![Screen Shot 2025-01-18 at 1 00 20 AM](https://github.com/user-attachments/assets/877579d0-71da-4265-90fd-4cf5cac98f36)

Use the “guest” login to start the WebGoat.
  **(See the screenshot below.)**
 ![Screen Shot 2025-01-18 at 1 01 47 AM](https://github.com/user-attachments/assets/2407f4c8-1283-4525-94bf-8ae94ae19f40)

Section 1: Access Control Matrix

a. Click on Access Control Flaws on the side bar and then “Using AccessControl Matrix” link below it.
  **(See the screenshot below.)**
  ![Screen Shot 2025-01-18 at 1 02 20 AM](https://github.com/user-attachments/assets/a3602043-b9e1-482a-bd4b-034c5a71337f)

b. You will see a list of users from the drop-down menu next to “Change user:”. and the list of resources (folders) from the drop-down menu
next to “Select Resource:”.
c. Each user has access to specific files. Select a user from dropdown (Ex: moe), select a resource (Ex: Public Share) and click on the Check Access button.


You will see the current permission, if you have access or not in a red line above the user name on the same screen.

  **(See the screenshot below.)**
 
![Screen Shot 2025-01-18 at 1 04 41 AM](https://github.com/user-attachments/assets/93bc1dc4-d073-456e-81ef-08f8ef65ed37)

Time Card Entry
Performance Review
Time Card Approval
Site Manager Account Manager

Section 2: Attack on Access Control
a. Now, click on “Bypass path based access control scheme” on the side bar.
b. Go to ApplicationsàWeb Application Analysis and open “webscarab”.
  **(See the screenshot below.)**
![Screen Shot 2025-01-18 at 1 05 24 AM](https://github.com/user-attachments/assets/0a5aea2d-e99c-40bd-9394-c604dc29dbc3)

 c. “WebScarab” window appears, which looks as shown below:
  **(See the screenshot below.)**
![Screen Shot 2025-01-18 at 1 06 05 AM](https://github.com/user-attachments/assets/ba8d8733-241f-4e95-b562-bed281012241)

 d. Go to Proxy ® Manual Edit and select “Intercept requests”.
  **(See the screenshot below.)**
![Screen Shot 2025-01-18 at 1 06 55 AM](https://github.com/user-attachments/assets/36c5cc4e-8a79-492b-b7aa-ec6b80f5b574)

 e. Go to Proxy ® Listeners and observe the used port.
  **(See the screenshot below.)**
![Screen Shot 2025-01-18 at 1 07 21 AM](https://github.com/user-attachments/assets/37593da9-4cd2-4acf-8f81-8c1d37dd1713)

 f. Next, go to the browser and open the Preferences menu as shown below.
 
  **(See the screenshot below.)**
![Screen Shot 2025-01-18 at 1 07 50 AM](https://github.com/user-attachments/assets/95e1c0f7-835d-4fac-9981-aab99c162c97)

 g. under Network Settings and click on Settings.
   **(See the screenshot below.)**
 ![Screen Shot 2025-01-18 at 1 08 26 AM](https://github.com/user-attachments/assets/9ce0d94a-0499-401d-a4b5-ffb7bb8d7fb8)

 h. Make the settings as below. Remove any text in the “No proxy for” box. Give the address and port number from WebScarab and click “ok”.
   **(See the screenshot below.)**
 ![Screen Shot 2025-01-18 at 1 09 01 AM](https://github.com/user-attachments/assets/1743d868-6845-4c84-bbcc-0d8958c10b39)

 In the Firefox URL location, type “about:config” and hit enter as shown below.
 
   **(See the screenshot below.)**
  ![Screen Shot 2025-01-18 at 1 09 27 AM](https://github.com/user-attachments/assets/124b1b90-6960-4959-9bd9-1a2128c862db)

  In the search bar, type “network.proxy.allow_hijacking_localhost”, as shown below. You will see the field set to “false”,

  **(See the screenshot below.)**
  ![Screen Shot 2025-01-18 at 1 10 34 AM](https://github.com/user-attachments/assets/31fa9bbf-3256-493a-a053-ff5501d8b769) 
  
  click on the button (highlighted red below) to switch it to “true”.
  
  **(See the screenshot below.)**
  ![Screen Shot 2025-01-18 at 1 11 07 AM](https://github.com/user-attachments/assets/3958fabd-1c05-44d0-b822-2deb666546fa)

    The field will be set to “true”.
    
   **(See the screenshot below.)**
  ![Screen Shot 2025-01-18 at 1 11 39 AM](https://github.com/user-attachments/assets/d31e5ec6-74f0-491b-985c-14d9f48971c2)

    i. Go back to WebGoat and select one of the files in the list and click on the button “View File”.
  **(See the screenshot below.)**
   ![Screen Shot 2025-01-18 at 1 12 09 AM](https://github.com/user-attachments/assets/164840fa-7f40-46c7-829e-9ab2ce81460a)

    j. An intercepted request will pop up.
  **(See the screenshot below.)**
 ![Screen Shot 2025-01-18 at 1 12 37 AM](https://github.com/user-attachments/assets/0404b42e-cfab-4e1f-93cd-bc1affa31164)

   k. In the tab “URLEncoded” below, row “Variable”, column “Value”, type: “../../../../../WEB-INF/spring-security.xml”
  and click the “Accept changes” button.
  **(See the screenshot below.)**
![Screen Shot 2025-01-18 at 1 13 04 AM](https://github.com/user-attachments/assets/2862e4f2-c0fd-40d0-a71a-356d55036994)

 l. Continue clicking on the “Accept changes” button until all the intercepted requests are processed.
 m. On the main page of WebGoat, you will see the message in red: 
“Congratulations. You have successfully completed this lesson.”
![Screen Shot 2025-01-18 at 1 13 33 AM](https://github.com/user-attachments/assets/80e986dd-d418-4236-9ded-ac0cfcfb5cb5)

![Screen Shot 2025-01-18 at 1 14 12 AM](https://github.com/user-attachments/assets/97a57877-64b8-4e8b-b559-87cdf07455ea)
