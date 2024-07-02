# Connect a data source

To start building your application, you need to connect a data source to it. If you haven't previously connected a data source, you'll need to create a new one. However, since the data sources are reusable across your applications, you can also choose a previously connected data source, if there are any.

To connect a new data source, click and goto the **Data Sources** page from navigation menu

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Data source list</p></figcaption></figure>

Select your data source type. Enter a data source name to identify it within your app. Add data source configuration details: these can be a list of credentials, an API URL, a link to a Google Sheet, and more depending on a particular data source.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Configure connection</p></figcaption></figure>

When done, click **Test connection** to check whether the configuration is correct.

{% hint style="info" %}
Flowfy doesn’t store your data. We only keep the encrypted credentials to access a data source.
{% endhint %}

If you have previously connected a data source, it will already be available in the list of the data sources, so you can start using it right away.

Now you can use in visual designer.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For HTTP data source, “Test connection” doesn't really test the connection. It's used to check the URL correctness.
{% endhint %}

