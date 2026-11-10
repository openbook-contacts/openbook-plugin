---
name: request-controls
description: Change who can ask the person for contacts on Openbook: Allow requests from Everyone, All Contacts or Nobody, removing their number from searches, hiding a contact from requests, blocking requests from someone, and turning texts about requests on or off.
---

# Control who can ask

Explain requests from others before naming them: nobody sees the person's contacts, people they know can ask them for one, and nothing is shared without their yes. Each control below is the person's own; confirm before changing any.

- **Who can send requests:** `update_settings` `requests_from`: `everyone` (the default: people they know and people in their groups), `contacts` (only people whose number they have, in the contacts they added or on their cards) or `nobody`, which also turns off their own searches through others.
- **Their number in searches:** `update_settings` `findable_by_others: false` takes their own number out of searches across directories. Someone without an account can do the same at withopenbook.com/opt-out.
- **Hide one contact from requests:** `hide_contacts` with contacts from their own directory: nobody can ask about them through the person or anyone in their groups, and they stay in their groups and on their phones. `hidden: false` undoes it. Hiding every contact they added turns off their own searches through others.
- **Block requests from someone:** `block_contacts` with contacts of theirs that have a mobile number: that person can't send them any request, and isn't told. Requests from them already waiting go unanswered. `blocked: false` unblocks.
- **Texts about requests:** `update_settings` `texts: true` only when the person asks for texts themselves, after telling them that how often varies, that message and data rates may apply, and that they can reply STOP to stop and HELP for help. `texts: false` turns them off.
- **A whole group:** keeping a group out of everyone else's searches is Hide from search (`manage_groups` `hide_from_search`), which takes a plan and Who can join and find it. Say so and point to withopenbook.com, never a price. Hiding or blocking one of their own contacts is always theirs to do.

Nobody is told when they're hidden or blocked.
