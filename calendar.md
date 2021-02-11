## Context

This document contains a list of use cases/requirements for a W3C community-wide calendaring system. It will help the W3C community to organize itself and simplify their handling of meetings. It is intended for W3C Groups at large and to be viewable by a large set of calendar clients.


## Use cases

1. Schedule meetings for Working Groups, Interest Groups, Community Groups, Business Groups, Advisory Board, Task Forces
1. Schedule joint meetings and meetings with observers/guests
1. A chair or team contact schedule (video/phone/f2f) meetings at a specific time, or recurring time, within a specific timezone
1. Provide joining instructions only visible to meeting participants
1. Participants receive calendar invitations that can be added to their own calendar, in their own local timezone
1. Participants may signal regrets or intent to participate
1. A chair or team contact should be able to schedule ad-hoc variation in meeting occurrences:
   1. Cancel if it’s around holidays/f2f meetings/TPAC
   1. Shift by hours or days based on travels, meeting conflicts or UTC/DST
1. Ability to schedule complex recurrence patterns:
   1. Regular meetings may alternate times within the same month to accommodate global participation (eg CSS)
1. Attach additional information to each meeting occurrence:
   1. Agenda
   2. Minutes/Notes
1. … provide a Web view of the calendar


## Requirements

1. For a Group Chair/TC, using the W3C website
   1. Create, and view group meetings. Creating calendar entries needs to be easy, not idiosyncratic to
      some edge tool. Many people will need to do this frequently and it
      should not become an administrative burden.
   1. Use one-time or recurrence patterns:
      1. weekly, bi-weekly, monthly recurrence
         1. "nth XXX-day" (e.g. 1st and 3rd Monday) of the month as well as the Xth of each month.
      1. allow exception dates
      1. allow recurrence end date
   1. Update, move, delete each meeting occurrence at any time
   1. Associate the meeting to the group, a task force, or a subset of group individuals
   1. Add non-group participants to meeting occurrence/recurrence
   1. [nice to have] Create joint meetings (2+ groups)
   1. Anchor the meeting in a specific timezone (UTC by default). The system will provide automatically a link to a timezone converter
   1. [v.next] Optionally, activate meeting invitations/reminders for participants
   1. Provide attendance instructions to meeting participants (with Member-only link for WebEx passcode/Hangout link, if any?)
   1. Link to agenda/notes/minutes for each meeting occurrence
   1. [v.next] [nice to have] Optionally receive notification if a participant confirm/regret
      1. if so, ability to specify an alternate address or web dashboard for those notifications
   1. [v.next] [nice to have] Write access from external clients (ical?)
1. For meeting participants:
   1. View group meetings using the W3C website
   1. Add/access/synchronize group meetings to a local calendaring client, eg iCal, Google calendar, SOGo, mobile platform, etc. (use iCalendar? https://tools.ietf.org/html/rfc5545 and https://tools.ietf.org/html/rfc5546)
   1. View group meetings offline (sometime participants are offline when they try to join)
   1. From a meeting occurrence, navigate easily to attendance instructions, agenda, minutes/notes
   1. the meeting information should be easily discoverable in plain text, when receiving invitation (and not just ical)
   1. [v.next] Regrets notifications should not be distributed to everybody else subscribed to the event.
   1. [v.next] [nice to have] Confirm/Regret on calendar invitation
   1. [v.next] [nice to have] Automatic meeting reminders need to be opt-in, and ability to easily opt-out if they have opted in.
1. For W3C community users
   1. [nice to have] User tailored calendar ideally, e.g. https://www.w3.org/users/myprofile/calendar (with all events of my groups, could be a redirect to another application, users can view the calendar or subscribe to one or a set of calendars), with ability to filter events
   1. [v.next] [nice to have] Specific non-W3C users read access (such as family)
1. For W3C staff
   1. Team members can use the same system to schedule side/non-group related meetings
1. For W3C website
   1. Provide an organization calendar
   1. Accessible tooling support https://www.w3.org/WAI/WCAG21/quickref/
   1. Internationalization support (timezones, non-english)
   1. TLS support, W3C account support
   1. Group database integration (DBWG). Support for any W3C groups such as WG, IG, AB, TAG, CG, and various task forces

NOTE: requirements may be met by a combination of off-the-shelf tools.

## Guidelines / documentation

* [guideline] Each event should contain call details (no browser needed to attend the call)
* [guideline] Discipline in canceling or moving meetings
* [guideline] Rotating the scheduling of meetings in different time zones
* [support] Providing support for people who have a hard time with calendar systems (user doc)
* [support] Explain how to share a given calendar and how to integrate it with a third party calendar application.

## Off-the-shelf tools

* [SOGo](https://sogo.nu/)
* [Google calendars](https://www.google.com/calendar)
* [Yandex calendars](https://calendar.yandex.com/)
* Anything else we should look at?

## Others

* Customized TPAC schedule, similar to IETF meeting agenda at https://datatracker.ietf.org/meeting/101/agenda ?
* free/busy handling for group and participants
* Anything else from https://www.washington.edu/ucal/require.html ?
