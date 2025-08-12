# WorkO
# Job Portal Web Application 🚀

A comprehensive job portal platform built with Java, JSP, and MySQL that connects job seekers with employers. This full-stack application provides an intuitive interface for job searching, application management, and administrative controls.

## 📌 Key Features

### For Job Seekers
- Create and manage professional profiles
- Search jobs using advanced filters (location, salary, experience level)
- Track application status in real-time
- Save favorite job listings
- Receive email notifications for application updates

### For Administrators
- Comprehensive dashboard with analytics
- User management system
- Job posting moderation tools
- Generate reports on platform usage
- Manage company profiles and verifications

## 🛠️ Technical Stack

### Backend
- **Java** - Core application logic and business rules
- **JSP (JavaServer Pages)** - Dynamic web page generation
- **Servlets** - Handle HTTP requests and responses
- **MySQL** - Data persistence and management

### Frontend
- **HTML5** - Structure and content
- **CSS3** - Styling and animations
  - Flexbox for flexible layouts
  - Grid system for complex arrangements
  - Media queries for responsiveness
- **JavaScript** - Interactive features and form validation

### Tools & Libraries
- **JDBC** - Database connectivity
- **jQuery** - DOM manipulation and AJAX calls
- **Bootstrap** - Responsive design framework
- **Font Awesome** - Icons and visual elements

## 🔧 Setup and Installation

### Prerequisites
- JDK 8 or higher
- MySQL 5.7+
- Apache Tomcat 9.0
- Maven (for dependency management)

### Database Setup
```sql
CREATE DATABASE job_portal;
USE job_portal;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100) NOT NULL,
    role VARCHAR(20) DEFAULT 'USER',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE jobs (
    job_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100) NOT NULL,
    company VARCHAR(100) NOT NULL,
    location VARCHAR(100),
    description TEXT,
    requirements TEXT,
    salary_range VARCHAR(50),
    posted_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Configuration Steps
1. Clone the repository
```bash
git clone https://github.com/smash-19/job-folio.git
cd job-folio
```

2. Configure database connection in `src/main/resources/db.properties`:
```properties
db.url=jdbc:mysql://localhost:3306/job_portal
db.username=your_username
db.password=your_password
db.driver=com.mysql.cj.jdbc.Driver
```

3. Deploy to Tomcat
   - Build the WAR file using Maven
   - Deploy to Tomcat's webapps directory

## 🏗️ Project Structure
```
job-portal/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── controllers/
│   │   │   ├── models/
│   │   │   ├── dao/
│   │   │   └── utils/
│   │   ├── webapp/
│   │   │   ├── WEB-INF/
│   │   │   ├── css/
│   │   │   ├── js/
│   │   │   └── views/
│   │   └── resources/
│   └── test/
├── pom.xml
└── README.md
```

## 💻 Usage Examples

### User Registration
```java
// Example API endpoint for user registration
@WebServlet("/register")
public class RegisterServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, 
                         HttpServletResponse response) 
                         throws ServletException, IOException {
        String username = request.getParameter("username");
        String password = request.getParameter("password");
        String email = request.getParameter("email");
        
        UserDAO userDao = new UserDAO();
        boolean success = userDao.registerUser(username, password, email);
        
        if (success) {
            response.sendRedirect("login.jsp");
        } else {
            request.setAttribute("error", "Registration failed");
            request.getRequestDispatcher("register.jsp")
                   .forward(request, response);
        }
    }
}
```

## 🔒 Security Features
- Session management
- Input validation and sanitization
- CSRF protection
- Prepared statements for SQL queries

## 🚀 Future Enhancements
- [ ] Implement OAuth 2.0 authentication
- [ ] Add resume parsing functionality
- [ ] Integrate real-time chat between employers and candidates
- [ ] Implement advanced search with ML recommendations
- [ ] Add mobile application support

## 👥 Contributing
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📧 Contact
Your Name - [samertechnologies@gmail.com](mailto:samertechnologies@gmail.com)
Project Link: [https://github.com/smash-19/job-folio](https://github.com/smash-19/job-folio)
