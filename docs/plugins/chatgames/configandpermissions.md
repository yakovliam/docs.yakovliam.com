# Config & Permissions

The configuration for ChatGames is very easy to understand.

Location
-
The main configuration's location is in the plugins folder under the subdirectory named 'SpaceChat' (`/plugins/ChatGames/config.yml`)

Example
-
Here's the default configuration contents.
```yaml
#   ██████ ██   ██  █████  ████████      ██████   █████  ███    ███ ███████ ███████  #
#  ██      ██   ██ ██   ██    ██        ██       ██   ██ ████  ████ ██      ██       #
#  ██      ███████ ███████    ██        ██   ███ ███████ ██ ████ ██ █████   ███████  #
#  ██      ██   ██ ██   ██    ██        ██    ██ ██   ██ ██  ██  ██ ██           ██  #
#   ██████ ██   ██ ██   ██    ██         ██████  ██   ██ ██      ██ ███████ ███████  #
settings:
  delay-between-games: "5m" # 5m = 5 minutes
  wait-until-answer-from-ask: "1m"
question-type-message:
  unscramble: "&7Unscramble &b[this word](hover: &cThe scrambled word is &b%supplied%&c!) &7for a chance to win a prize!"
  math: "&7Solve &b[this math equation](hover: &cThe equation is &b%supplied%&c!) &7for a chance to win a prize!"
text-wrapper:
  - "&8(&bChat Games&8) &7» %text%"
player-won-message: "&f[%player%](hover: &b%player% &aguessed the correct answer!) &7won the game! The answer is: &f%answer%&7!"
nobody-won-message: "&cNobody &7won the game! The answer was: &f%answer%&7!"
player-won-received-message: "&fYou won &f%prize%&f!"

# Use PlaceholderAPI placeholders for the commands
rewards:
  0:
    chance: 5.0
    command: "eco give %player_name% 100"
    handle: "$100"
  1:
    chance: 3.0
    command: "give %player_name% diamond 1"
    handle: "1 diamond"
  2:
    chance: 0.5
    command: "eco give %player_name% 1000"
    handle: "$1,000"
```