# Docker-two-tier-app
2-tier app by using Docker

# After the deployment, you shall face - Programming error (*MySQL error - table not found);
 - Sol: Create the messages table in your MySQL database: (In Mysql running conatiner)
 ```bash 
     docker exec -it <ID> sh   #( To enter mysql running container - *ID = container ID) 
     mysql -u root -p          #(To access MySQL tables, db, etc.) [password - admin]
```
# After above steps you able access and create db, tables in mysql. 
```bash
    show databases;   #(To see all present db)
    use myDB;         #( To changed DB) [*myDB database used in code and config file]
```
# Now Create the messages table in your MySQL(myDB) database:
```bash
   CREATE TABLE messages (
         id INT AUTO_INCREMENT PRIMARY KEY,
         message TEXT
   );
```
