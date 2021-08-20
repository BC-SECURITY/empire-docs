# Dropbox

We can leverage the Dropbox API as a C2 channel, which can utilize existing architecture inside a network and obfuscate web traffic. The documentation for this comes from [BC Security Dropbox Blog Post](https://www.bc-security.org/post/empire-dropbox-c2-listener/).

## Empire Setup

The Dropbox listener requires two distinct steps, setting up the listener in Empire and then configuring an application to use the Dropbox API. This is slightly more complicated than a basic HTTP listener but will be broken down step-by-step below. The first step is to launch the listener inside of Empire by typing:

```text
uselistener dbx
```

![Uselistener dbx in Empire client](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2021/04/listener_selection.png?resize=1083%2C1050&ssl=1)

Entering the listener menu will provide info \(if any is documented\) about the listener and options for configuration. If you notice, the only option displayed for the Dropbox listener that is required and not configured is the _APIToken_ which will require setting up a Dropbox developer account.

![Dropbox listener options](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2021/04/options.png?resize=972%2C1052&ssl=1)

## Dropbox Account Creation

You will have to navigate to the [Dropbox developer page](https://www.dropbox.com/developers/) and setup an account to access this feature. We recommend that you setup a new account for using an Empire listener since Dropbox may disable your account, and you would lose access to your data. Luckily, they offer a 2 GB basic plan which is FREE.

**Warning: Use at your own risk, we take no responsibility if your Dropbox account becomes disabled.**

![ Dropbox developer page](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2021/04/sign_in.png?resize=305%2C516&ssl=1)

Sign in to Dropbox developer page: [https://www.dropbox.com/developers](https://www.dropbox.com/developers)

## Dropbox Configuration

Once you have an account setup, you will be able to access the developer options, and you will need to click on the App Console tab at the top of the screen.

![Select App Console on the top bar once logged in](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2021/04/app_console.png?resize=1170%2C62&ssl=1)

From the App Console, you will be given the option to create a new application, click on _Create app._

![Create new application for Dropbox](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/create_app-1.png?resize=1170%2C139&ssl=1)

Dropbox migrated their API from v1 to v2 a few years ago, so this may look unfamiliar if you haven’t accessed this page \(relatively\) recently. You now have to select a scoped access application and then give it access to all files and folders in a user’s Dropbox. More permissions will be required, so this gives us an easy starting place. Then name the application with something that won’t give itself away instantly \(e.g., totally\_not\_empire\).

![Generate Full Dropbox application with a semi-unique name](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/app_config.png?resize=1170%2C795&ssl=1)

Now you will create the application and will be presented with configuration options. The first thing we will do is update the permissions so that a user can make modifications to files and folders.

![Select permissions tab to access user privileges](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2021/04/permissions-1.png?resize=809%2C140&ssl=1)

Specifically, you will be granting access to the following options. Just a note, you need to change all of these permissions before generating an access token.

* Files.metadata.write – View and edit information about your Dropbox files and folders
* Files.metadata.read – View information about your Dropbox files and folders
* Files.content.write – Edit content of your Dropbox files and folders
* Files.content.read – View content of your Dropbox files and folders

![Update user permissions to have full-access to files and folders](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/update_permissions.png?resize=1112%2C317&ssl=1)

Next, you will need to return to the settings page and enable additional users. This will ensure that the Empire server can communicate to Dropbox and that your agents can also communicate through Dropbox to your Empire server.

![Enable additional users for the application](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/enable_additional_users.png?resize=1170%2C626&ssl=1)

Now you can generate your access token \(APIToken\). Be sure to select no expiration for your access token. Otherwise, it will expire after 4 hours, and you will need to reconfigure your listener and agents with a new token.

![](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2021/04/access_token-1.png?resize=1030%2C121&ssl=1)

![Generate OAuth2 access token with no expiration dateAccess Token Example](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/oauth2.png?resize=1037%2C447&ssl=1)

## Empire Dropbox C2

Now that we have gone through configuring Dropbox, you can set your APIToken for the Dropbox listener. This can be done by typing:

```text
set APIToken 
```

![Set APIToken on dbx listener and execute](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/set_api_token.png?resize=440%2C97&ssl=1)

Assuming everything went according to plan, you will see a notification that the Dropbox listener successfully started. We recommend generating a new token if you receive an error since the permissions sometimes don’t update properly for the Dropbox access token. Once you have an active listener, you can next generate a launcher to try out the C2 channel. For this example, we will be using the multi/launcher, which can be accessed by:

```text
usestager multi/launcher
Set Listener dbx
```

![Select usestager multi/launcher](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2021/04/usestager_dbx_p2.png?resize=754%2C614&ssl=1)

![Set Listener to dropbox](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2021/04/usestager_dbx.png?resize=755%2C488&ssl=1)

Technically you only need to set the listener to generate this launcher. However, the default Empire payload has been extensively signatured and will be instantly caught by most Antiviruses. You will have to do some custom obfuscation to get the payload through, but for testing purposes, it is easiest to disable real-time protection and run the payload directly in your PowerShell terminal. If you are interested in learning more about obfuscation, you can check out our recent webinar that explores basic .NET and PowerShell obfuscation techniques: [Evading Detection: A Beginner’s Guide to Obfuscation.](https://www.youtube.com/watch?v=lP2KF7_Kwxk) 

![Multi/launcher one-liner PowerShell launcher](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/multi_launcher.png?resize=1170%2C426&ssl=1)

## C2 Architecture

Once you deploy your launcher, you will receive a few notifications and warnings. These aren’t anything to worry about and are purely informational.

![Empire server messages for staging a Dropbox payload](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2021/04/server_messages.png?resize=728%2C188&ssl=1)

Empire updates the Dropbox directories to be used as a C2 during the agent’s initial staging. This is done by creating a series of folders and text documents that will be used to transfer information. For example, the staging folder will be used for sending Stage 2 of the agent, the taskings folder is used for sending tasks \(e.g., Mimikatz, Seatbelt, etc.\) to the agent, and results returns the information from the ran tasks.

![Dropbox folder used for C2 channel](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2021/04/dropbox_folders.png?resize=997%2C565&ssl=1)

## Empire Agent

Finally, after all the architecture stuff, you can interact with your agent and try out your new infrastructure. Keep in mind that the default beacon time is 60 seconds, so responses may feel slow compared to the default HTTP listener. You can update this when you setup your listener, however, if the purpose of this is to look like Dropbox traffic then you should keep the default beaconing.

![Dropbox agent callback](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2021/04/agents_menu.png?resize=1170%2C117&ssl=1)

![Agent interaction using new 4.0 interface](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2021/04/agent_interaction.png?resize=687%2C366&ssl=1)

Just to make sure this is covered again, you are using this at your own risk, and we do not take responsibility if your Dropbox account becomes disabled. In addition, this tool is purely for testing and educational purposes only with the system owner’s permission and should not be used maliciously. With that said, enjoy adding the Dropbox listener as part of your red team infrastructure.

