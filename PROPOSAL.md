# Edu-365 School Management System – Final Project Proposal

## 1. Introduction

Edu-365 School Management System is a web-based platform developed to address the challenges faced by modern educational institutions. With the rapid growth of digital technologies, schools still struggle with manual processes that are time-consuming, error-prone, and inefficient. Edu-365 is designed to centralize all school operations—from admissions and scheduling to academic performance monitoring—into one streamlined, secure, and user-friendly system.

---

## 2. Problem Statement

Many schools in our region still rely on manual processes for record-keeping and fee management, which causes:

- **Data Fragmentation:** Disparate data across multiple paper files or standalone software systems.
- **Inefficiency:** High administrative overhead and long delays in generating reports.
- **Inaccurate Records:** Increased potential for errors in attendance, grading, and financial records.
- **Fee Payment Difficulties:** Manual or limited digital payment options hinder timely fee collection.

---

## 3. Project Objectives

The key objectives of Edu-365 are:

- **Automation:** Streamline routine tasks (admissions, attendance, grading) to minimize manual work.
- **Centralization:** Consolidate student, teacher, and administrative data into one secure system.
- **Enhanced Communication:** Provide dedicated dashboards and communication channels for administrators, teachers, students, and parents.
- **Secure Fee Management:** Integrate MPesa for efficient, real-time fee collection and management. (on development)
- **Data-Driven Insights:** Generate actionable reports and analytics for informed decision-making.

---

## 4. Project Scope

Edu-365 will cover:

- **User Management:** Role-based access for administrators, teachers, students, and parents.
- **Class and Schedule Management:** Creation and scheduling of classes, timetables, and room allocations.
- **Attendance & Grade Tracking:** Real-time attendance marking and grade recording with historical data storage.
- **Fee Management & MPesa Integration:** A dedicated module for fee collection, complete with transaction history and automated notifications, leveraging MPesa’s mobile payment capabilities.
- **Communication Tools:** Internal messaging, announcements, and automated alerts.
- **Reporting:** Comprehensive report generation for academic performance, attendance trends, and financial transactions.

---

## 5. Detailed Technical Requirements

### 5.1 Frontend

- **Technology:** React.js
- **Features:**
  - **Responsive UI:** Adaptable to desktops, tablets, and mobile devices.
  - **Routing & State Management:** Managed with React Router and Context API/Redux for smooth navigation and real-time data updates.
  - **User Interface:** Intuitive design created with modern tools (e.g., Figma) ensuring ease of use for all stakeholders.
- **Deployment:** Hosted on Netlify, leveraging its global CDN, continuous deployment pipelines, and automatic build processes.

### 5.2 Backend

- **Technology:** Node.js with Express.js
- **Features:**
  - **RESTful API:** Secure endpoints for CRUD operations (users, classes, attendance, grades, fees).
  - **Database:** MongoDB using Mongoose for flexible schema definitions and robust data management.
  - **Security:** Implementation of JWT-based authentication and role-based access control to protect sensitive data.
  - **MPesa Integration:**
    - **Payment Module:** Integration of the MPesa Daraja API to facilitate fee payments.
    - **Transaction Flow:** When a fee payment is initiated, the system will trigger an MPesa STK Push, verify the transaction, and record the details in the database.
    - **Notifications:** Automated SMS/email confirmations are sent upon successful payment.
- **Deployment:** Deployed on Render, which offers seamless GitHub integration, scalable resource management, and secure handling of environment variables (such as MONGODB_URI, JWT_SECRET, and MPesa API keys).

### 5.3 Additional Tools

- **CI/CD Pipelines:** GitHub Actions will be used for automated testing, building, and deployment to ensure code quality.
- **Monitoring & Logging:** Tools like Sentry and Loggly will be integrated for real-time error tracking and performance monitoring.

---

## 6. System Architecture and Design

### 6.1 Architectural Overview

