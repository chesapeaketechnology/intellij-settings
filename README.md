# intellij-settings
The common IntelliJ settings used by the development team.


## Usage
1. Open IntelliJ and select **File > Settings Repository...**
   Note: if you don't see this option, you will need to enable the Settings Repository plugin.
   
2. Copy the clone URL for this repository and paste it as the **Upstream URL**.

3. Click **Overwrite Local**


## Troubleshooting
- If IntelliJ ever fails to sync with an error such as "Failed to Sync Settings: Commit on repo without HEAD currently not supported", delete the local Git clone of the settings repository from
<user_home>\.IntelliJIdea<version>\config\settingsRepository\repository.


## About this repo
More information about this IntelliJ functionality is available [here](https://www.jetbrains.com/help/idea/sharing-your-ide-settings.html#settings-repository).

By default the Settings Repository plugin in IntelliJ automatically synchronizes the local settings
with the repository whenever a project is closed or IntelliJ is exited. This means that any changes
to the local settings would be written back to the repository. This is not desirable 
since we don't want to force individual user preferences on everyone.

One option to resolve this would have been to use the repo as a read-only settings repo by entering
the repo URL in the **Read-only Sources** list on **Settings > Tools > Settings Repository**. However
when testing this option, it did not seem like the read-only repo was actively used to keep settings
up to date, so if a change was ever made to the settings repo, it would not be reflected in IntelliJ.

The option chosen for this repository was to prevent writes to the settings repo. This way, IntelliJ
may try to write the local settings back to the repo, but it will not succeed. The failure is silent
so developers shouldn't be affected by the inability to push.

If the settings ever need to be modified, an administrator should disable **Require pull request 
reviews before merging** for master in the branches settings, make the change, and reenable the
setting, along with **Require review from Code Owners**.