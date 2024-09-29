# AWS-Disaster-Recovery-Demo

## Employee Management Application

- Connect to Mysql RDS Instance
- mysql -H \< RDS Endpoint \> -u admin -p
- create user 'tom'@'%' identified by 'root';
- create database kube;
- GRANT ALL PRIVILEGES ON kube.* TO 'tom'@'%';


App

- git clone https://github.com/14Rahul/Employee-Management-Three-Tier-App.git
- sudo apt-get install maven default-jre
- vi Employee-Management-Three-Tier-App/springboot-backend/src/main/resources/application.properties 
- spring.datasource.url=jdbc:mysql://<RDS Endpoint>:3306/kube?createDatabaseIfNotExist=true&allowPublicKeyRetrieval=true&useSSL=false
- cd /Employee-Management-Three-Tier-App/springboot-backend/
- mvn clean install
- Create Service File for Backend service
- vi /etc/systemd/system/employee-backend.service


Web

- sudo apt-get install npm
- sudo npm update npm -g
- vi /Employee-Management-Three-Tier-App/react-frontend/src/services/EmployeeService.js
- const EMPLOYEE_API_BASE_URL = "http://<LB Endpoint>:8080/employees";
- cd /Employee-Management-Three-Tier-App/react-frontend/
- Create Service File for Frontend service
- vi /etc/systemd/system/employee-frontend.service
