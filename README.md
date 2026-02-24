git clone
visual studio 2022  or version they are using
sql  version specific


Master  ===> Production
Develop ==> Stagging 
Test  ===> Testing  (QC testing)
Register-user  ==> Development  (Developer working)


development developer 1(create a branch and give name like task name) task1
development developer 2(create a branch and give name like task name) task2

developer 1  take latest from develop branch  and merge into Test 


https://localhost:7031/controllername
header : name =GetWeatherForecast

API ROUTES of controller need to check to hit from postman


| Shortcut             | Purpose                                                                   |
| -------------------- | ------------------------------------------------------------------------- |
| `Ctrl + .`           | Quick Fix / Suggestions (add using, generate method, implement interface) |
| `Ctrl + Space`       | Trigger IntelliSense manually                                             |
| `Ctrl + K, Ctrl + C` | Comment selected code                                                     |
| `Ctrl + K, Ctrl + U` | Uncomment selected code                                                   |
| `Ctrl + D`           | Duplicate line                                                            |
| `Alt + ↑ / ↓`        | Move line up or down                                                      |
| `Ctrl + Shift + L`   | Select all occurrences of selected word                                   |
| `Ctrl + F`           | Find                                                                      |
| `Ctrl + H`           | Replace                                                                   |
| `Ctrl + Shift + F`   | Find in entire solution                                                   |
| `Ctrl + Shift + H`   | Replace in entire solution                                                |
| `Ctrl + G`           | Go to Line Number                                                         |
| Shortcut     | Purpose              |
| ------------ | -------------------- |
| `F12`        | Go to Definition     |
| `Ctrl + F12` | Go to Implementation |
| `Ctrl + -`   | Navigate Back        |
| Shortcut     | Purpose               |
| ------------ | --------------------- |
| `F5`         | Start Debugging       |
| `Ctrl + F5`  | Run Without Debugging |
| `Shift + F5` | Stop Debugging        |
| `F9`         | Toggle Breakpoint     |
| `F10`        | Step Over             |
| `F11`        | Step Into             |
| Shortcut             | Purpose                                                         |
| -------------------- | --------------------------------------------------------------- |
| `Ctrl + R, Ctrl + R` | Rename variable/class safely (updates references automatically) |

class library   :  not ui, not configuration, 

assembly?

common project (common folder)
Email Service :  (which is sending email [Templates] ,from email)
Templates means HTML page.
class library ==> 
interface
class email (from, to, content,cc,bcc)


class library  == lighweight, easy to use, use multiplaces

Clean architecture:
Domain =  business logic
Infrastructure,  ==  interface,service [implement interface (business logic)]
API  =>controller, simple logic
controller => Iservice  ==>Service  => IRepo  ==> Repo =>Method

web api ==> [controller => Iservice  ==>Service  => IRepo  ==> Repo =>Method]


Web API
 Create Web api project.
 add packages[core,core.tools,core.sqlserver].
 Create folder (model, controller, Create a class dbcontext)
 inside dbcontext we will have only models which represent table.
 Create a model first and use inside dbcontext.
 Repository folder 
 Service folder
 inside a repository folder and create Interface (name  based on model or requirement)  IemployeeRepositry
 insde a repository folder and create class same name as interface   employeeRepostiry
 create methods inside the Iemployee  (interface)  
 implement all that methods of Iemployee interace inside  emloyeeClass  [Businee logic]
 inside a service folder we wil create  interface and class.
 IemployeeService,EmployeeService.
 Controller folder. created get, post,put ,delete.   we will use service.
 
 employee repository.
 50 methods Iemployee interface.
 employee class have 50 method implemented.
 
 two controller.
 deparment controller.  [10 methods]  ==>  10  methods  from repository
 salary controller.  [40 methods]  ==>40  methods  from repository.
   
 Add   == > input is employeeModel  => output id bool(success/fail) Create
 Update   ===> input is employeeModel  => output id bool(success/fail) Update
 Delete  ==>  input as a employeeid => Delete
 GetList  =>  nothig => output as a list a employee. Read
 
class libarary  is core project. small project which gives dll and then can use in another project. 

using multiple class libararies and one web api  we can create enterpise level project.
 if we use single web api:
 Hard to manage.
 take much time to load project. [timeout]
 more conflict.
 hard to indetify.
 
 
 
 
 mapper   ==>
 employee  : EmplyeeId,EmployeeName,DepartmentId,Address,Salary
 class2 = EmplyeeId,EmployeeName,DepartmentId,Address,Salary
 class1 = EmplyeeId,EmployeeName,DepartmentName,Address,Salary
 Create another class   ==>output will class1 = Mapper.map<class1>(class2).ignore(column);
 class1   = call another service  class1.deparmentName=  getdepartmentNamebyId(class2.deparmentId);
 API return class1 model.
 
 
Company working on taxation.
Common class library. 

If youn want to use any interace  in DI  then you need to register interface with class.
inside progam.cs file
builder.Services.AddTransient<IEmployeeRepository, EmployeeRepository>();

three approach : Code first,DB first and model first.

Database First Approach (Web API)

Create project
Add required EF Core packages (SqlServer, Tools, Design)
Create folders: Models, Services, Repositories
Add ConnectionStrings in appsettings.json
Run Scaffold-DbContext "ConnectionString" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -Context ApplicationDbContext
Add DbContext in Program.cs using builder.Services.AddDbContext
Create interface and repository class in Repositories folder
Create interface and service class in Services folder
Register repository and service in Program.cs using AddScoped

Code First Approach (Web API)
Add required EF Core packages (SqlServer, Tools, Design)
Create folders: Models, Data, Services, Repositories
Add ConnectionStrings in appsettings.json
Create model class with properties based on table structure
Create DbContext class in Data folder with DbSet with model builder method
Add DbContext in Program.cs using builder.Services.AddDbContext
Run Add-Migration InitialMigration
Run update-database
Create interface and repository class in Repositories folder
Create interface and service class in Services folder
Register repository and service in Program.cs using AddScoped
