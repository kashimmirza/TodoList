# TodoList
This is a simple Todo application built with an ASP.NET Core backend and a React frontend. It includes functionalities for creating, updating, and deleting tasks, as well as marking them as complete.


Prerequisites
Before running this application, make sure you have the following installed on your machine:

.NET SDK (version 6.0 or later)
SQL Server (for the database)
Node.js (version 16.0 or later)
NPM (comes with Node.js)
                                                                                                    
  
  
  
  
  

Backend Setup (ASP.NET Core)
   1.Clone the Repository
     git clone https://github.com/kashimmirza/TodoList.git
     cd TodoList
     git checkout master
     cd Backend
     click Backend.sln( to load and prepare the project for run in visual studio)
    2. Configure the Database Connection
        Update the connection string in the appsettings.json file to point to your SQL Server instance:
           "ConnectionStrings": {
         "DefaultConnection": 
          "Server=YOUR_SERVER;Database=TodoAppDb;Trusted_Connection=True;MultipleActiveResultSets=true"
          }

    3. Setup the Database
       Run the following command to apply the migrations and create the database:
       dotnet ef database update
    4. install this NuGet package Swashbuckle.AspNetCore , 
           Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.SqlServer (for SQL Server)
         
    5.Run the Backend API
      Start the ASP.NET Core API server by running:
      dotnet run
      The API will be accessible at https://localhost:7128


Frontend Setup (React.js)
  1. Navigate to the Frontend Directory
       cd frontend
  2. Install Dependencies
        Install the required packages using npm:
              run the following command in frontend project to install all dependency:
                   npm install react react-dom
                   npm install @mui/material @mui/icons-material @emotion/react @emotion/styled
                   npm install axios

  3. Configure the Backend API URL
         Make sure the frontend is pointing to the correct backend API URL. Open the TodoList.js file and ensure 
         the API URL matches the backend:
         const response = await axios.get("https://localhost:7128/api/todo");
 4.Run the Frontend
     Start the React development server:
      npm start
     The React app will run at http://localhost:3000


1. Enabling CORS
To allow requests from your React frontend to the ASP.NET Core backend, CORS needs to be configured in the backend API.
    1. Add CORS in the Backend (Already added in the project):
          builder.Services.AddCors(options =>
          {
              options.AddPolicy("AllowAllOrigins", builder =>
             {
                   builder.AllowAnyOrigin().AllowAnyMethod().AllowAnyHeader();
              });
           });


 2.Use the CORS Policy in the request pipeline
     app.UseCors("AllowAllOrigins");



Now, you can access the frontend on http://localhost:3000 and it will communicate with the backend API running on https://localhost:7128.

Swagger for API Documentation
The backend API comes with Swagger UI enabled. Once the backend is running, you can view the API documentation by navigating to:

https://localhost:7128/swagger/index.html



Issues
If you encounter any issues, please feel free to open an issue in the repository or contact me via email at kashimmirza86@gmail.com.







