# OneDrive

This listener is really useful because it runs in Microsoft’s infrastructure, which makes it very difficult to block for organizations that are utilizing Office 365 and other Microsoft products. The documentation for this comes from [BC Security OneDrive Blog Post](https://www.bc-security.org/post/using-the-onedrive-listener-in-empire-3-1-3/).

To run the OneDrive listener, type

```text
uselistener onedrive
```

![](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2020/05/2.png?resize=931%2C740&ssl=1)

## Azure Setup

The OneDrive listener does require a Microsoft Azure account to setup the application permissions. So you will either need to have one or set one up. Once your account is setup, login into [https://portal.azure.com/\#blade/Microsoft\_AAD\_RegisteredApps/ApplicationsListBlade](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) to access the App registrations page. Next, select New Registration.

![](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2020/05/3.png?fit=1170%2C162&ssl=1)

Add your application name. It doesn’t matter what it is, so just type something in. You will want to enter the redirect URI as:

```text
https://login.live.com/oauth20_desktop.srf
```

![](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2020/05/4.png?fit=1170%2C592&ssl=1)

Once your application has been registered, you will be taken to the application overview page. Copy your ClientID over to Empire.

![](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2020/05/5.png?fit=1170%2C519&ssl=1)

The Client Secret is the next field required by Empire. However, it is not automatically generated but can be easily created by navigating to the Certificates & Secrets tab. Once on this page, select New Client Secret to generate the new value.

![](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2020/05/6.png?fit=1170%2C589&ssl=1)

## Empire Configuration

Copy this value and enter it into Empire as the ClientSecret. At this point, the listener is nearly complete. However, we will need to copy the authentication code from the OAuth App. To obtain the AuthCode you will be required to login into your app from your Azure account. If you type in execute in Empire, you will be provided a web address that you can copy to navigate to the page to obtain your AuthCode.

![](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2020/05/7.png?resize=1098%2C790&ssl=1)

Your browser will automatically redirect you to the page with the AuthCode. The AuthCode is contained in the URL and you will need to copy it over to Empire. Do not include the “&lc=1033” at the end of the URL as part of the AuthCode.

![](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2020/05/8.png?resize=859%2C95&ssl=1)

The last step for configuring the listener is to enter the AuthCode, as seen below, then execute.

![](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2020/05/9.png?resize=581%2C154&ssl=1)

Empire will automatically configure a folder on your OneDrive that will contain the results, staging, and taskings. You will not need to make any changes to these files.

![](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2020/05/10.png?resize=683%2C191&ssl=1)

Once you have started the listener, you can create stagers just like with any other stager by typing:

```text
set Listener onedrive
```

![](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2020/05/11.png?resize=541%2C209&ssl=1)

Test your launcher and if you configured everything properly, you will successfully receive a callback using your OneDrive listener. The staging process is a bit slower than a typical listener due to the listener going through OneDrive, however, just give it a minute and it should populate.

![](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2020/05/12-1.png?resize=1027%2C505&ssl=1)

