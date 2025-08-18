Tech Stack
Backend:
![alt text](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
![alt text](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
Database:
![alt text](https://img.shields.io/badge/Entity%20Framework-512BD4?style=for-the-badge)
(with SQLite Azure Data Studio)
Frontend:
![alt text](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![alt text](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![alt text](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)

# 🎬 Fullstack Movies API

FullstackMoviesApi is a **portfolio project** designed to demonstrate a wide range of full-stack development skills.  

It showcases the implementation of complex data models with many-to-many relationships (movies, actors, genres, theaters), secure authentication with role-based authorization, and seamless integration with cloud services like **Azure Storage** for media management.  

The application allows **regular users** to browse, filter, and rate movies, while providing a powerful and exclusive **administrative dashboard** for managing all content.

---

## ✨ Key Features

### 🔐 Secure Authentication & Authorization
- User registration and JWT-based login system using **.NET Identity**.  
- Role-based access control (**Admin vs. User**).  
- Admins have exclusive rights to create, edit, and delete content.  
- Admins can promote or revoke other users’ admin status.  

### 🎬 Dynamic Movie Catalog
- Advanced filtering by **genre, title, upcoming releases, and in-theaters status**.  
- **Paginated results** for smooth browsing.  
- Users can view movie details and **submit ratings**.  

### ⚙️ Comprehensive Admin Dashboard
- Full **CRUD** (Create, Read, Update, Delete) operations for Movies, Actors, Genres, and Theaters.  
- Rich form handling with **react-hook-form**.  
- Typeahead/autocomplete functionality for selecting actors when creating/editing movies.  

### ☁️ Cloud Integration
- Movie posters and actor images uploaded and served from **Azure Blob Storage**.  

### 🗺️ Interactive Maps
- Movie theater locations displayed on an **interactive Leaflet map**.  

---

## 🛠 Tech Stack

| Category       | Technology |
|----------------|------------|
| **Backend**    | .NET 9, ASP.NET Core Web API, Entity Framework Core, ASP.NET Core Identity, RESTful API |
| **Frontend**   | React, Vite, TypeScript, Axios, React Hook Form, Context API & Custom Hooks |
| **Database**   | SQL Server / PostgreSQL (via EF Core) |
| **Cloud & DevOps** | Azure Blob Storage (media), Azure App Service (deployment) |
| **Libraries**  | Leaflet (maps), Typeahead.js, SweetAlert2, Bootstrap |

---

## 🚀 Getting Started: Full Setup & Run Guide

### ✅ Prerequisites
Make sure you have the following installed:
- [.NET SDK (7 or 8)](https://dotnet.microsoft.com/en-us/download)  
- [Node.js & npm](https://nodejs.org/)  
- [Git](https://git-scm.com/)  
- An **Azure Storage account** (for file upload functionality). You’ll need the connection string.  
- EF Core Tools (if not installed):  
  ```bash
  dotnet tool install --global dotnet-ef

### 1️ Clone the Repository (with Submodules)

This is a critical step. You must use the `--recurse-submodules` flag to clone both the main repo and the nested **client** and **server** repos at the same time:

```bash
  git clone --recurse-submodules <your-repo-url>
  cd FullstackMoviesApi
  git submodule update --init --recursive
```

### 2 Configure Application Settings:
Open the appsettings.Development.json file. You need to add your database connection string and your Azure Storage connection string
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost; Database=MoviesApi; Trusted_Connection=true; TrustServerCertificate=true",
    "AzureStorageConnection": "your connection string with this service"
  },
  "allowedOrigins": "http://localhost:5173",
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "keyjwt": "A random key"
}
```
### 3 Configure and Set Up the Backend (Server)
```bash
  cd server
  dotnet ef migrations add InitialCreate            
  dotnet ef database update
  dotnetrun
```
.env file: VITE_API_URL=http://localhost:5000/api

### 4 Configure Frontend
```bash
npm install
npm run dev
```


