Scripts for lazy developres
===========================

## set of scripts that eases daily work and reduce repetitive work and ensures consistency

if the script is taking optional ticket_id, it either acts on provided ticket_id or uses current ticket_id set by *set_ticket* script

- **set_ticket <ticket_id>** stores the id of the ticket you work on to the file, so you do not have to type it repeatedly
- **ticket** outputs the current ticket you are working on - reads what was set by **set_ticket**
- **jira_data [<ticket_id>]** queries jira api for ticket details and returs reduced set of data, expects $JIRA_URL, $JIRA_USERNAME and $JIRA_API_TOKEN env variables to be set
- **branch_name [<ticket_id>]** returns how the branch for ticket_id should look like
- **commit_message [<ticket_id>]** returns how the commit message for ticket_id should look like
- **component-name** walks up the current working directory and asks the user if CWD is the component name that shall be used
- **into progress <ticket_id>** via jira api sets the ticket to _In Progress_ state (ensure it is transition 201 in your care)
- **confirm <any set of commands>** - Asks the user if the provided command shall be executed, or if the user wants to edit the commands or skip. Usefull for interactive scripts. The edit functionality uses env variable $VISUAL for starting desired editor
- **start_working <ticket_id>** - whole workflow of starting working on a ticket

## Required environment variables:

- **JIRA_URL** url of your jira: eg. `https://braiins.atlassian.net`
- **JIRA_USERNAME** - your login username in jira, email in my case
- **JIRA_API_TOKEN** - api token obtained from jira
- **TICKET_FILE** - file path where set_ticket and ticket scripts would store current ticket, if not set it would use `~/ticket_id`
- **VISUAL** or **EDITOR** for using your desired editor in confirm script
