# AbpModulePrefix
Edit Module Table Prefix/Scheme

Refer to:
https://github.com/abpframework/abp/issues/3121

When you user dotnet ef command, please add -s parameter.
dotnet ef migrations add rename_table -s ..\Acme.BookStore.Web\Acme.BookStore.Web.csproj
-s   --startup-project <PROJECT>  Relative path to the project folder of the startup project. Default value is the current folder.


cd Acme.BookStore.EntityFrameworkCore.DbMigrations

dotnet ef migrations add rename_table -s ..\Acme.BookStore.Web\Acme.BookStore.Web.csproj


You can add this code to Program.cs for all db-using applications (migrator, web... etc.).
Note: please also add this code to this files for PMC ef command like add-migration/update-database
..\Acme.BookStore.EntityFrameworkCore.DbMigrations\EntityFrameworkCore\BookStoreMigrationsDbContextFactory.cs
For example:

    BookStoreMigrationsDbContextFactory.cs file:  
    public BookStoreMigrationsDbContext CreateDbContext(string[] args)
    {
        //Setting your table prefix here also
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

        var configuration = BuildConfiguration();

        var builder = new DbContextOptionsBuilder<BookStoreMigrationsDbContext>()
            .UseSqlServer(configuration.GetConnectionString("Default"));

        return new BookStoreMigrationsDbContext(builder.Options);
    }
    


    ..\Dychar.Dyframe.DbMigrator\Program.cs
    
    static async Task Main(string[] args)
        {
             //Setting your table prefix here also
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
            
            Log.Logger = new LoggerConfiguration()
                .MinimumLevel.Information()
                .MinimumLevel.Override("Microsoft", LogEventLevel.Warning)
                .MinimumLevel.Override("Volo.Abp", LogEventLevel.Warning)
                .MinimumLevel.Override("Acme.BookStore", LogEventLevel.Debug)
                .Enrich.FromLogContext()
                .WriteTo.File(Path.Combine(Directory.GetCurrentDirectory(), "Logs/logs.txt"))
                .WriteTo.Console()
                .CreateLogger();

            await CreateHostBuilder(args).RunConsoleAsync();
        }
 
