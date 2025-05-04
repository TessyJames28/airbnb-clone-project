# AirBnB Clone Project
## An Overview
The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts.


## Project Goal
1. **User Management:** Implement a secure system for user registration, authentication, and profile management.
2. **Property Management:** Develop features for property listing creation, updates, and retrieval.
3. **Booking System:** Create a booking mechanism for users to reserve properties and manage booking details.
4. **Payment Processing:** Integrate a payment system to handle transactions and record payment details.
5. **Review System:** Allow users to leave reviews and ratings for properties.
6. **Data Optimization:** Ensure efficient data retrieval and storage through database optimizations.


## Technology Stack
- **Django:** A high-level Python web framework used for building the RESTful API.
- **Django REST Framework:** Provides tools for creating and managing RESTful APIs.
- **PostgreSQL:** A powerful relational database used for data storage.
- **GraphQL:** Allows for flexible and efficient querying of data.
- **Celery:** For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis:** Used for caching and session management.
- **Docker:** Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines:** Automated pipelines for testing and deploying code changes.


## Team Roles and Responsibilities
- **Backend Developer:** Responsible for implementing API endpoints, database schemas, and business logic and
 solves any technical problems emerging during the development lifecycle.
- **Database Administrator:** Manages database design, indexing, and optimizations.
- **DevOps Engineer:** Handles deployment, monitoring, and scaling of the backend services and facilitates
 cooperation between development and operations teams. The DevOp builds continuous integration and continuous
 delivery (CI/CD) pipelines for faster delivery.
- **QA Engineer:** Ensures the backend functionalities are thoroughly tested and meet quality standards by
 spotting functional and non-functional defects for improvement. They evaluate an application from different
 angles—be it functionality, usability, security, or performance (hence, many types of testing). 


## Database Design
1. `User`
   - Fields:

     - `id:` Unique identifier for the user
     - `name:` Full name
     - `email:` Used for login and communication
     - `password_hash:` Encrypted password for authentication
     - `is_host:` Boolean indicating if user can list properties

   - Relationships:
     - A user can own multiple properties
     - A user can make multiple bookings
     - A user can leave multiple reviews
     - A user can make multiple payments

2. `Property`
   - Fields:

     - `id:` Unique identifier for the property
     - `owner_id:` Foreign key to User
     - `title:` Name or headline of the listing
     - `location:` City, address, or coordinates
     - `price_per_night:` Cost per night

   - Relationships:

     - A property belongs to one user (host)
     - A property can have many bookings
     - A property can have many reviews

3. `Booking`
   Fields:

id: Unique identifier for the booking

user_id: Foreign key to User (guest)

property_id: Foreign key to Property

start_date: Check-in date

end_date: Check-out date

Relationships:

A booking belongs to one property

A booking is made by one user

A booking can have one payment record

4. Payment
Fields:

id: Unique identifier for the payment

booking_id: Foreign key to Booking

amount: Payment amount

status: e.g., pending, completed, failed

payment_method: e.g., credit card, PayPal

Relationships:

A payment is linked to one booking

A user indirectly relates to payment via their bookings

5. Review
Fields:

id: Unique identifier for the review

user_id: Foreign key to User (reviewer)

property_id: Foreign key to Property

rating: e.g., 1–5 stars

comment: Text content of the review

Relationships:

A review is left by one user

A review is linked to one property

