# Workbook 1.3
In this workbook, you will run your application as a `jar` file. We will never use this method, but it's good to be familiar with it.

## Download the resources

If you still haven't downloaded the resources, [click here](https://github.com/rslim087a/spring-boot-bootcamp-resources). Follow these steps to download the zip file.

![a804cbd4-25d4-4bb1-826f-f35dd5660541.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F38bc17a1-4104-4f52-becc-d86cc9890199?alt=media&token=57373f86-7c4a-4e5d-ab6b-4dc19f2ab9d9)

Unzip the resources into a folder.

![Screen Shot 2022-07-15 at 3.49.08 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc615da57-d373-4eaa-ab8a-2378436d88bc?alt=media&token=5f01bcbd-e713-4d1b-8d69-c5ed75f46982)

## Launch the Starter Workbook

From `spring-boot-bootcamp-resources` > `1.intro-to-springboot` > `workbook-1.3` > `starter`, launch the `workbook` folder. 

![Screen Shot 2022-05-31 at 7.03.07 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F7372915d-2a61-442a-943d-c7534abf894f?alt=media&token=e1c13a54-f156-4d88-8ced-dfa390e9b4fd)

## Frequently Asked Question
- Question: The `mvnw` wrapper command is 'not found'.
- Answer: From your editor, **only** launch the workbook folder.

![Screen Shot 2022-07-13 at 9.16.40 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F8892f566-e070-413f-8c03-0985fa94ef45?alt=media&token=e8c3583b-4d98-4989-8897-d16d70d051b1)

This ensures that your terminal points to the exact folder that your wrapper is in.

![Screen Shot 2022-07-13 at 9.19.56 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F09bf444a-b53d-4cd2-b030-7d825e978b9a?alt=media&token=a1643aab-5e72-4545-817c-b8f01b4bea6e)


## `mvnw package`
1. Compiles your code.
2. Packages everything in a JAR file inside `target`.

The name of your JAR file is determined by the `artifact-id` and `version` 
![Screen Shot 2022-05-31 at 7.10.00 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F9b9a2ccd-ebcc-4dba-a1d3-ff4341e3af2e?alt=media&token=77afa40b-5f08-4cdb-9f2a-c8d8d14afa05)

`SNAPSHOT` means this version of your application is under development. Version 0.0.1 of our application is complete and stable, so remove `SNAPSHOT`.

![Screen Shot 2022-05-31 at 7.12.26 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F568391ab-5911-4ad4-aff9-1ea191eb8ca4?alt=media&token=23853c42-c10b-4374-9cb8-ca26d94b4c92)

Package your application.

![Screen Shot 2022-05-31 at 7.21.17 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fdb24f7fe-6c61-4c8f-81c8-70d629678b14?alt=media&token=0b99a548-e24f-4318-801b-04da23cb8df3)

The JAR file packages all of your application's compiled code. Now your application is portable. 

## Task 

Drag the `jar` file to your `Desktop`.

![Screen Shot 2022-09-22 at 9.53.00 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F70629877-8945-4bd9-9357-68d18bfb4ca1?alt=media&token=cbc020c8-5454-40e1-9400-2902651a7352)

## **Instructions for Mac Users**
Scroll down if you're a Windows user. From your Mac, launch a terminal.

![Screen Shot 2022-05-31 at 7.26.41 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F6189314e-39c3-474c-a9ca-78817409b396?alt=media&token=a2cb71e1-bf2d-44bf-bf09-c7d238d69596)

Enter the command `cd` to start from the root of your filesystem.

![Screen Shot 2022-05-31 at 7.54.24 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Ff3816c95-caa7-4106-8c11-332814c3d0a5?alt=media&token=62d16ac8-a155-4f0c-b40c-d4c0031164f4)

The next `cd` command must direct the terminal to your Desktop directory.

![Screen Shot 2022-05-31 at 7.55.16 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F47dc93f5-4029-4600-9394-30bcbfc09e63?alt=media&token=739d26fb-4db8-4740-bfa4-985da2d1f5eb)

Your terminal now points to your Desktop. Run the `jar` file using the command `java -jar workbook-0.0.1.jar`.

![Screen Shot 2022-09-17 at 12.54.22 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F363774ef-a98e-42d6-8388-9be3e4c5890d?alt=media&token=75ab92a0-9af2-4a07-a876-82f5ce03650a)

## **Instructions for Windows Users**
Launch the Command Prompt from your start menu.
![Screen Shot 2022-09-17 at 12.42.12 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F32d10a4b-ae6b-40b2-a57c-74553c87cf55?alt=media&token=ee5a8ad4-a43c-4835-bb1a-0e4b608f28ac)

Your path should start at `C:\Users\username`
![Screen Shot 2022-09-17 at 12.44.31 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F31d61a00-6d48-48ad-8ed2-89d4f6bd6c8f?alt=media&token=534b2309-dee5-4fba-9a07-830193ae53ee)

Enter the command: `cd Desktop` to go to your Desktop directory.

![Screen Shot 2022-09-17 at 12.47.52 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc9683bbd-99dd-43d0-8af2-408aa91eb860?alt=media&token=ccd97225-e41d-4a82-b29c-6712bbdbbf6a)

Your command prompt now points to your Desktop. Run the `jar` file inside your Desktop using `java -jar workbook-0.0.1.jar`.

![Screen Shot 2022-09-17 at 12.54.22 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fd4961681-7242-4f05-9f5e-ae828ddebdc3?alt=media&token=4c415578-350a-499d-a297-837b29aa75cf)

## Recap
- `mvnw package` packages your application into a `jar` file.
- `java -jar` runs all of the compiled classes inside of the jar file – essentially, running your app!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!