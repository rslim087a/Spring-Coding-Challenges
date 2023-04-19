# Workbook 1.2

You will create a simple web application using Spring Boot.

![Screen Shot 2022-04-28 at 10.07.43 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ffd346c5d-579f-466e-8a8f-6424ff56cf22?alt=media&token=3c07459a-f7b7-4ee8-8f46-3f22f8123ef2)

## Spring Initializr

Launch the [Spring Initializr](https://start.spring.io/)

![Screen Shot 2022-06-10 at 11.37.43 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F4851367d-045f-4285-b2c5-8d4f0ed386eb?alt=media&token=af71a162-4262-4112-8068-a2927388fa30)

## Group Id
>Group Id identifies the organization

It cannot contain capital letters and must be a fully-qualified domain.

## Artifact Id
>Artifact Id determines the application name.

It cannot contain capital letters and must join words with a hyphen.

## Java version

> Be careful when selecting the Java version.

Your project will not compile if selects a **higher** version than the one you installed.

### Example

1. Java 17 is installed.  

2. The project selects a version of 19.

![Screen Shot 2022-09-24 at 12.22.12 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fd465ab09-9663-44cc-b7a0-55cd23c847e8?alt=media&token=de16c845-75f9-4e54-a624-0e371da16b5b)

Trying to compile throws an **error:** *`invalid target release: 19`*

![Screen Shot 2022-09-23 at 11.57.02 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc4443f81-a871-4ebe-9c03-a302e8252187?alt=media&token=88eae40f-0a80-4a17-9c16-147c6e900d49)

## Dependencies
> software that your application depends on.
Add the **Spring Web** dependency to bootstrap the launch of an HTTP server.

## `application.properties`
> configures the settings of your application.
Your application must respond to requests made on port 9090. 

## static folder
> contains static HTML, images or CSS files.
Add an HTML file to the `static` folder.

![Screen Shot 2022-04-28 at 9.57.00 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fe82fb068-e710-46e7-80ab-54b0de5ad468?alt=media&token=b9ef38ff-403c-4416-b4ea-30d676d35789)

 Your HTML must render a static view that contains four headers:

```
>> Printing is fun!
>> Java > Python.
>> I spilled Java all over my paper.
>> My dog ate my Java.
```

See the **HTML Cheat Sheet** if you need help setting up the HTML document. 

## Potential Error
If your application fails to start, terminate other applications running on port 9090.

![Screen Shot 2022-07-04 at 12.00.25 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fd0281837-a48b-4558-8ac1-9243535a7c0e?alt=media&token=082d8e01-ae89-4a86-a908-f8fa089ce6fa)


## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!