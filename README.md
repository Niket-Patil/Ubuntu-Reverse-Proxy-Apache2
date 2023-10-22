# Ubuntu-Reverse-Proxy-Apache2
In this assignment we are using AWS EC2 Instance (Ubuntu) for hosting a sample application and implementing a Apache reverse proxy.

# AWS EC2 Setup and Configuration: 
1.	Login to AWS Console 
2.	Go to Services --> EC2 --> Launch Instance
3.	Select the following configuration:

 ![1](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/df055021-5190-4e8d-9e23-83ea77e89443)
![2](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/5d904a7f-04b7-4052-8c29-2cd23bd6d3e9)
![3](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/b3a7d7bd-4dd1-44ac-a883-3be9f916b26c)
![4](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/e1dcea65-229b-4796-840e-4e383bd17d2a)

Use the default VPC and Subnets. 
Allow SSH and HTTP/HTTPS in security groups.

4.	Click on “Launch Instance”

5.	Once the instance 2 checks click on “connect”.

6.	Run “sudo apt-get update && sudo apt-get upgrade -y” command to update Ubuntu.

 ![5](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/3901b4f1-66d3-4edd-ac0d-06f6748b2ccd)

7.	Once the upgrade is done, use command “sudo apt-get install apache2”

 ![6](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/af3b4b3b-e1a6-4074-b714-ce67b0f9cead)

8.	Install “npm” and “nodejs” using the command :
“sudo apt install npm”
“sudo apt install nodejs”


# Application Hosting Files Setup:
Here we are going to create a sample VUE.js application using VUE CLI.

1.	Navigate to the html directory using command                                         
“cd /var/www/html”. 

2.	Install the VUE CLI using command:
“npm install -g @vue/cli”

 ![7](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/6cdb772b-d73f-4857-a492-37bdefe7618b)
 
4.	Create a sample project using the command:
“vue create hello-world”
Select Default [Vue 3]
 
![8](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/ad3095c7-6264-4719-9a59-d4598d01ffd8)

4.	 Now once the project is created. Navigate to the root directory of the project and use “npm run build” to run the application.

 ![9](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/967bcdcb-e1fc-4d5b-a873-814b1e031200)

The web application well not be available to the internet unless we configure the Apache server

# Configuring the Apache server:
To make our WebApp accessible over the internet we need to setup a reverse proxy using the Apache server configurations.

1.	We need to enable “proxy” and “proxy_http” modules using the following commands:
“sudo a2enmod proxy && sudo a2enmod proxy_http”

![10](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/ae72593b-4c9d-47ee-a41e-98745613c8f1)

2.	Restart Apache Server 
“Sudo systemctl restart apache2” 

 


3.	Navigate to  /etc/apache2/sites-available/000-default.conf
Edit the configuration file using any editor to your required settings/configuration

4.	Edit the Following: 
 
![11](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/28b6962d-5e71-446d-8660-99e104f5541e)

5.	Restart Appache.

Now Copy your EC2 Instance Public IP and Past it on the Browser.
 
# Output

![12](https://github.com/Niket-Patil/Ubuntu-Reverse-Proxy-Apache2/assets/86849874/86100f4e-014b-4820-9a44-6699b61049e9)



