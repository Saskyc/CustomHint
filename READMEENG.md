# CustomHint
## Description
A plugin that allows you to create your own custom HUD for the server.  
To ensure proper functionality, the plugin requires **AdvancedHints** and **Newtonsoft.Json**, which are included in the releases for all versions.  
For suggestions, please ping me on the EXILED Discord server or DM: @narin4ik.  

## Guide

### How to install the plugin?
Go to the [latest release](https://github.com/BTF-SCPSL/CustomHint/releases). Download all the *dll* files from the release. Then upload the following files to the server: *CustomHint.dll* and *AdvancedHints.dll* to the Plugins folder (`.../EXILED/Plugins`), and *Newtonsoft.Json.dll* to the dependencies folder (`.../EXILED/Plugins/dependencies`).  
After installation, *start/restart* the server.  
Once you've completed all the steps, the configuration will be generated in `.../EXILED/Configs` under `[port]-config.yml` and `[port]-translation.yml`.

### Configuring the plugin
We'll start with the easiest part, `[port]-config.yml`. Use the *CTRL+F* shortcut to search for `custom_hint` and locate the plugin configuration.  
The default `[port]-config.yml` looks like this, with all points explained:
```yaml
custom_hint:
# Plugin enabled (bool)?
  is_enabled: true
  # Debug mode?
  debug: false
  # Enable or disable HUD-related commands.
  enable_hud_commands: true
  # Enable or disable automatic plugin updates.
  auto_updater: true
  # Enable or disable game hints.
  game_hint: true
  # Enable or disable hints for spectators.
  hint_for_spectators_is_enabled: true
  # The interval for changing spectator hints (in seconds).
  hint_message_time: 5
  # Default role name for players without a role.
  default_role_name: 'Player'
  # Default role color (for players without roles).
  default_role_color: 'white'
  # Ignored roles.
  excluded_roles:
  - Overwatch
  - Filmmaker
  - Scp079
```
After configuring `[port]-config.yml`, move on to `[port]-translation.yml`. Use *CTRL+F* again to search for `custom_hint`.  
You'll find the following:
```yaml
custom_hint:
# Hint message for spectators.
  hint_message_for_spectators: |-
    <size=75%>{servername}
    {ip}:{port}

    {player_nickname}, spec, duration: {round_duration_hours}:{round_duration_minutes}:{round_duration_seconds}.
    Role: {player_role}
    TPS: {tps}/60

    Information:
    Class-D personnal: {classd_num} || Scientists: {scientist_num} || Facility Guards: {facilityguard_num} || MTF: {mtf_num} || CI: {ci_num} || SCPs: {scp_num} || Spectators: {spectators_num}
    Generators activated: {generators_activated}/{generators_max}

    {hints}</size>
  # Hint message for rounds lasting up to 59 seconds.
  hint_message_under_minute: |-
    <size=75%>{servername}
    {ip}:{port}

    Quick start! {player_nickname}, round time: {round_duration_seconds}s.
    Role: {player_role}
    TPS: {tps}/60</size>
  # Hint message for rounds lasting from 1 minute to 59 minutes and 59 seconds.
  hint_message_under_hour: |-
    <size=75%>{servername}
    {ip}:{port}

    Still going, {player_nickname}! Time: {round_duration_minutes}:{round_duration_seconds}.
    Role: {player_role}
    TPS: {tps}/60</size>
  # Hint message for rounds lasting 1 hour or more.
  hint_message_over_hour: |-
    <size=75%>{servername}
    {ip}:{port}

    Long run, {player_nickname}! Duration: {round_duration_hours}:{round_duration_minutes}:{round_duration_seconds}.
    Role: {player_role}
    TPS: {tps}/60</size>
  # Message displayed when the HUD is successfully hidden.
  hide_hud_success_message: '<color=green>You have successfully hidden the server HUD! To get the HUD back, use .showhud</color>'
  # Message displayed when the HUD is already hidden.
  hide_hud_already_hidden_message: '<color=red>You''ve already hidden the server HUD.</color>'
  # Message displayed when the HUD is successfully shown.
  show_hud_success_message: '<color=green>You have successfully returned the server HUD! To hide again, use .hidehud</color>'
  # Message displayed when the HUD is already shown.
  show_hud_already_shown_message: '<color=red>You already have the server HUD displayed.</color>'
  # Message displayed when DNT (Do Not Track) mode is enabled.
  dnt_enabled_message: '<color=red>Disable DNT (Do Not Track) mode.</color>'
  # Message displayed when commands are disabled on the server.
  command_disabled_message: '<color=red>This command is disabled on the server.</color>'
```
And after localization... Voilà! Everything is ready! You can restart the server *(fully)*, and CustomHint will work perfectly.  
Thank you to everyone who uses this plugin. Best of luck!  

## Placeholders
| Placeholder            | Description                           |
| ---------------------- | ------------------------------------- |
| {servername}           | Server name.                         |
| {ip}                   | Server IP address.                   |
| {port}                 | Server port.                         |
| {tps}                  | Server TPS.                          |
| {player_nickname}      | Player's nickname.                   |
| {player_role}          | Player's role.                       |
| {player_GameRoles}     | Player's game role.                  |
| {round_duration_seconds}| Round duration in seconds.           |
| {round_duration_minutes}| Round duration in minutes.           |
| {round_duration_hours} | Round duration in hours.             |
| {classd_num}           | Number of Class-D personnel.         |
| {scientist_num}        | Number of Scientists.                |
| {facilityguard_num}    | Number of Facility Guards.           |
| {mtf_num}              | Number of MTFs.               |
| {ci_num}               | Number of Chaos Insurgents.          |
| {scp_num}              | Number of SCP objects.               |
| {spectators_num}       | Number of spectators (including Overwatch). |
| {generators_activated} | Number of activated generators.       |
| {generators_max}       | Maximum number of generators.         |
| {hints}                | Hints from the Hints.txt file.        |
