# airbnb-clone-project
## Team Roles

Each team member contributes to the success of the project by fulfilling specific roles and responsibilities. Below is a summary of the core roles:

- **Project Manager**: Oversees the entire project lifecycle, ensures timelines and milestones are met, and acts as a liaison between stakeholders and the development team.

- **Backend Developer**: Responsible for implementing the server-side logic, APIs, authentication systems, and business logic. Ensures scalability, performance, and security of the application.

- **Database Administrator (DBA)**: Designs, optimizes, and maintains the database. Ensures data integrity, security, and efficient access to information for other components.

- **Quality Assurance (QA) Engineer**: Develops and executes manual and automated tests to ensure software reliability, usability, and performance before deployment.

- **DevOps Engineer**: Handles the infrastructure, CI/CD pipelines, deployment processes, and system monitoring. Ensures smooth integration between development and operations.



## Technology Stack

The following technologies were used in this project, each serving a specific role in the system's architecture:

- **Django**: A high-level Python web framework used for rapid development of secure and scalable web applications. In this project, it is used to build RESTful APIs and manage server-side logic.

- **PostgreSQL**: An advanced open-source relational database system. It is used to store and manage structured data efficiently with support for complex queries.

- **GraphQL**: A query language for APIs that allows clients to request exactly the data they need. It helps reduce over-fetching and under-fetching of data, improving API performance and flexibility.

- **Docker**: A containerization tool used to package the application and its dependencies, ensuring consistent environments across development and production.

- **Nginx**: A web server used to serve the application, handle static files, and act as a reverse proxy for load balancing and performance optimization.

- **Redis**: An in-memory data store used for caching and real-time data processing to improve the application’s speed and responsiveness.

- **GitHub Actions**: A CI/CD tool used to automate testing and deployment workflows directly from the GitHub repository.


## Feature Breakdown

The Airbnb Clone project replicates the core functionality of a real-world booking platform, providing a seamless experience for both property owners and travelers. Below are the main features and how each contributes to the overall system.

### 🔐 User Management
Allows users to register, log in, and manage their profiles securely. The system supports role-based access, distinguishing between property owners and guests.

### 🏘️ Property Management
Enables property owners to list, update, and delete properties. Each listing includes details such as location, pricing, availability, and photos, providing travelers with the information they need to book confidently.

### 📅 Booking System
Allows guests to check availability, reserve properties, and manage bookings. The system prevents overlapping bookings and ensures availability is accurately reflected.








## Database Design   

The project’s database is structured around core entities that support user interactions, property listings, and booking workflows. Below are the key entities, their essential fields, and their relationships.

### 🧑 Users
Represents individuals using the platform, either as property owners or customers.

**Key Fields:**
- `id` (Primary Key)
- `name`
- `email` (Unique)
- `password_hash`
- `role` (e.g., owner, customer)

**Relationships:**
- A user can own multiple properties.
- A user can make multiple bookings and leave multiple reviews.

---

### 🏠 Properties
Represents real estate listings available for booking.

**Key Fields:**
- `id` (Primary Key)
- `owner_id` (Foreign Key to Users)
- `title`
- `description`
- `location`
- `price_per_night`

**Relationships:**
- Each property is owned by one user.
- A property can have multiple bookings and reviews.

---

### 📅 Bookings
Tracks reservations made by users for properties.

**Key Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `check_in_date`
- `check_out_date`
- `status` (e.g., confirmed, canceled)

**Relationships:**
- Each booking is made by a user for a specific property.
- Each booking can be associated with one payment.

---

### 💳 Payments
Stores transaction details for completed bookings.

**Key Fields:**
- `id` (Primary Key)
- `booking_id` (Foreign Key to Bookings)
- `amount`
- `payment_method` (e.g., credit card, PayPal)
- `payment_status`

**Relationships:**
- Each payment is linked to one booking.

---

### ⭐ Reviews
Allows users to leave feedback on properties they have booked.

**Key Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `rating` (1 to 5)
- `comment`

**Relationships:**
- A user can leave multiple reviews.
- Each review is tied to a specific property.

---

### 🔄 Entity Relationships Summary

- **User ↔ Properties**: One-to-Many (a user can own many properties)
- **User ↔ Bookings**: One-to-Many (a user can make many bookings)
- **User ↔ Reviews**: One-to-Many (a user can write many reviews)
- **Property ↔ Bookings**: One-to-Many (a property can have many bookings)
- **Property ↔ Reviews**: One-to-Many (a property can have many reviews)
- **Booking ↔ Payment**: One-to-One (each booking has one payment)



## API Security

Securing backend APIs is critical to ensuring data protection, system integrity, and user trust. The Airbnb Clone project implements multiple layers of security to safeguard sensitive operations and prevent unauthorized access.

### 🔐 Authentication
All users must authenticate using secure methods (e.g., token-based authentication such as JWT). This ensures that only registered users can access protected routes and resources.

**Why it's important:** Prevents unauthorized access to user accounts, property data, and booking details.

---

### 🛂 Authorization
Role-based access control (RBAC) is implemented to ensure users can only perform actions permitted by their role (e.g., guests can't delete listings, only property owners can manage their properties).

**Why it's important:** Protects the platform from abuse and enforces data ownership and accountability.

