# poopmail-structure

## FAQ

### What the f**k is poopmail?

Well, poopmail is an attempt to create a simple yet sexy trash-temp-email service which is completely open source.
However, we don't wanna annoy everybody by showing stupid ads so we decided to limit access to cool people only, so the service is invite-only.
Maybe that will change, maybe not, let's see if we even get this shit to work.

### How do I get invited?

Yes.

### You didn't answer my question you stoopid moron!

Don't be rude!

### Why the name?

Because it's cool. Isn't it?

### Yes. NOW SHOW ME THE STRUCTURE!!!

Chill dude.

## Structure

Even if this is a simple project, just like everybody else, we love failing at overengineering.
This is why we decided to create 4 completely useless and overkill services for poopmail. Stay tuned!

* **toilet** is where all incoming mails flow into. Because trash-mails are used for, you might've guessed it, yes, poop, we liked this name. Well, **toilet** just receives ~~emails~~ poop, checks if they are addressed to one of our domains and then simply redirects the email in a simpler form (target, subject, sender and content) into a **Redis PubSub channel**.
* **canalization** then receives these mails, searches for an open mailbox mapped to the email target and saves the email into the database if one was found. If not, the email is simply disposed.
Additionally it supports WebSocket connections to distribute incoming emails to connected frontend clients if needed.
**canalization** also keeps track of user accounts and their attached mailboxes and exposes simple REST endpoints to manage them.
* **sewage-plant** is our sexy hexy sleeky weeky web frontend. It simply looks nice and gives you a nice interface to interact with your poopmail-related stuff.
* **karen** receives any incidents that appear in any of the other services and notifies us through multiple channels about these. **karen** is triggered by **Redis PubSub** messages.

**Note:** This message wasn't approved by cerus.