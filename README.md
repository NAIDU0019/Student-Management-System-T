

# 🎓 Student Management System

A **Spring Boot** web application for managing student information. It provides CRUD operations, search/filter functionality, input validation, and a responsive UI using **Thymeleaf**. The backend uses **Spring Data JPA** with an **H2 embedded database**.

---

## 🚀 Features

* Add, update, delete, and view student records.
* Search students by name or class.
* Filter and paginate student lists.
* Server-side input validation (e.g., valid email, age range).
* User-friendly UI with Thymeleaf.
* Error handling with meaningful messages.

---

## 🛠️ Technologies Used

* Java 17+
* Spring Boot
* Spring Data JPA
* H2 Embedded Database
* Thymeleaf
* Bootstrap (optional, for styling)

---

## 📦 Project Structure

```
student-management/
├── src/
│   ├── main/
│   │   ├── java/com/example/studentmanagement/
│   │   │   ├── controller/
│   │   │   ├── entity/
│   │   │   ├── repository/
│   │   │   └── service/
│   │   └── resources/
│   │       ├── templates/
│   │       ├── static/
│   │       └── application.properties
└── README.md
```

---

## 🧩 Entity: Student

```java
@Entity
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long studentId;

    @NotBlank
    private String name;

    @Min(5)
    @Max(100)
    private int age;

    @NotBlank
    private String studentClass;

    @Email
    private String email;

    @NotBlank
    private String address;
}
```

---

## 🌐 REST Endpoints / Web Routes

| Method | URL                     | Description            |
| ------ | ----------------------- | ---------------------- |
| GET    | `/students`             | List all students      |
| GET    | `/students/new`         | Show create form       |
| POST   | `/students`             | Add new student        |
| GET    | `/students/edit/{id}`   | Show update form       |
| POST   | `/students/update/{id}` | Update student         |
| GET    | `/students/delete/{id}` | Delete student         |
| GET    | `/students/search`      | Search/filter students |

---

## 🔍 Search & Filter

You can search students by name or filter by class via query parameters:

```
/students/search?name=John
/students/search?studentClass=10A
```

---

## 📄 Templates (Thymeleaf)

* `list.html`: Lists all students with pagination and search/filter options.
* `form.html`: Add/edit student form.
* `error.html`: Displays error messages.

---

## 💾 application.properties

```properties
spring.datasource.url=jdbc:h2:mem:studentdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
spring.thymeleaf.cache=false
server.error.whitelabel.enabled=false
```

---

## ✅ Validation Rules

* **Name**, **Class**, and **Address**: Must not be empty.
* **Email**: Must be a valid email format.
* **Age**: Must be between 5 and 100.

Handled using JSR-380 annotations (`@NotBlank`, `@Email`, `@Min`, `@Max`).

---

## 🧪 Running the Application

### Prerequisites

* Java 17+
* Maven

### Steps

```bash
git clone https://github.com/yourusername/student-management.git
cd student-management
mvn spring-boot:run
```

* Access the app at: `http://localhost:8080/students`
* H2 Console: `http://localhost:8080/h2-console` (JDBC URL: `jdbc:h2:mem:studentdb`)

---

## 🛑 Error Handling

* Validation errors are shown next to form fields.
* Not-found and server errors are displayed via a friendly error page.

---

## 📌 TODO / Future Enhancements

* Role-based access (admin/teacher).
* Export student data to CSV.
* Integration tests.
* REST API version with Swagger docs.

---

## 👨‍💻 Author

**Your Name**
GitHub: https://github.com/NAIDU0019

---

## 📝 License

This project is licensed under the MIT License.

---

