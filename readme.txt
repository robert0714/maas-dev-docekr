===================
Prerequisite
===================

docker container  Mysql無法被外部Ansible使用指令控制，所以需要手動下指令進入
` docker exec -it mysqldb /bin/bash
 mysql -uroot  -p -Bse  "create user 'chain'@'%' identified by 'qazwsx' ;grant all on  *.* to 'chain'@'%' "; 
  