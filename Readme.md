Copy the db_server_address and web_server_address from the output.

How to deploy a LAMP stack in AWS using terraform

Connect to EC2 instance (web server)
ssh -i "/home/ec2-user/<your_private_key>.pem" <web_server_address>
1
	
ssh -i "/home/ec2-user/<your_private_key>.pem" <web_server_address>

Edit index.php in EC2 instance (web server)
vi /var/www/html/index.php
----------------------
#change only <your_aws_mysql_rds_endpoint> with db_server_address from output
$link = mysql_connect('<your_aws_mysql_rds_endpoint>', 'myuser', 'mypassword');
----------------------
:wq
1
2
3
4
5
6
	
vi /var/www/html/index.php
----------------------
#change only <your_aws_mysql_rds_endpoint> with db_server_address from output
$link = mysql_connect('<your_aws_mysql_rds_endpoint>', 'myuser', 'mypassword');
----------------------
:wq

How to deploy a LAMP stack in AWS using terraform
## Connect to mysql rds instance
mysql -h <db_server_address> -P 3306 -u myuser -p
#create table and insert data
USE mydb;
CREATE TABLE counter (visits int(10) NOT NULL);
INSERT INTO counter(visits) values(1);
1
2
3
4
5
6
	
## Connect to mysql rds instance
mysql -h <db_server_address> -P 3306 -u myuser -p
#create table and insert data
USE mydb;
CREATE TABLE counter (visits int(10) NOT NULL);
INSERT INTO counter(visits) values(1);

How to deploy a LAMP stack in AWS using terraform

Open web_server_address in the browser , hit refresh and check
