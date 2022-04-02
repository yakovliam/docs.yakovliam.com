# Lang Config

These are messages that can be edited to make the feel of your server a bit different.
There is nothing special here; you just edit what you want or keep it as it is!

Example
-
Here's the default language configuration file
```yaml
general:
  help:
    - "&bSpaceChat &7&o(v2)&r &3help"
    - "&f- &d/spacechat reload"
    - "&f-   &3Reload plugin &7(chat formats, messages)"
    - "&f- &d/broadcast"
    - "&f-   &3Broadcast a message to the server"
    - "&f-   &7(Seamlessly works with redis)"
    - "&f- &d/broadcastminimessage"
    - "&f-   &3Broadcast a message &7(using minimessage) &3to the server"
    - "&f-   &7(Seamlessly works with redis)"
    - "&f- &d/channel join &7<channel>"
    - "&f-   &3Start talking in a specific channel"
    - "&f-   &7(Seamlessly works with redis)"
    - "&f- &d/channel leave"
    - "&f-   &3Stop talking in your current channel"
    - "&f-   &7(Seamlessly works with redis)"
    - "&f- &d/channel listen &7<channel>"
    - "&f-   &3Subscribe to messages from a specific channel"
    - "&f-   &7(Seamlessly works with redis)"
    - "&f- &d/channel mute &7<channel>"
    - "&f-   &3Unsubscribe to messages from a specific channel"
    - "&f-   &7(Seamlessly works with redis)"
channel:
  join:
    - "&aYou &ejoined &7%channel%"
  leave:
    - "&aYou &cleft &7%channel%"
  listen:
    - "&aYou &estarted listening to &7%channel%"
  mute:
    - "&aYou &cstopped listening to &7%channel%"
  invalid:
    - "&cOops! We can't find a channel with the name of &7%channel%&c."
  access-denied:
    - "&cOops! You aren't allowed to interact with that channel!"
ignore:
  player-not-found:
    text:
      - "&cCould not find specified player."
reload:
  success:
    - "&aSuccessfully reloaded &bChat"
  failure:
    - "$&cFailed to reload &bChat$"
broadcast:
  args:
    - "&cOops! &7You need to specify a message."
  wrapper:
    - "[&f&oBroadcast](hover: &cThis is a broadcast!) \u00BB &7%message%"
```

