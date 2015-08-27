slt: Set your API Token

Open alfred and type slt, then paste your token. If you don't have a token, then hold cmd to open the API page to get one (look for your team near the bottom of the page).
slf: Search files

Open alfred and type slf to search files. Selecting a file opens it in your browser
slp: Set your presence

Open alfred and type slp active or slp away
slc: View, leave and join channels or private groups

Open alfred and type slc to display a searchable list of channels. Selecting a channel with alt leaves and ctrl lets you join. Currently only alt is functional with groups.

slclr: Clear unread messages

This currently only marks Channels as read and not groups. Depending on the size of your organizations this can also take a few seconds to run.
slim: Enter a users name to search for most recent DM messages
slr: Search your starred items

Highlight a result and hitting enter opens the web client to that result
sls: Perform a query across all your channels in your organizations

Highlight a result and hitting enter opens the web client to that result
Depending on the size of your organization this can take a few seconds to run
slk: Search users, groups and rooms while passing the select resulted to the desktop client with cmd+k functionality

Caution: If you are using multiple organizations this particular command will not interact properly with the desktop client. Currently Slack does not have a built out deep link system in OSX and without it it's hard to account for organization order in the your client. I left this in place for users in single organizations
Note: If you're using Slack in fullscreen mode you will need to a delay to the Applescript. Open Alfred preferences, go to the Slackfred workflow and double click the slk input. Add in a delay (you may need to tweak based on your monitor/system) similar to this example:
on alfred_script(q) tell application "Slack" to activate tell application "System Events" delay .6 keystroke "k" using {command down} tell process "Slack" to keystroke (q as string) key code 36 end tell end alfred_script



cal [month [year]] [<] [>]

↕ Choose a week.
enter ↵ Open /Application/Calendar with week view and selected week.
<, > Display calendar of previous/next month.
month year Display Calendar with specific month and year.
calconfig Show configuration file.

