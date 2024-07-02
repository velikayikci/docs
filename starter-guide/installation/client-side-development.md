# Client side development

Within this documentation, we will first create a book listing page where we will list the books. Then, we will create a Book definition page where we can create and edit books. As part of the CRUD operations, we will write the Book API on the ASP.NET Core side.

## Creating the _Books_ Page

Create **book** folder under the **Flowfy.Web/src/pages**, and then create **books.tsx** page inside of **book** folder.

In **book.tsx** file we have such as code as below.

{% hint style="info" %}
**Flowfy.Web** is a node.js project, the others one are ASP.Net core projects.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

```typescript
import { FC, useState } from 'react';
import useProxy from 'src/hooks/useProxy';
import DataGrid from 'src/components/DataDisplay/DataGrid';
import TransactionPage, {
    TransactionPageProps
} from 'src/components/Layout/TransactionPage';

const Books: FC<TransactionPageProps> = (props) => {
    const proxy = useProxy();
    const [books, setBooks] = useState<any[]>([]);

    const fetchBooksCommand = async () => {
        const response = await proxy.get<any[]>('/api/app/book/', {
            showListedDataCountMessage: true
        });
        if (response.success) {
            setBooks(response.value);
        }
    }

    return (
        <TransactionPage
            commands={{ fetchBooksCommand }}
        >
            <DataGrid
                dataSource={books}
            />
        </TransactionPage>
    );
};

export default Books;
```

Import the **book.tsx** page in **pages/index**

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

## **Defining Books page**

In this part we will define Books page and then we will define actions of Books page.

Open the **Pages** page in Flowfy app to define the Books page

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

**Parent menu**: Determines where the page will be positioned in navigation menu.

**Page Name\*:** It is the page title that will be visible in the menu and everywhere.

**Code\*:** It is the name of the lazy import as below, also you will use this code to show a page.

<div align="left">

<figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

</div>

Example code;

```typescript
pageManager.showDialog('YourPageCode', {
  width: 1150, height: 720
});
```

**Path\***: Physical path of the file but just replaced '**src/pages'** with '**/app'** as below.

**Show In Navigation Menu**: Determine whether the page is visible or not in the navigation menu.

**Active**: Determines whether the page is active or inactive. If it is set to false, it will not be visible in the menu and will be disabled for use.

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

After click save action, our page added. Then manage the page Actions.

## Defining Books Page Actions

{% hint style="info" %}
**In Flowfy, Pages and page's actions are definition based, and permissions depends on page's actions.**

For example: If the user does not have permission for the Save action, they will not be able to see the Save button in the toolbar.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

**Action Type**: There are 2 types of actions

* Default: For the default actions on toolbar.
* Virtual: Only for the permissions. For example; If you want to show the father's name field only to developers, in this case, you need to use virtual permission.

**Name\***: Name of the action on toolbar.

**Command Name\***: Command Name: The name of the method that will be executed when the action is clicked on the code side.

<figure><img src="../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

If you want to disable or hide a action add prefix **CanExecute** or **CanVisible** to the command name.

```typescript
// this method is always running, 
// so don't use proxy calls inside of method
const CanExecutefetchBooksCommand = () => {
    return true;
}
// hide or visible the action.
const CanVisiblefetchBooksCommand = () => {
    return true;
}

return (
    <TransactionPage
        commands={{ fetchBooksCommand, 
        CanExecutefetchBooksCommand, 
        CanVisiblefetchBooksCommand  }}
    > 
    ....
```

Now, refresh the app and you will see the your Books page.

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
We added some temp data to the Books table.
{% endhint %}
