---
description: >-
  Flowfy provides a flexible and intuitive interface for managing pages within
  an application. This document describes how to manage pages using the Flowfy
---

# Pages

### Overview

Pages in the Flowfy are the building blocks of an application's user interface. Pages can be created and customized to meet the needs of the application's users. Page management in Flowfy allows users to create, edit, delete, and organize pages to create a cohesive and effective application.

### Page management

#### List pages

Goto **Pages** page from the navigation menu to manage your pages.

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption><p>List Pages</p></figcaption></figure>

### Creating Page

If you have permission to create page you will see **New Page** action under the **New** menu.

:In Flowfy, **all actions** are permission based. If you don't see **New Page** action, request permission from your administrator to see or goto [**Permissions**](https://app.flowfy.net/app/permission) page and define permission for yourself. Goto [**Permissions**](https://app.flowfy.net/app/permission) documentation for more information.

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

To create a new page, follow these steps:

1. Open the application in which you want to create a new page.
2. Navigate to the "Pages" section in the platform's menu.
3. Click the "New Page" button.
4. Choose the type of page you want to create (e.g., form, grid, report).
5. Customize the page by adding components, defining data sources, and configuring properties.

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

* **Parent Menu** determine where the page will be positioned.
* **Page Name** determine the page name. Page name is multi language, if click the right icon in the input, other languages will shows.
*   **Code** determine the page unique code. If you want to show a page from code behind, you will use this code.

    ```js
    pageManager.showDialog('UniquePageCode', {
        width: 580, height: 550,
        pageParams: selectedItem.id
    });
    ```
* **Path** determine the page url address.&#x20;
* **Icon** determine the page icon.
* **Show In Navigation Menu** If true, page will shown in the left navigation menu.
* **Active** determine the page active or not.

#### Editing Pages

To edit an existing page, follow these steps:

1. Open the application that contains the page you want to edit.
2. Navigate to the "Pages" section in the platform's menu.
3. Click on the page you want to edit.
4. Make the necessary changes to the page by adding or removing components, modifying data sources, or updating properties.

#### Deleting Pages

To delete a page, follow these steps:

1. Open the application that contains the page you want to delete.
2. Navigate to the "Pages" section in the platform's menu.
3. Click on the page you want to delete.
4. Click the "Delete" button.
5. Confirm the deletion.



### Creating menu

If you have permission to create menu you will see **New Menu** action under the **New** menu.

After click the **New Menu** action, **Menu Entry** page will appear.

<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption><p>Menu Entry</p></figcaption></figure>

* **Parent Menu** determine where the page will be positioned.
* **Menu Name** determine the menu name. Menu name is multi language, if click the right icon in the input, other languages will shows.
* **Icon** determine the menu icon.
* **Show In Navigation Menu** If true, menu will shown in the left navigation menu.
* **Active** determine the menu active or not.
