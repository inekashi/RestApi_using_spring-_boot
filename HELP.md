GET (Used to read the data)
1) Create the controller.
2) In that controller, use @Autowired for Spring to handle the object creation of FakeDatabase instead of creating the object manually.
3) Create the endpoints using the @GetMapping annotation.
4) In the endpoint, return the FakeDatabase, which will return the data in the format of a list containing objects of type students.
5) Create the "students" POJO class, which represents the data.
6) Use a static method in the FakeDatabase to avoid creating a new object every time it's called (prevents potential future problems).

POST (Used to create new data)
1) Create a @GetMapping to enable the functionality, then write a @PostMapping method.
2) In the @PostMapping method, use @RequestBody to accept JSON data from the user.
3) Convert the received JSON data into a POJO class (students).
4) Call the FakeDatabase method to add the new data.
5) In the FakeDatabase, create a List<students> return type to handle the data, and ensure the data is in students format.
6) Use the students object and add the received data to the list.

DELETE (Used to delete existing data)
1) Use the name or ID (or any unique identifier) to find the data in the list that needs to be deleted.
2) Use @DeleteMapping to handle the delete operation.
3) In the void function, use @PathVariable("id") to get the ID from the user.
4) Call the FakeDatabase method and pass the ID to it.
5) Inside the FakeDatabase method, use a loop (e.g., forEach) to find the record by ID and use the .remove() method to delete the item from the list.

CRUD Operations Using JSP and MySQL
1) Use @Autowired to inject the repository into the controller (e.g., public UserRepository userRepository).
2) Define a function in the controller with a return type of List<students>.
3) In this function, call the userRepository.findAll() method, which is part of the repository.
4) Return the result after typecasting it to a List.
5) In the controller, simply call this function to retrieve the data.
6) To fetch a single record, use findById() and pass the ID to it.

PUT (Used to update data)
1) To update an existing value, use @RequestBody and then call the userRepository.save() method to persist the updated data.

DELETE (Used to delete data)
1) To delete a record, use @PathVariable to retrieve the user ID.
2) Call the deleteById() method to remove the record from the database.

Nested Custom
1) A nested class is a class inside another class (like a loop within a loop).
2) The "students" class is the parent class, and "Life" is the child class.
3) In the "Life" class, define fields like hobby, die, and an ID (primary key).
4) Use @Entity and @GeneratedValue to automatically generate the ID.
5) In the "students" class, use @OneToOne to define the relationship between the parent and child entities.
6) Use @OneToOne(cascade = CascadeType.ALL) to ensure that operations like create, update, and delete happen simultaneously on both parent and child.

@JsonManagedReference and @JsonBackReference
1) These annotations are used to prevent an infinite loop when accessing entities from child entities.
2) In the "Life" class (child), use @JsonBackReference to prevent infinite recursion when accessing parent data.
3) In the "students" class (parent), use @JsonManagedReference to manage the parent-child relationship and stop the infinite loop during serialization.
