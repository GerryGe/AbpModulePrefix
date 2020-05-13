# AbpModulePrefix
Edit Module Table Prefix/Scheme

Refer to:
https://github.com/abpframework/abp/issues/3121

When you user dotnet ef command, please add -s parameter.
dotnet ef migrations add rename_table -s ..\Acme.BookStore.Web\Acme.BookStore.Web.csproj
-s   --startup-project <PROJECT>  Relative path to the project folder of the startup project. Default value is the current folder.


cd Acme.BookStore.EntityFrameworkCore.DbMigrations

dotnet ef migrations add rename_table -s ..\Acme.BookStore.Web\Acme.BookStore.Web.csproj



Volo.Abp.AuditLogging.AbpAuditLoggingDbProperties.DbTablePrefix = "Dy";
Volo.Abp.BackgroundJobs.BackgroundJobsDbProperties.DbTablePrefix = "Dy";

Volo.Abp.FeatureManagement.FeatureManagementDbProperties.DbTablePrefix = "Dy";
Volo.Abp.IdentityServer.AbpIdentityServerDbProperties.DbTablePrefix = "Dy";
Volo.Abp.Identity.AbpIdentityDbProperties.DbTablePrefix = "Dy";
Volo.Abp.PermissionManagement.AbpPermissionManagementDbProperties.DbTablePrefix = "Dy";
Volo.Abp.SettingManagement.AbpSettingManagementDbProperties.DbTablePrefix = "Dy";

Volo.Abp.TenantManagement.AbpTenantManagementDbProperties.DbTablePrefix = "Dy";

//BloggingDbProperties.DbTablePrefix = "Dy";
//DocsDbProperties.DbTablePrefix = "Dy";
