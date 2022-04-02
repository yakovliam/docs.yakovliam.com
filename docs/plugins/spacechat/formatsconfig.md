# Formats Config

The formatting configuration is self-explanatory (by comments), so I will leave the default chat format configuration file below.

Example
-
Here's the default chat formatting configuration
```yaml
#############################################################################
#                    spacechat Formats Configuration (v2)                   #
#                                                                           #
# Written by yakovliam (https://yakovliam.com)                              #
#                                                                           #
# Refer to the spacechat official documentation for help:                   #
# https://docs.yakovliam.com/                                               #
# Refer to the MiniMessage documentation for help with formatting:          #
# https://bit.ly/MiniMessageDocs                                            #
# https://docs.adventure.kyori.net/minimessage.html#format                  #
#############################################################################

#=#=#=#=#=#=#=#=#=#=#=#=#
# Chat Formats          #
#=#=#=#=#=#=#=#=#=#=#=#=#

# list of all chat formats
chat:
  # the handle of the chat format (what it is called in the code & what it is referenced by)
  default:
    # if this is higher than other formats and the player has permission for multiple, this one will be shown
    priority: 1
    # The permission node for the player to use
    permission: "space.chat.cf.default"

    # the format itself; it contains parts that make up the chat format
    format:
      # these names are ambiguous. make them whatever you want and however many you want!
      prefix:
        # the text shown (Can't use MiniMessage parsing for this!)
        text: "&#34eb96Default &8| "

        # interaction events. right now you can do something on "click", or when someone "hovers"
        extra:
          # on click event
          click:
            # <- open a url; the options are: "open_url", "run_command", "suggest_command", "change_page", "open_file", etc - self explanatory
            action: "open_url"
            # this is the value used. if open_url, this is the open url....etc
            value: "https://tebex.io"

          # when someone hovers
          hover:
            lines:
              # these are the lines shown when someone hovers over the message
              - "&b&lClick to"
              - "&7purchase &oranks"

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

      # you don't have to include extra here at all; it can just be text
      separator:
        text: "&8&l\u00BB&r "

      chat-message:
        text: "<chat_message>"

  staff:
    priority: 100
    permission: "space.chat.cf.staff"
    format:
      prefix:
        text: "&cStaff &8| "
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

  # Donator (Mini-Message) (test) format
  donator:
    priority: 5
    permission: "space.chat.cf.donator"

    format:
      # Formats can also be one line only...format using MiniMessage (link for syntax above)
      # Make sure to specify "line" instead of "text" when it is ONE line ONLY
      the-entire-line:
        line: "<click:open_url:https://www.spigotmc.org/><hover:show_text:\"<yellow>Click to get donator!\"><red>Donator</red> <dark_gray>|</hover></click> <click:suggest_command:/msg %player_name%><hover:show_text:\"<aqua><bold>Click to\n</bold><gray>message <italic>%player_name%\"><gray>%player_displayname%</hover></click> <dark_gray><bold>\u00BB <reset><chat_message>"

#=#=#=#=#=#=#=#=#=#=#=#=#
```