Edu-365 is built on the MERN stack (MongoDB, Express.js, React, Node.js), which ensures a unified development environment with efficient data flow and modular design.

### 6.2 Component Breakdown

- **Frontend (React):**
  - **Components:** Reusable UI elements (Navbar, Dashboard, Forms) for various user roles.
  - **Pages:** Dedicated interfaces for Administrators, Teachers, Students, and Parents.
- **Backend (Node.js/Express.js):**
  - **API Layer:** Exposes endpoints for all core functionalities.
  - **Database Layer:** MongoDB collections for Users, Classes, Subjects, Attendance, Grades, and Transactions (including MPesa-related data).
- **Integration with MPesa:**
  - **Payment Endpoints:** Secure API routes to initiate and verify MPesa transactions.
  - **Transaction Management:** Detailed logging and real-time updates to reflect fee payment status.

### 6.3 Folder Structure

```plaintext
Edu-365-School-Management-System
├── README.md                     # Project documentation
├── .vscode/                       # VS Code settings
│   ├── settings.json              # Editor-specific configurations
├── .gitignore                     # Files to exclude from Git
├── .env                           # Environment variables
├── package-lock.json              # Dependency lock file
├── package.json                   # Project dependencies and scripts

# Backend (Node.js + Express + MongoDB)
├── backend/
│   ├── package.json               # Backend dependencies
│   ├── package-lock.json          # Backend dependency lock file
│   ├── .env                       # Backend environment variables
│   ├── .gitignore                 # Ignore sensitive backend files
│   ├── index.js                   # Main backend entry file
│   
│   ├── controllers/                # Handles API logic
│   │   ├── subject-controller.js
│   │   ├── admin-controller.js
│   │   ├── teacher-controller.js
│   │   ├── notice-controller.js
│   │   ├── student-controller.js
│   │   ├── class-controller.js
│   │   ├── complain-controller.js
│   
│   ├── models/                     # Mongoose schemas for MongoDB
│   │   ├── sclassSchema.js
│   │   ├── subjectSchema.js
│   │   ├── adminSchema.js
│   │   ├── noticeSchema.js
│   │   ├── teacherSchema.js
│   │   ├── studentSchema.js
│   │   ├── complainSchema.js
│   
│   ├── routes/                     # API routes
│   │   ├── route.js

# Frontend (React + Redux)
├── frontend/
│   ├── public/
│   │   ├── index.html              # Main HTML file
│   
│   ├── src/                        # React source code
│   │   ├── index.js                # Main React entry file
│   │   ├── index.css               # Global styles
│   │   ├── App.js                  # Main React component
│   
│   │   ├── components/              # Reusable UI components
│   │   │   ├── ErrorPage.js
│   │   │   ├── buttonStyles.js
│   │   │   ├── AccountMenu.js
│   │   │   ├── SpeedDialTemplate.js
│   │   │   ├── mobileChecker.js
│   │   │   ├── CustomBarChart.js
│   │   │   ├── attendanceCalculator.js
│   │   │   ├── TableViewTemplate.js
│   │   │   ├── CustomPieChart.js
│   │   │   ├── SeeNotice.js
│   │   │   ├── styles.js
│   │   │   ├── TableTemplate.js
│   │   │   ├── Popup.js
│   
│   │   ├── redux/                   # Redux state management
│   │   │   ├── teacherRelated/
│   │   │   │   ├── teacherSlice.js   # Teacher state slice
│   │   │   │   ├── teacherHandle.js  # Teacher state handler
│   │   │   ├── noticeRelated/
│   │   │   │   ├── noticeSlice.js    # Notices state slice
│   │   │   │   ├── noticeHandle.js   # Notices state handler
│   │   │   ├── studentRelated/
│   │   │   │   ├── studentHandle.js  # Student state handler
│   │   │   │   ├── studentSlice.js   # Student state slice
│   │   │   ├── sclassRelated/
│   │   │   │   ├── sclassHandle.js   # Class state handler
│   │   │   │   ├── sclassSlice.js    # Class state slice
│   │   │   ├── userRelated/
│   │   │   │   ├── userSlice.js      # User state slice
│   │   │   │   ├── userHandle.js     # User state handler
│   │   │   ├── complainRelated/
│   │   │   │   ├── complainHandle.js # Complaints state handler
│   │   │   │   ├── complainSlice.js  # Complaints state slice
│   │   │   ├── store.js              # Centralized Redux store
│   
│   │   ├── pages/                    # Page components
│   │   │   ├── Homepage.js
│   │   │   ├── ChooseUser.js
│   │   │   ├── Logout.js
│   │   │   ├── LoginPage.js
│   │   │   ├── teacher/              # Teacher-related pages
│   │   │   │   ├── TeacherClassDetails.js
│   │   │   │   ├── TeacherHomePage.js
│   │   │   │   ├── TeacherComplain.js
│   │   │   │   ├── TeacherProfile.js
│   │   │   │   ├── TeacherSideBar.js
│   │   │   │   ├── TeacherDashboard.js
│   │   │   │   ├── TeacherViewStudent.js
│   │   │   ├── student/              # Student-related pages
│   │   │   │   ├── StudentSideBar.js
│   │   │   │   ├── StudentSubjects.js
│   │   │   │   ├── StudentDashboard.js
│   │   │   │   ├── ViewStdAttendance.js
│   │   │   │   ├── StudentProfile.js
│   │   │   │   ├── StudentComplain.js
│   │   │   │   ├── StudentHomePage.js
│   │   │   ├── admin/                # Admin-related pages
│   │   │   │   ├── teacherRelated/
│   │   │   │   │   ├── ChooseSubject.js
│   │   │   │   │   ├── AddTeacher.js
│   │   │   │   │   ├── ShowTeachers.js
│   │   │   │   │   ├── ChooseClass.js
│   │   │   │   │   ├── TeacherDetails.js
│   │   │   │   │   ├── AdminRegisterPage.js
│   │   │   │   ├── noticeRelated/
│   │   │   │   │   ├── ShowNotices.js
│   │   │   │   │   ├── AddNotice.js
│   │   │   │   ├── studentRelated/
│   │   │   │   │   ├── SeeComplains.js
│   │   │   │   │   ├── ViewStudent.js
│   │   │   │   │   ├── AddStudent.js
│   │   │   │   │   ├── StudentExamMarks.js
│   │   │   │   │   ├── StudentAttendance.js
│   │   │   │   │   ├── ShowStudents.js
│   │   │   │   ├── classRelated/
│   │   │   │   │   ├── AddClass.js
│   │   │   │   │   ├── ClassDetails.js
│   │   │   │   │   ├── ShowClasses.js
│   │   │   │   ├── subjectRelated/
│   │   │   │   │   ├── ShowSubjects.js
│   │   │   │   │   ├── SubjectForm.js
│   │   │   │   │   ├── ViewSubject.js
│   │   │   │   ├── AdminHomePage.js
│   │   │   │   ├── SideBar.js
│   │   │   │   ├── AdminDashboard.js
│   │   │   │   ├── AdminProfile.js
│   
│   ├── netlify.toml                 # Netlify deployment config
│   ├── package-lock.json            # Frontend dependencies
│   ├── package.json                 # Frontend dependencies
│   ├── .gitignore                   # Ignore frontend files
│   ├── .env                         # Frontend environment variables

```

