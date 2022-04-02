# Config & Permissions

The configuration for SpaceChat is very easy to understand.

Location
-
The main configuration's location is in the plugins folder under the subdirectory named 'SpaceChat' (`/plugins/SpaceChat/config.yml`)

Storage
-
If you would like to explore how you can edit storage features, please visit the [Storage Page](plugins/spacechat/storage.md).

Logging
-
There is currently one available type of logging that you can enable-disable.

### log-to-storage
If enabled (set to `true`), the plugin will record every chat message sent to the specified storage medium (YAML or MySQL). If you wish to read about changing storage features, please visit the [Storage Page](plugins/spacechat/storage.md).

Permissions
-

| Configuration Location             | Default Permission                      | Description                                                                 |
| ---------------------------------- | --------------------------------------- | --------------------------------------------------------------------------- |
| `permissions.use-chat-colors`      | space.chat.chatcolor                    | Allow players to color their message in chat with `&`                       |
| `permissions.use-item-chat`        | space.chat.item-chat                    | Allow players to use item chat                                              |
| `permissions.use-chat-links`      | space.chat.chatlinks                    | Allow players to use links in chat                                          |

Redis
-

Redis is an advanced tool that can be used to synchronize multiple servers using SpaceChat. If set up correctly, you can have multiple servers
with the exact same chat (e.g. Multiple Skyblock sub-servers). Set your `server-identifier` to the professional handle of your server. The `server-displayname`
is the more often displayed text, so that can have spaces and colors. You can access these variables in your chat formats using the placeholders 
found below. The `url` is a customizable connection URL, and the `chat-channel` should be set to the same thing (pub/sub channel) for each
server that wants to be synced.

