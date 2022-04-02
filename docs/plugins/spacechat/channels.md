# Channels

The configuration for Channels is very easy to understand.

Example
-
Here's the default configuration contents.
```yaml
channels:
  staff:
    permission: "space.chat.channel.staff"
    format:
      prefix:
        text: "&c[Staff Channel] &8| "
      username:
        text: "&7%player_displayname% "
        extra:
          click:
            action: "suggest_command"
            value: "/msg %player_name%"
          hover:
            lines:
              - "&b&lClick to"
              - "&7message &o%player_name%"
      separator:
        text: "&8&l\u00BB&r "
      chat-message:
        text: "&e<chat_message>"
```