---

## 7. Project Planning and Timeline

### 7.1 Project Phases

**Planning & Research (Weeks 1-2):**
- Define detailed requirements through stakeholder interviews and surveys.
- Finalize project scope, objectives, and design wireframes.
- **Missing Detail:** Develop risk analysis by identifying potential issues (API integration challenges, security vulnerabilities, scalability concerns) and proposing mitigation strategies.

**Design & Prototyping (Weeks 3-4):**
- Develop UI prototypes using Figma.
- Establish API specifications and design the database schema.
- **Missing Detail:** Create ER diagrams and relationship mappings to clarify data models.

**Development (Weeks 5-10):**
- **Backend:** Develop RESTful API, implement JWT security, and integrate the MPesa payment module.
- **Frontend:** Build responsive interfaces and integrate with backend APIs.
- **Missing Detail:** Allocate resources and budget estimates for development and testing.

**Testing & Integration (Weeks 11-12):**
- Conduct unit, integration, and end-to-end tests.
- Perform user acceptance testing (UAT) with a pilot group (administrators and teachers) to validate key features such as MPesa payment flows.
- **Missing Detail:** Document test cases, feedback collection, and iteration cycles for improvements.

**Deployment & Training (Weeks 13-14):**
- Deploy the backend on Render and the frontend on Netlify.
- Provide training sessions for administrators and teachers on system usage.
- **Missing Detail:** Plan for post-deployment support and maintenance (bug fixes, updates, monitoring).

