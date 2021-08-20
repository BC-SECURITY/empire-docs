# Staging

The key-exchange protocol used by Empire is called [Encrypted Key Exchange](https://en.wikipedia.org/wiki/Encrypted_key_exchange) \(EKE\). There’s a better overview [here](http://stackoverflow.com/questions/15779392/encrypted-key-exchange-understanding).

For Empire, a small launcher \(a basic proxy-aware IEX download cradle\) is used to download/execute the patched **./data/stager.ps1** script. The URI resource for this request can be specified in **./setup\_database.py** under the **STAGE0\_URI** paramater. The **stager.ps1** is case-randomized then XOR encrypted with the AES staging key from the database config. This means the key-negotiation stager delivered to each agent will be randomized/different per server, but will be static for each server instance. The staging key is sent with the launcher in order to decrypt the stager, so is assumed to be "burned" by network defenders.

This stager generates a randomized RSA private/public key pair in memory, uses the AES staging key to post the encrypted RSA public key to the **STAGE1\_URI** resource \(also specifiable in **./setup\_database.py**\). A random 12-character SESSIONID is also generated at this point, which is the initial name the agent uses to check in. After this post, the server returns the server’s epoch time and a randomized AES session key, encrypted in the agent’s public key.

The agent decrypts the values, gathers basic system information, and posts this information to the server encrypted with the new AES session key to **STAGE2\_URI**. The server then returns the patched **./data/agent.ps1**, which can be thought of as the standard API. From here, the agent starts its beaconing behavior.

\[\[[https://github.com/EmpireProject/Empire/wiki/Images/empire\_staging\_process.png\|align=center](https://github.com/EmpireProject/Empire/wiki/Images/empire_staging_process.png|align=center)\]\]

