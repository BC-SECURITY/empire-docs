# Credential Menu

Empire will attempt to parse standard Mimikatz outputs and keep them in an internal credential store. Credentials can be viewed from anywhere with the `credentials` command. The credential store can effectively operate as a golden and silver ticket catalog generating the appropriate ticket on demand, storing passwords, and hashes. Credentials can be added to the database by typing `add <domain> <username> <password>`.

![](https://user-images.githubusercontent.com/20302208/100279997-58c7a200-2f1c-11eb-9230-9becfb48bf9a.jpg)

Credentials can also be added manually. Use the `usecredentials add` command. There will be a blank field with the field that needs to be set. Set each field use `set`. Check that the fields are filled out with the `options` command. To save them into the credential menu save them with the `execute` command.

![](https://user-images.githubusercontent.com/82531659/157063795-5f9f74a4-b698-4815-806f-ba9990b41e11.png)

## ****
