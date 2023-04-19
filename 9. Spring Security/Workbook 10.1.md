# MySQL

Installing MySQL on your machine is tedious. It is easier to run MySQL from a **container**.
## Docker Container

A Docker container is a lightweight environment that contains an application and **only** the resources that the application needs to run – **nothing else**.

![Screen Shot 2022-08-25 at 8.53.57 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fcdf1104c-f93d-43e0-849a-e1c1a94bd2ec?alt=media&token=8d3a0c22-bbdc-4d24-9a2f-e09bea988573)

The **Docker Engine** allows you to manage and run docker containers. Follow this link to install [Docker](https://docs.docker.com/get-docker/) for your operating system.

![Screen Shot 2022-08-25 at 8.55.51 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fbf89243d-c92d-4fbd-b8be-dbf7d286d440?alt=media&token=e1b7c15f-2ce8-44ec-be02-29a69fb9d7d5)

After installing Docker, run the command `docker version` to confirm that it's running.

![Screen Shot 2022-08-25 at 9.05.03 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ff14ee84e-f791-4c5e-8374-234316b73ca2?alt=media&token=8ae328e9-e5df-43ba-b672-b71f7913dbb8)

## Running MySQL

Launch the Docker Compose file by following this path in your resources.

![Screen Shot 2022-08-25 at 9.09.10 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F5d18a7a6-3d8f-4f39-90f6-5eacf393073c?alt=media&token=145fd252-7a4b-4309-9563-4b393808af24)

The Docker Compose file configures the settings of a container.
![Screen Shot 2022-08-25 at 9.11.15 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F640267fc-db78-4cd8-b9e4-98caf72879b7?alt=media&token=9bc2c468-72b2-4445-8f07-e378b30b77b2)

1. The Docker container will run an instance of MySQL 8.0.
2. The MySQL instance will contain a database called `db`.
3. The MySQL credentials are `user` and `password`
4. The password for the default `root` user will also be `password`.
5. MySQL will run on port 3306.
6. The container will expose port 3306 to the outside.
7. MySQL data will be maintained within a volume that exists on your machine. 

From Visual Studio Code, launch a terminal.

![Screen Shot 2022-08-26 at 12.04.49 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F6df01baf-5033-46cd-8bff-6c44f3eb46b6?alt=media&token=5a9b30a1-9acd-41f5-927d-957547c93c7e)

Make sure the path points to the folder that contains your docker-compose file.

![Screen Shot 2022-08-26 at 12.06.11 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F543458db-aa59-40b1-ab38-ae5da87e8b18?alt=media&token=7a8707b0-6612-45c9-b16c-0293c9dcbe18)

Run the command `docker compose up` to start up the docker container.

![Screen Shot 2022-08-26 at 12.08.31 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F119f4bda-2060-4ed1-95ca-9cbfdd8fcf97?alt=media&token=b9c930da-9843-4311-8acc-cb73595efc0b)

The MySQL application running inside the container can be accessed on port 3306.

## Launch the Spring Boot Project.

From another Visual Studio Code window, launch the starter project.

![Screen Shot 2022-08-26 at 8.23.08 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F86aa3843-eb12-4e58-949e-0d9497f44704?alt=media&token=2bfea272-262f-406a-a017-2b19826d3e8c)

Add this dependency in order to connect your application to the running instance of MySQL.

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```
Make sure to add this dependency **after** Spring Data JPA. Otherwise, you may get a `DataSourceConfiguration` exception.

![Screen Shot 2022-09-27 at 11.37.46 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe81d74df-3e8b-4d48-bac6-4b55a99e9bbe?alt=media&token=8fc24a54-f07d-4ab7-ac1c-6c8048e5a39b)
Inside your `application.properties` file, add these properties

```
spring.datasource.url=jdbc:mysql://localhost:3306/db
spring.datasource.username=user
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=create
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
```

![Screen Shot 2022-08-26 at 12.37.09 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fcc40d681-7d30-40ee-ab64-7a6162eaa7a2?alt=media&token=811c3c11-1e29-4a53-bc6c-59edad006f56)

1. The Spring Boot application connects to the MySQL instance that's running on port `3306`. It connects to the database: `db`.

2. The Spring Boot application uses the credentials `user` and `password` to authenticate.

3. Hibernate drops existing tables before creating new ones. In production, **do not include this line** because you do not want to destroy previous data during every re-launch. It's fine to keep it during development.

   - Side Note: Spring Data JPA uses the Hibernate implementation.

4. The docker container is running MySQL 8.0. We need to specify a dialect of MySQL8 so that hibernate generates appropriate SQL statements.

## **Run your application**

Congratulations! You connected your Spring Boot application to a MySQL database. Feel free to make requests from Postman to your heart's content.

![Screen Shot 2022-08-26 at 10.49.17 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F9d8daf77-b88a-4ace-825a-2761108745bc?alt=media&token=da0a5961-52bc-423d-b2f8-942bf069c8c2)

It's normal if you notice errors being thrown the first time you run the application. At first, `ddl-auto = create` attempts to drop existing tables from an **empty** database before creating new ones. 

## MySQL Workbench

Download the MySQL workbench from [MySQL workbench](https://www.mysql.com/products/workbench/). Once you download the workbench, open it and click the `+` icon. 

![Screen Shot 2022-08-26 at 12.59.21 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fd18ab88c-e9c7-45aa-b100-73e75158f45f?alt=media&token=c016f0da-8ba6-437c-84eb-a505fa9c10b6)

Use the following values in order to set up a connection with the currently running instance of MySQL. The `Connection Name` can be anything.

![Screen Shot 2022-08-26 at 1.01.31 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe929139c-963b-485f-a870-1163db2b9337?alt=media&token=e764c7c1-0343-4abf-b937-423055e97754)

Enter the password that corresponds to the username. Mac users: you might need to press `Store in Keychain` first. 

![Screen Shot 2022-08-26 at 1.05.35 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe952b0e8-46c1-4b86-8e09-837be2b69476?alt=media&token=cb01326d-36d3-451c-9496-09a08d9342b5)

Test your connection to ensure that it is successful.

![Screen Shot 2022-08-26 at 1.01.44 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F1389bef7-0709-4129-af3e-c625cfea6f49?alt=media&token=65221622-eb93-4060-92c7-982474284e82)

Open the connection, and click on **Schemas**. 

![Screen Shot 2022-08-26 at 1.07.26 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F9b1df339-5bfe-4df4-bb05-741afa972083?alt=media&token=a21ac641-f632-4af6-a01f-9d242f2e77f6)

Here you can see the database `db`, and all of the tables that Spring Boot created.

![Screen Shot 2022-08-26 at 1.08.53 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F140435da-00e4-4b88-a336-aa36eaf12bf3?alt=media&token=23778f30-90e7-4e76-be8e-4056e0440adf)

Feel free to query the saved data:
```sql
SELECT * FROM database_name.table_name
/* Example: SELECT * FROM db.student */
```
On the top toolbar, press the first lightning button to run the query.

![Screen Shot 2022-08-26 at 10.57.03 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fd1e27dd3-cecd-4c44-83f2-905ac39cbceb?alt=media&token=0c44a91d-5d22-4770-b197-f76dea4e01cd)

**Results**

![Screen Shot 2022-08-26 at 10.58.26 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F42fd25c2-b194-4831-81f2-c30d564ca29e?alt=media&token=21c5f81d-0f6f-4771-85ea-9e2c9ebabf57)

## Final Task

The docker engine can be heavy on your machine. Close it when you're done with it.

### Mac
![Screen Shot 2022-08-27 at 12.28.33 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8b2231d7-9b44-4de9-8df0-e19d16cd3d8d?alt=media&token=aa1c236a-4e50-49b0-8f75-50d87067fb43)

### Windows

![Screen Shot 2022-08-27 at 12.29.15 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fab5f9394-ca72-4271-87d9-4a24cbc719e1?alt=media&token=7e46faae-a573-43ee-8ca4-d121374252ee)

Don't worry, you won't lose any data. You can restart the docker engine by clicking the app.

![Screen Shot 2022-08-27 at 12.32.43 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F3fdf24a4-2cbc-4e3f-860c-99340b11ec84?alt=media&token=66e6b241-f149-4be3-b2d1-c918aa5fee7f)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!