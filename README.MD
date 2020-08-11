13 .- Adding an Entity Framework Migration
------------------------------------------------------------------
Use .Net Core SDK installed: 3.1.302
API > dotnet tool install --global dotnet-ef --version 3.1.302
API> dotnet ef -h
API> dotnet ef migrations add InitialCreate -o Data/Migrations

Your startup project 'API' doesn't reference Microsoft.EntityFrameworkCore.Design. This package is required for the Entity Framework Core Tools to work. Ensure your startup project is correct, install the package, and try again.
-- Use nuget to install Microsoft.EntityFramework.Design

dotnet tool update --global dotnet-ef --version 3.1.0'. Update the tools for the latest features and bug fixes.
API> dotnet tool update --global dotnet-ef --version 3.1.6

--Value cannot be null. (Parameter 'connectionString')

14.- Updating the database
---------------------------
API> dotnet ef database -h
  drop
  update

API> dotnet ef database update
 it creates skinet.db (SQlLite).

Ctrl + P 
>SQLite: Open Database
it opens SQLite explorer on the IDE 

Right click Products. Select Generate Query (insert)
INSERT INTO `Products` (Id, Name)
VALUES (1, 'Product one), (2, 'Product 2'), '(3, 'Product 3);

Right Click. Select Run Query
Show table

15.- Reading the data form the Database in the API
-----------------------------------------------------
Scoped.- is available for the lifetime of the request
ActionResult<List<Product>> GetProducts()

17.- Creating the additional projects
-------------------------------------
skinet> dotnet new -h 
skinet> dotnet new classlib -o Core
skinet> dotnet new classlib -o Infrastructure
skinet> dotnet sln add Core
skinet> dotnet sln add Infrastructure
skinet>  cd API
API> dotnet add reference ../Infrastructure
API> cd..
skinet> cd Infrastructure
Infrastructure> dotnet add reference ../Core
Infrastructure>cd..
skinet> dotnet restore

Housekeeping
Menu-> File/Preferences/Settings/exclude/Files exclude/**/obj, **/bin

21 The Repository Pattern
-------------------------
23.- Adding a Repository and Interface
services.AddScoped<IProductRepository, ProductRepository>();
AddTransient - lifetime of the request i limites for each method in the controller (Too short)
AddSingleton.- Lifetime of the request las until the applicationis closed
AddScoped .- Lifetime of the reques finishes when the controller is closed

25.- Create new migration for the entities
skinet> dotnet ef database drop -p Infrastructure -s API
skinet> dotnet ef migrations remove -p Infrastructure -s API

skinet> dotnet ef migrations add InitialCreate -p Infrastructure -s API -o Data/Migrations
-p ==> Project
-s ==> Start Project
-o ==> Output folder

26.- Configuring the migrations
-------------------------------
FORMAT CODE: Shift + Alt + F.
+++++++++++++++++++++++++++++++













