# AbpModulePrefix
Edit Module Table Prefix/Scheme

Refer to:
https://github.com/abpframework/abp/issues/3121

When you user dotnet ef command, please add -s parameter.
dotnet ef migrations add rename_table -s ..\Acme.BookStore.Web\Acme.BookStore.Web.csproj
-s   --startup-project <PROJECT>  Relative path to the project folder of the startup project. Default value is the current folder.


cd Acme.BookStore.EntityFrameworkCore.DbMigrations

dotnet ef migrations add rename_table -s ..\Acme.BookStore.Web\Acme.BookStore.Web.csproj

