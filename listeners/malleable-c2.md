# Malleable C2

The Malleable C2 Listener gives control to operators to customize their beacons to match specific threats. It does this through profiles, which are simple scripts that instruct the listener how to store, interpret, and extract data.

![Malleable profile for Amazon](../.gitbook/assets/image%20%282%29.png)

Malleable C2 is not a new concept, having been employed by Cobalt Strike for several years and is one of the most valuable features for the platform. Profiles allow users to change various settings within a beacon to truly customize its footprint. This post is not going to be a deep dive into Malleable Profiles, since Empire leverages the same profiles used in Cobalt Strike. If you are interested in learning more, we highly encourage checking out [Joe Vest’s post](https://posts.specterops.io/a-deep-dive-into-cobalt-strike-malleable-c2-6660e33b0e0b) or [Cobalt Strike’s Malleable C2 documentation](https://www.cobaltstrike.com/help-malleable-c2).

This project originated from [Johneiser’s Malleable C2 Parser](https://github.com/johneiser/MalleableC2Parser), which is a Python 2.7 implementation that parses the profile for the listener. Unfortunately, the project was no longer maintained and required a [refactor](https://github.com/BC-SECURITY/MalleableC2Parser) to work with Empire.

The parser takes the profile and executes the set of transforms that were scripted. The transformation order is extremely important, since both directions have to produce the same result. Currently, Empire can only ingest the Global Options and HTTP/S blocks. So a lot of the new functionality that was added in Cobalt Strike 4.0 will not be ingested. In the future, we hope to incorporate this additional functionality.

![Listener transform functionality from transformation.py](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2020/09/Screenshot_2020-09-06_21-14-54.png?resize=586%2C324&ssl=1)

Launching a Malleable C2 Listener can be simply done by using the Empire Command Line Interface \(CLI\) and typing:

```text
uselistener http_malleable
```

![Starting http\_malleable listener in Empire](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2020/09/Screenshot_2020-09-06_21-11-10.png?resize=1170%2C668&ssl=1)

The info page should look familiar since it uses similar settings as the standard HTTP listener, just with the addition **Profiles**. Profiles are loaded through your directory by using :

```text
set Profile apt1.profile
```

**Tip:** Double click tab and it will autocomplete whatever you are typing.

![Loading APT1.Profile as a Malleable Listener](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2020/09/Screenshot_2020-09-06_21-11-46.png?resize=1170%2C392&ssl=1)

Once you have your listener configured, you can run it and inspect it before launching your campaign. You can check out the serialized version of the profile by typing:

```text
listeners
info http_malleable
```

![Serialized Profile for APT1.Profile](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2020/09/Screenshot_2020-09-06_21-12-25.png?resize=1170%2C749&ssl=1)

Seems simple enough, right? But a peek behind the curtain will give some insight into how the agent is being constructed. For example, the serialized data is ingested to build the listener and configure the agent according to the profile. Now, this is not a perfect process, \(and we have managed to get the parser to nearly 100%\) we occasionally come across profiles that are not compatible. If you happen to be a Cobalt Strike user, the c2lint tool is invaluable for checking if profiles are correctly formatted.

One of the areas that still needs some improvement is when the listener tries to ingest serialized profiles. Occasionally Empire will successfully start the listener, but the agent will fail to properly stage when using a launcher. We are always trying to improve Empire functionality, so please [submit any issues](https://github.com/BC-SECURITY/Empire/issues) to our Github, since we heavily rely on users to help us identify areas for improvement.

We have also set up a [repository](https://github.com/BC-SECURITY/Malleable-C2-Profiles) for working profiles, which we will continue to update as new threat profiles are generated. This is also an opportunity for everyone to submit and share their profiles \(assuming they work with Empire\).

![Code excerpt from http\_malleable.py](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2020/09/Screenshot_2020-09-06_21-15-26.png?resize=944%2C523&ssl=1)

Similar to Cobalt Strike, Empire can only load a single profile per instance \(for now\). You can always spin up another instance of Empire if you want to run multiple Malleable Listeners at once. Otherwise, other listener types will still work while you have an active Malleable C2 Listener.