Example
-
Here's the default configuration contents.
```yaml
####################################
# spacechat Configuration          #
# v2                               #
# Written by yakovliam             #
# Visit https://www.yakovliam.com  #
####################################

#=#=#=#=#=#=#=#=#=#=#=#=#=#=#=#
# Storage Configuration       #
#                             #
# Storage types:              #
# -> mysql - RECOMMENDED      #
# -> json - NOT RECOMMENDED   #
#=#=#=#=#=#=#=#=#=#=#=#=#=#=#=#
storage:
  use: "json" # which storage type should we use?
  # MySQL configuration settings
  mysql:
    # Define the address and port for the database.
    # - The standard DB engine port is used by default
    #   (MySQL: 3306, PostgreSQL: 5432, MongoDB: 27017)
    # - Specify as "host:port" if differs
    address: localhost

    # The name of the database to store spacechat data in.
    # - This must be created already. Don't worry about this setting if you're using MongoDB.
    database: minecraft

    # Credentials for the database.
    username: root
    password: ''
    pool-settings:
      # Sets the maximum size of the MySQL connection pool.
      # - Basically this value will determine the maximum number of actual
      #   connections to the database backend.
      # - More information about determining the size of connection pools can be found here:
      #   https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing
      maximum-pool-size: 10

      # Sets the minimum number of idle connections that the pool will try to maintain.
      # - For maximum performance and responsiveness to spike demands, it is recommended to not set
      #   this value and instead allow the pool to act as a fixed size connection pool.
      #   (set this value to the same as 'maximum-pool-size')
      minimum-idle: 10

      # This setting controls the maximum lifetime of a connection in the pool in milliseconds.
      # - The value should be at least 30 seconds less than any database or infrastructure imposed
      #   connection time limit.
      maximum-lifetime: 1800000 # 30 minutes

      # This setting controls how frequently the pool will 'ping' a connection in order to prevent it
      # from being timed out by the database or network infrastructure, measured in milliseconds.
      # - The value should be less than maximum-lifetime and greater than 30000 (30 seconds).
      # - Setting the value to zero will disable the keepalive functionality.
      keepalive-time: 0

      # This setting controls the maximum number of milliseconds that the plugin will wait for a
      # connection from the pool, before timing out.
      connection-timeout: 5000 # 5 seconds

      # This setting allows you to define extra properties for connections.
      #
      # By default, the following options are set to enable utf8 encoding. (you may need to remove
      # these if you are using PostgreSQL)
      #   useUnicode: true
      #   characterEncoding: utf8
      #
      # You can also use this section to disable SSL connections, by uncommenting the 'useSSL' and
      # 'verifyServerCertificate' options below.
      properties:
        useUnicode: true
        characterEncoding: utf8
        #useSSL: false
        #verifyServerCertificate: false
    tables:
      chat-logs: "spacechat_chatlogs"
      users: "spacechat_users"
      subscribed-channels: "spacechat_subscribed_channels"

#=#=#=#=#=#=#=#=#=#=#=#=#=#
# Redis Configuration     #
#                         #
# This allows multiple    #
# server to have the same #
# chat happening in       #
# realtime!               #
# ----------------------- #
# NOTE: THESE ARE NOT     #
# CHANNELS! THIS IS FOR   #
# MULTI-SERVER SYNC       #
#=#=#=#=#=#=#=#=#=#=#=#=#=#
redis:
  enabled: false
  # Set these server name values to the name of the current server the plugin is present on.
  # For example, if we're running on 'skyblock-1', change the identifier to 'skyblock-1'. This can be accessed
  # through placeholders using %spacechat_server-identifier%
  # The displayName is a display version of the server that can be accessed through placeholders as well by using
  # %spacechat_server-displayname%
  server:
    identifier: "server1"
    displayName: "&a&lServer #1"
  # redis://[password@]host[:port][/databaseNumber]
  # redis-socket:///path/to/socket
  url: "redis://[password@]host[:port][/databaseNumber]"

  # <!> 'chat-channel' and 'broadcast-channel' can ***NOT*** be the same <!>
  # Please choose two different channels
  chat-channel: "spacechat-message"
  broadcast-channel: "spacechat-broadcast"

  # This is the key that should be used to define where spacechat looks for a player's current subscribed channels list
  # If you do not know how to configure redis data structures and keys, DO NOT TOUCH THIS VALUE
  player-subscribed-channels-list-key: "spacechat:subscribedchannels:%uuid%:channels"
  player-current-channel-key: "spacechat:channels:%uuid%:current"
  channels-subscribed-uuids-list-key: "spacechat:channels:%channel%"

#=#=#=#=#=#=#=#=#=#=#=#=#
#      Misc Settings    #
#=#=#=#=#=#=#=#=#=#=#=#=#
logging:
  chat:
    log-to-storage: true

broadcast:
  # If enabled, any 'broadcast commands' will broadcast using the wrapper specified
  # in the lang.yml file. If disabled, all broadcasts will default to plain white with
  # no prefixes or suffixes
  use-lang-wrapper: false

item-chat:
  enabled: false
  replace-aliases:
    - "[item]"
    - "{item}"
  with:
    chat: "&7[&f%name% &ox%amount%&7]"
    lore:
      # If enabled, all [item]s in chat will have ONLY the custom lore that is listed below
      use-custom: false
      custom:
        - "&7This is"
        - "&6Custom"
        - "&c&bLore!"
  # This dictates the maximum amount of times that players can use the item-chat feature in a single message
  # Set to -1 to disable the maximum amount
  max-per-message: 2

# Enables or disables relational placeholders
# <!> <!> <!> <!> <!> You can only enable this if your server is [NOT] USING MULTI-SERVER CAPABILITIES (redis, etc) <!> <!> <!> <!> <!> Y
use-relational-placeholders: false

# Enables or disables owner recognition
# No need to change this value as it is set to "true" by default (and forced)
# in every other version of spacechat
owner-join: true

#=#=#=#=#=#=#=#=#=#=#=#=#=#
# Permissions             #
#                         #
# For:                    #
# Using chat colors (&)   #
# Using chat links        #
# Using item chat ([item])#
#=#=#=#=#=#=#=#=#=#=#=#=#=#
permissions:
  use-chat-colors: "space.chat.chatcolor"
  use-chat-links: "space.chat.chatlinks"
  use-item-chat: "space.chat.item-chat"
```