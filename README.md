# spring-clould-filebackend-and-propertiespriority

Dependencies:
for confserver:"spring-cloud-config-server".
for client: "Spring Cloud Starter Config".

I this project we set up to a file system repository rather than GIT by using two properties on Config-Server : "spring.profiles.active" for repository type and "spring.cloud.config.server.native.search-locations" for the location of our properties files. To activate priority we should set the property 'spring.cloud.config.name' in bootstrap file to the name of our microservice in our case users-ws. In the repo dir, we created two property files: 'application.properties' this file is shared for all microservices and 'users-ws.properties' was specified for users microservice. That means users microservice would use the two properties files but if the same property appeares in the two files then the 'users-ws.properties' priority has the higher priority.

Run example steps:

1. post : http://localhost:8011/users-ws/users
   body : 
   <UserResposeModel>
    <firatname>Ziad</firatname>
    <lastname>Jamal</lastname>
    <email>alaajamal470@gmail.com</email>
    <userId>2eeaec6f-4092-46d1-ba23-b84ce1006d97</userId>
   </UserResposeModel>
   
2. post : http://localhost:8011/users-ws/users/login
   body :
    {
    "email":"alaajamal470@gmail.com",
    "password":"154454588"
    }
3. get : http://localhost:8011/users-ws/users/status/check
   Header :
   Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIyZWVhZWM2Zi00MDkyLTQ2ZDEtYmEyMy1iODRjZTEwMDZkOTciLCJleHAiOjE1OTUyNjk5ODN9.cIZOTV8gfZtQTa0_odhkrN2TFPvbYCTD8WbwyIPQKmg
   this header was taken from the successful login request in step2.
   
 you will notice that the specified property in 'users-ws.properties' with apear after the 3rd request.
