# Commands

SpaceChat is a very simple but functional plugin, so there aren't many commands you need to learn.

Viewing Available Commands In-Game
-

To view all available commands, you can do the command `/spacechat`
This command will only be available to players with the permission node `space.chat.command`
         
Reloading The Plugin
-
To reload, you can simply do
`/spacechat reload`

Please note: You're also able to instantly reload the plugin simply by saving a configuration file.
The plugin will automatically handle it for you.

This will reload almost all aspects of the plugin, including:
- Storage
- Configurations
- Formats
- Logging Data
- Language Data
- All settings
- All database connections (if applicable)

In order to reload the plugin (using the command above), the applicable player needs the permission node `space.chat.command.reload`.


!> **Remember**: For any sub commands below `/spacechat`, the player **needs** to have the permission node `space.chat.command`!


Broadcasting
-
To broadcast, you can simply do
`/broadcast <message>`

This will broadcast a message to the server.
If the internal messaging system is enabled (redis), then all connected servers will also receive the broadcast.

In order to broadcast (using the command above), the applicable player needs the permission node `space.chat.command.broadcast`.

!> **Remember**: For any sub commands below `/spacechat`, the player **needs** to have the permission node `space.chat.command`!


Broadcasting with MiniMessage
-
To broadcast with minimessage, you can simply do
`/broadcastminimessage <message>`

This will broadcast a message to the server using minimessage instead of traditional color coding.
If the internal messaging system is enabled (redis), then all connected servers will also receive the broadcast.

In order to broadcast (using the command above), the applicable player needs the permission node `space.chat.command.broadcastminimessage`.

!> **Remember**: For any sub commands below `/spacechat`, the player **needs** to have the permission node `space.chat.command`!

Channels
-
To interact with channels, you can simply do
`/channel [join|leave|listen|mute]`

This will execute the applicable channel command.

In order to use channels (using the command above), the applicable player needs the permission node `space.chat.command.channel.join/leave/listen/mute`.

!> **Remember**: For any sub commands below `/spacechat`, the player **needs** to have the permission node `space.chat.command`!

