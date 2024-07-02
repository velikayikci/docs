# Server side development

## **Creating the Book entity**

Create the Book entity in **Flowfy.Domain** like below;

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

```csharp
using Flowfy.Entities;
using System;

namespace Flowfy.Book
{
    public class Book : EntityBase<Guid>
    {
        public string Name { get; set; }

        public decimal Price { get; set; }
    }
}
```

## **Creating the BookModel Dto**

Create the BookModel (BookDto) inside of **Flowfy.Application.Contracts**

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

```csharp
using Flowfy.Dtos;
using System;

namespace Flowfy.Book
{
    public class BookModel : ModelBase<Guid>
    {
        public string Name { get; set; }

        public decimal Price { get; set; }
    }
}
```

## **Creating the BookService**

Create the BookService/ Book API in **Flowfy.Application** like below;

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Volo.Abp.Domain.Repositories;

namespace Flowfy.Book
{
    public class BookService : FlowfyAppService
    {
        private readonly IRepository<Book, Guid> BookRepository;

        public BookService(
            IRepository<Book, Guid> bookRepository)
        {
            BookRepository = bookRepository;
        }

        public async Task<List<BookModel>> GetAllAsync()
        {
            var books = (await BookRepository.GetListAsync()).ToList();

            return ObjectMapper.Map<List<Book>, List<BookModel>>(books);
        }
    }
}
```

Auto map the **Book** entity and BookMode Dto in **FlowfyApplicationAutoMapperProfile.cs** file.

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

```csharp
CreateMap<Flowfy.Book.Book, BookModel>();
```

Add Books to FlowfyDbContext.cs under the **Flowfy.EntityFrameworkCore/EntityFrameworkCore** as below;

<figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

```csharp
public DbSet<Flowfy.Book.Book> Books { get; set; } 
```

Configure the **Books** table in FlowfyDbContext.cs under the **Flowfy.EntityFrameworkCore/EntityFrameworkCore** as below;

<figure><img src="../../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

<pre class="language-csharp"><code class="lang-csharp">builder.Entity&#x3C;Flowfy.Book.Book>(b =>
{
    b.ToTable(FlowfyConsts.DbTablePrefix + "Books", FlowfyConsts.DbSchema);
    b.ConfigureByConvention();
    b.Property(x => x.Name).HasMaxLength(128).IsRequired();
<strong>    b.Property(x => x.Price).IsRequired();
</strong>});
</code></pre>

## Migration

Right clict the **Flowfy.DbMigrator** and **Set as Startup Project** then open the Package Manager Console and select **Flowfy.EntityFrameworkCore** project as Default project then write "add-migration MyBookTable" to migration.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

Execute the generated migration

Run the Flowfy.DbMigrator console project to create Book table in database.

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

After running, refresh the database table, you will see Books table&#x20;

<div align="left">

<figure><img src="../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

</div>

Lastly, right click the **Flowfy.HttpApi.Host** and **Set as Startup Project** then **Start without Debugging**

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

Here is the your Book API.

Now we can call this api from client side.

<figure><img src="../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>
