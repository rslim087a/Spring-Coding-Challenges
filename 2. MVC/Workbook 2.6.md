# Workbook 2.6

![Screen Shot 2022-08-15 at 11.17.47 PM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc7225a6b-ccaa-4d58-8859-ec42b47e017a?alt=media&token=1d888dcc-71d3-4fc3-bb65-0105b243cbdb)

## Task 1

Inside the handler method, add two model attributes:
```java
   model.addAttribute("budget", 4000);
   model.addAttribute("make", "Toyota");
```

## Task 2
- If the entered `budget` is greater than or equal to $5000, compare the entered `make` against 5 cases:
   - **Toyota**: display `Toyota Corolla: $5,000`
   - **Volkswagen**: display `Volkswagen Jetta: $6,000`
   - **Ford**: display `Ford Escape: $7,000`
   - **Honda**: display `Honda Civic: $8,000`
   - **default**: display: `No cars match your query.`

- Otherwise, display: `Sorry, we don't have any cars below $5,000`. 

### Test Case: `budget`: `4000` | `make`: `Toyota` 
-----
![Screen Shot 2022-05-22 at 2.16.05 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F3d1e072f-6baa-429d-925d-985cf9f3fcae?alt=media&token=df1f9907-4e62-445c-bce3-022279ab7c60)


### Test Case: `budget`: `10000` | `make`: `Toyota` 
-----
![Screen Shot 2022-05-22 at 2.17.20 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2Fc8c2716d-3d3f-449c-8885-29ed0a1b1ae8?alt=media&token=17d095ab-3774-49a8-a5ca-b2cb311aeea3)

### Test Case: `budget`: `10000` | `make`: `Subaru`
-----
![Screen Shot 2022-05-22 at 2.18.14 AM.png](https://firebasestorage.googleapis.com/v0/b/learnthepart-75aed.appspot.com/o/images%2F7ca5459f-7648-41a5-82f3-378640264908?alt=media&token=d5e28710-c9a7-4a7b-885b-dda7a284a76f)

## Good Luck!

--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!