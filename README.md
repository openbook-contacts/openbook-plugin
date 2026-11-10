# Openbook

Openbook gives a club, school, team or company one shared contact directory that shows up in everyone's phone contacts, and gives every person a directory of their own.

With Openbook in Claude you can:

- Start a directory for your group and make groups like Parents or Coaches.
- Add and update contacts, or hand Claude a spreadsheet, a photo of a sign-up sheet or an email thread, and check the contacts it makes before they're added.
- Decide what everyone in each group sees of each field: Visible, Request required or Hidden.
- Invite people by email, or with a text you send yourself.
- Answer and make requests for a contact's number or email.
- Put Openbook on your iPhone, iPad, Mac or Android phone, where the contacts stay current on their own, and choose whether each group shows in your Contacts or only when you search.
- Find someone through people you know, like a plumber or a tutor: nobody sees your contacts, people you know can ask you for one, and nothing is shared unless the person who has the contact says yes.

Openbook is invite only for now: you're invited once someone who uses Openbook invites you or adds your mobile number to one of their groups. It works with US mobile numbers.

## Install

In Claude, add Openbook from the directory, then connect it and sign in. In Claude Code:

```
/plugin install openbook --marketplace openbook-contacts/openbook-plugin
```

## What's in it

- **Openbook's connector**, at `https://api.withopenbook.com/mcp`. When you connect it, Openbook's own sign-in opens, and you sign in with your mobile number, a passkey or a code Openbook emails you. New users add their name and an email, which a code confirms.
- **Twenty skills, one job each**, which Claude picks as they fit: getting started, importing a spreadsheet, a vCard file, a photo or an email thread, keeping your own contacts in Openbook, recommendations, adding the people you know, refreshing a group for a new season, tidying contacts, inviting people, searching, finding someone through people you know, asking your contacts, answering requests, sharing your details, who can send you requests, phones, and groups and access, with Openbook's rules for every task.

## What it sends, and where

The plugin runs nothing on your computer. Its skills are instructions for Claude, and its one connector is Openbook's own server, `https://api.withopenbook.com/mcp`. Claude sends it only what you ask Openbook to do, like a contact to add or a name to search for. When you hand Claude a file, a photo or an email, Claude reads it and sends Openbook the contacts it found, once you've checked them.

Every tool only does what you could do in Openbook yourself, with the directories and groups your account can reach, and Openbook asks Claude to confirm changes with you before making them. Openbook texts only codes, and notices to people who turn texts on themselves, and it never sells anything in Claude. How Openbook keeps and uses what it gets is in its Privacy Policy, https://withopenbook.com/privacy, and its Terms are at https://withopenbook.com/terms.

## Help

Steps for connecting Openbook are at https://withopenbook.com/connect. Email support@withopenbook.com with anything else.

## License

The plugin's files are under the MIT License (`LICENSE`). Openbook itself is a service of Openbook Contacts Inc., under its Terms.
