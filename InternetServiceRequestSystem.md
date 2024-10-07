
# Internet Services Request System

## Overview

This project implements a RESTful interface for managing customer requests related to internet services. The system allows users to request internet access, cancel subscriptions, and update user profiles with ID pictures. The implementation utilizes Spring Boot and integrates with Keycloak for robust security.

## Tech Stack

- **Spring Boot**: A Java-based framework that simplifies the setup and development of new Spring applications, providing features like dependency injection and embedded servers.
  
- **Spring Web**: A module that provides the necessary components for building web applications and RESTful services.

- **Keycloak**: An open-source Identity and Access Management solution that handles user authentication and authorization, allowing for centralized management of users and roles.

- **MongoDB**: A NoSQL document database used for storing user profiles and other related data, offering scalability and flexibility in data management.

- **Maven**: A build automation tool used for managing project dependencies and building the application.

- **Docker (optional)**: A platform for developing, shipping, and running applications in containers, ensuring consistency across environments.

- **JUnit**: A testing framework for Java that is used for writing and running tests to ensure application reliability.

- **Spring Security**: A powerful and customizable authentication and access control framework for Java applications, providing security features for RESTful services.

- **MultipartFile**: A Spring interface that represents an uploaded file, allowing for easy handling of file uploads in web applications.

### HTTP Endpoints

1. **Request Internet Access**
   - **URL**: `POST /api/v1/internet-access`
   - **Description**: Allows a user to request internet access with specified details.
   - **Request Body**:
     ```json
     {
       "serviceType": "Optic Fiber",
       "speed": "300"
     }
     ```
   - **Response Codes**:
     - `201 Created`: Successfully created a request order.
     - `400 Bad Request`: Invalid input parameters.
     - `500 Internal Server Error`: An unexpected error occurred.

2. **Cancel Subscription**
   - **URL**: `DELETE /api/v1/subscription/{subscriptionId}`
   - **Description**: Allows a user to cancel an existing subscription.
   - **Path Variable**: `subscriptionId` - ID of the subscription to cancel.
   - **Response Codes**:
     - `204 No Content`: Successfully canceled the subscription.
     - `404 Not Found`: Subscription not found.
     - `500 Internal Server Error`: An unexpected error occurred.

3. **Update User Profile**
   - **URL**: `PUT /api/v1/users/{userId}/profile`
   - **Description**: Allows a user to update their profile, including uploading a picture of their ID.
   - **Path Variable**: `userId` - ID of the user whose profile is to be updated.
   - **Request Body**: Multipart file upload for the ID picture.
   - **Response Codes**:
     - `200 OK`: Successfully updated the profile.
     - `400 Bad Request`: Invalid input parameters.
     - `404 Not Found`: User not found.
     - `500 Internal Server Error`: An unexpected error occurred.

## Security Considerations

**Input Validation**: Validate input parameters and file types to prevent harmful data.

**File Size Limitation**: Implement file size restrictions to avoid excessive resource usage.

**Using Keycloak for Authentication**

-   Login : Users will authenticate through Keycloak. 

-   Token Management: After authentication, Keycloak will provide a JWT token that must be sent in the Authorization header of subsequent API requests as a Bearer token.