# Installation

### Pre Requirements

* [Visual Studio 2017](https://www.visualstudio.com) (for backend ASP.NET Core applications)
* [.NET Core 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
* [Node.js 20+ with NPM 6+](https://nodejs.org/en/download/)
* [Yarn v1.x](https://classic.yarnpkg.com/lang/en/)

### **1.Install nuget packages**

Right click the **Flowfy.HttpApi.Host** project and select "**Set as StartUp project**". Then **build** the solution. It may take a longer time during the first build since all **nuget** packages will be restored.

<figure><img src="../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Make sure .NET 8.0 installed and appear in visual studio target framework like below
{% endhint %}

<figure><img src="../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

### **2.Install npm packages**

Navigate to the **`Flowfy.Web`** folder and open the terminal, run the following command:

```
yarn install    
```

{% hint style="info" %}
**Flowfy.Web** is a node.js project, the others one are ASP.Net core projects.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

### **3.Database migration**

Flowfy solution includes **`Flowfy.DbMigrator`** project, run this console project for database migrations. This project will create your database and tables.

Check the connection strings in the **appsettings.json** file under the **`Flowfy.HttpApi.Host`** and **`Flowfy.DbMigrator`** projects.

```json
"ConnectionStrings": {
  "Default": "Server=(LocalDb)\\MSSQLLocalDB;Database=FlowfyDB;Trusted_Connection=True"
}
```

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

This project will create your database. Initial data will be inserted when you run the **`Flowfy.DbMigrator`** project. You can open SQL Server Management Studio to check if database is created:

![](<../../.gitbook/assets/image (87).png>)



### **4.Run API Host (Server side)**

First Navigate to the **Flowfy.HttpApi.Host** folder and open the terminal, run the following command:

`npm install`

after instaling node modules right click the **Flowfy.HttpApi.Host** project and Start Without Debugging

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

After successfully database connection Swagger UI will appear on [https://localhost:44316](https://localhost:44316/swagger/index.html)/ as below

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

### **5.Run The Application (Client side)**

Navigate to the`Flowfy.Web` project and open the terminal then run the following command:

```
npm run dev
```

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

Open the browser goto [http://localhost:44321/](http://localhost:44321/) login page will appear as below;

First create new account to login.

{% hint style="info" %}
Set tenant name '**Flowfy**' for superadmin and SaaS management(SaaS menu will apear)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

## **Summary**

Open the **Flowfy.sln** project in Visual Studio, build the solution, run the **`Flowfy.Migration`** after database configuration, and run the server side **`Flowfy.HttpApi.Host`** in debug mode, go to **`Flowfy.Web`** project, install the npm packages with `yarn install`, after successful npm installation, then run the project with `npm run dev`
