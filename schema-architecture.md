

    This Spring Boot application uses both MVC and REST controllers. Thymeleaf templates are used for the Admin and Doctor dashboards, while REST APIs serve all other modules. The application interacts with two databases—MySQL (for patient, doctor, appointment, and admin data) and MongoDB (for prescriptions). All controllers route requests through a common service layer, which in turn delegates to the appropriate repositories. MySQL uses JPA entities while MongoDB uses document models. The models are then used to send back responses , completing the request-response  cycle . 


1. User accesses  Dashboards(Admin or Doctor) and  other frontend modules.
2. The action is routed to the appropriate Thymeleaf(for Dashboards) or REST controller(for other pages) based on the URL path and HTTP method .
3. The logic part(validation , business logic , routing to repos) is handed to the service layer by the controller layer . It lies between controller and data access layer and makes the application more testable and scalable  .
4. Repository layer simplifies data access operations by abstracting database access logic . This layer contains two repositories mainly MySQL (for structured data like admin , doctor , records etc.) and MongoDB(for unstructured data like prescriptions) .
5. The repositories above interface with database engines(MySQL and MongoDB) in this step .
6. Data from the database once received is modelled into Java model classes that the application can work with called Model Binding(OO representation of the Data) . Mysql data -> JPA Entities(@Entity) , MongoDB data -> Document Objects with @Document (further maps to JSON / BSON in collections) .
7. Application models from the previous step are used in this step. In MVC flows , controller sends models to Thymeleaf templates which are rendered as dynamic html in the browser .
In REST flows models are serialized into json and are sent back to the client as part of an HTTP response .