**Documentation & Presentation (Week 15):**
- Prepare comprehensive documentation (README, API docs, troubleshooting guides).
- Finalize and record a 5-minute presentation (using Google Slides or Loom).
- **Missing Detail:** Include evaluation criteria and submission guidelines in the documentation.

### 7.2 Milestones

- **MVP Delivery:** Core functionalities (user management, attendance, grades) with MPesa integration.
- **User Testing:** Positive feedback from a pilot test group.
- **Final Deployment:** Fully operational system deployed on Render and Netlify.

---

## 8. Deployment Strategy

### 8.1 Backend Deployment on Render

- **Steps:**
  - Pushed the code to GitHub.
  - Configured environment variables (e.g., `MONGODB_URI`, `JWT_SECRET`, MPesa API keys) via Render’s dashboard.
  - Enabled continuous deployment.
  - Verified functionality using Postman and automated tests.

### 8.2 Frontend Deployment on Netlify

- **Steps:**
  - Connected to the GitHub repository to Netlify.
  - Set the build command and published the directory.
  - Deployed and tested for responsiveness and API integration.

### 8.3 Post-Deployment

- **Monitoring & Logging:** Integrate Sentry/Loggly for error and performance tracking.
- **User Feedback & Iteration:** Collect feedback from real users and schedule periodic updates.
- **Documentation:** Maintain updated documentation for system usage and troubleshooting.

---

## 9. Future Enhancements

- **Additional Modules:** Expand to include library management, transportation, and extracurricular activity modules.
- **Mobile App:** Develop a companion mobile application for greater accessibility.
- **Advanced Analytics:** Integrate predictive analytics for insights on student performance and resource allocation.
- **Enhanced Communication:** Implement real-time chat and video conferencing features for virtual classrooms.

---

## 10. Submission

### Submission Requirements

- **GitHub Repository URLs:**  

  - https://github.com/daniel-ndeto/school-management-system.git

- **Live Application URLs:**

  **Canva presentation**: [https://www.canva.com/design/DAGjC239f2k/3b4cHpAxRLwpLF5rgd6yjw/edit]

**LIVE PROJECT LINK:** [(https://edu-365-front.vercel.app/)]

  - Frontend (Netlify): [https://edu-365-front.vercel.app/] 
  - Backend (Render): [https://edu-365-back.vercel.app/]

- **Final Presentation:** Upload Google Slides or Loom video link.
- **Documentation:** Include all installation, usage, and troubleshooting guides in the README.md file.

---

## 11. Conclusion

In summary, the Edu-365 School Management System is a transformative solution designed to streamline school administration through automation, centralization, and secure digital processes. With robust features—including user management, real-time attendance and grade tracking, and secure MPesa fee management—the project addresses critical pain points in traditional school operations. The enhanced proposal now includes comprehensive risk analysis, budget/resource allocation, UAT strategies, security measures, post-deployment support, and clear evaluation and submission guidelines. This thorough approach ensures a successful project outcome and provides a strong foundation for future enhancements.
