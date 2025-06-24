# ApiMonitor
ApiMonitor is a package that allows us to monitor the usage of our APIs Applications. Below is a description of each of the functionalities that it has available.
<!--TOC-->
  - [How to use it after installing the package](#How-to-use-it-after-installing-the-package)
  - [Getting Started with Client](#getting-started-with-client)
    - [Web Api Setting](#web-api-setting)
    - [Console App Setting](#console-app-setting)
<!--/TOC-->

## How to use it after installing the package

```C#
using ApiMonitorCore.Setting;

var builder = WebApplication.CreateBuilder(args);
builder.Services.AddControllers();
builder.Services.AddMonitor(builder.Configuration, new MonitorSetting()
{
    SqlSetting = new SqlSetting() { ConectionString = "Data Source=(localdb)\\MSSQLLocalDB;Initial Catalog=ApiMonitor;Integrated Security=True;Connect Timeout=30;Encrypt=False;Trust Server Certificate=False;Application Intent=ReadWrite;Multi Subnet Failover=False" },
    ApplicationName = "ApiName",
});
var app = builder.Build();
app.UseHttpsRedirection();
app.UseAuthorization();
app.UseMonitorUI(); //add Middleware
app.MapControllers();
app.Run();
```
With that configuration, it is enough to access the UI as shown in the picture. Just keep in mind that the database must be created first; all the tables will be created automatically.

![Flow diagram Echo](img/1.png)

