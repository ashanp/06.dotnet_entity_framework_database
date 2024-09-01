Step1.  Create a new .NET Core Web API project:
dotnet new webapi

Step2. Add Entity Framework Core and MySQL Packages
In the terminal do the following
dotnet add package Microsoft.EntityFrameworkCore --version 7.0.20
dotnet add package Pomelo.EntityFrameworkCore.MySql --version 7.0.20

Step3. Configure Your Database Context
create AppDbContext.cs and Product.cs in the Models folder

AppDbContext.cs
using Microsoft.EntityFrameworkCore;
public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options)
        : base(options)
    {
    }
    public DbSet<Product> Products { get; set; }
}

Product.cs
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}

Step 4: Configure MySQL in appsettings.json
"ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=mydatabase;User=root;Password=yourpassword;"
  },

Step 5: Update Program.cs
Please refer to the Program.cs file

Step 6: Create and Apply Migration
In the terminal do the following
dotnet ef migrations add InitialCreate
dotnet ef database update

if you dont have dotnet ef installed then install them using below commands
dotnet tool install --global dotnet-ef --version 7.0.0
verify the installation by below command
dotnet tool list -g
after install again try above 2 commands. 

Step 7: creat a controller file in controlder folder as ProductsController.cs
Please refer to the ProductsController.cs file

start the application and test it.

Ohh, dont forget to create below tables and insert sample data to the table.

create table Products (Id int, Name varchar(200), Price decimal);
insert into Products values (1, 'macbook pro', 3000.00);
insert into Products values (2, 'macbook air', 1000.00);

good luck :) 
