---
name: find-through-people-you-know
description: Find someone outside the person's own groups through people they know on Openbook: a plumber, a tutor, a pediatrician, a sitter, with find_people, then ask for their number with request_field; nobody sees anyone's contacts, and nothing is shared without a yes.
---

# Find someone through people you know

Use this when `search-contacts` finds nobody, or the person wants someone they don't know yet.

1. **Explain first:** nobody sees anyone's contacts. Openbook looks through what people they know could share, shows why each match came up but never who it is, and nothing is shared unless the person who has the contact says yes.
2. **It needs their contacts.** `find_people` works once they've added the contacts on their phone with Find people through contacts; if it says so, offer `add-phone-contacts`. It's also off while they limit requests to one group, or while every contact they added is hidden.
3. **Make each search count:** there are 3 a day. Ask what matters first, then search with `looking_for` (specific, like “a plumber who fixes water heaters”), `near` (a town or neighborhood) and `limit`.
4. **Show the matches as they come:** each has `why` it matched, its `area`, how many groups and people it came through, and `could_share`, who could share it. Someone you know shows by name; someone found through a group shows only as “Someone in a group you're in”. Never guess who a match is, and never ask anyone to guess.
5. **Ask for one:** `request_field` with the `match`, the `field` it offers (like `{ type: "phone", label: "work" }` for a business), `ask` with users from its `could_share`, and a `reason` in the person's words, like “Our water heater is leaking, hoping to book someone this week.” There's 1 request outside their groups a day, so confirm which match first.
6. **Follow up:** `my_requests` shows it waiting, then the answer. A yes puts the contact in Personal • By Request, which shows on their phones.
7. **If nothing comes up,** offer `ask-my-contacts`: a text they send to a few people they choose.
