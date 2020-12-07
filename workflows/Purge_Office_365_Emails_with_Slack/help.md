# Description

Understanding the scope of a phishing campaign is critical to ensuring no one in your organization takes the bait. This workflow runs a search from a command in Slack and purges emails across Microsoft Office 365 inboxes.

Sample Slack Trigger Commands:

`@Rapid7 InsightConnect delete-emails subject="A phishy email"`

`@Rapid7 InsightConnect delete-emails subject="A phishy email" from="example.com" body="Click here for free stuff"`

`@Rapid7 InsightConnect delete-emails subject="A phishy email" delete=true`

# Key Features

* **Know the Blast Radius** - More often than not with phishing attacks, where there’s one email, there’s many. Quickly find all users affected by the same campaign.

* **Eliminate the Threat** - Once a phishing message is verified, automatically remove that message from every inbox in your organization.

* **Rapidly Respond** - Every second wasted adds more risk to your environment. Rather than hopping from tool to tool to respond, take action directly from Slack.

# Requirements

* [Slack](https://insightconnect.help.rapid7.com/docs/configure-slack-for-chatops)
* [Microsoft Office365 Email Security](https://insightconnect.help.rapid7.com/docs/mass-delete-with-powershell#section-set-up-office-365-dependencies)

# Documentation

## Setup

Import the workflow from the Rapid7 Extension Library and proceed through the Import Workflow wizard in InsightConnect. Import plugins, create or select connections, and rename the workflow as a part of the Import Workflow wizard as necessary.

Activate the workflow in order to trigger with a Slack command.

### Usage

This workflow uses the Chat Ops Slack connection to listen for key messages. When the Slack command triggers this workflow, it will open a compliance search in Office 365 and optionally delete messages.

To trigger this workflow, send a direct message to Rapid7 InsightConnect from Slack like the following:

`delete-emails subject="A phishy email"`

You can also trigger this workflow from any channel by referencing Rapid7 InsightConnect:

`@Rapid7 InsightConnect delete-emails subject="A phishy email"`

This will kick off the workflow and prompt you when the search is completed. If any emails are found that match the criteria, you can choose the delete button in Slack to delete them.

Search criteria can be 'body', 'subject', or 'from' lines in the email. For example:

`delete-emails subject="A phishy email" from="example.com" body="Click here for free stuff"`

Any combination of 'body', 'subject', and 'from' can be used. At least one search item must be given.

If you'd like the workflow to just delete emails without prompting, you can also use 'delete=true'. For example:

`delete-emails subject="A phishy email" delete=true`

## Technical Details

Plugins utilized by workflow:

|Plugin|Version|Count|
|----|----|--------|
|Microsoft Office365 Email Security|2.2.1|3|

## Troubleshooting

_There is no troubleshooting information at this time_

# Version History

* 1.1.0 - Replace a Python script with Pattern Match steps for argument values extraction | Remove Python script for preparing a query | Improve workflow messaging | Update screenshots
* 1.0.3 - Change trigger command from `purge-email` to `delete-emails`
* 1.0.2 - Changed content search query to use double quotes | Workflow no longer prompts a manual purge when 0 emails are found | Trigger no longer requires an exclamation mark | Updated documentation
* 1.0.1 - Updated documentation
* 1.0.0 - Initial workflow

# Links

## References

* [Microsoft Office365](https://www.office.com)
* [Microsoft Office365 Email Security Plugin Configuration](https://insightconnect.help.rapid7.com/docs/mass-delete-with-powershell#section-set-up-office-365-dependencies)
* [Slack Configuration](https://insightconnect.help.rapid7.com/docs/configure-slack-for-chatops)
* [Slack](https://slack.com/)
