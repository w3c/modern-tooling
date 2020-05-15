W3C Community calendar specifications
===============

Initial goal of the project:
    Craft a system that will let the W3C community handle their meeting information as events in a calendar, 
    with associated information: attendees/invitees, agenda, minutes.

__Out of scope__

* Making the reservation on the teleconferencing platforms
Each system would require specific integration with its own API
We want to leave the liberty to groups to choose and change of platform.

* Integrate other calendars such as private/personal calendars. This can be achieved in calendar clients.
 

Creating / editing meetings
----------------

Some users can create and edit group meetings: (Access Control to be defined)

__Features__


* One-time or recurrent [weekly, bi-weekly, monthly, every n-th xxx-day, n-th of the month, support Excluded date, support end-date]. 
Let the user set the meeting base TZ (no default value)
* Create / update (not the date) / move (=update the time, date, or recurrence) / delete from web interface: 
Changes can trigger email reminders. [more details to be specified]
* Tie a meeting to one (or several?) W3C groups (attendees). Possibility to add a guest group for an occurrence of a recurring meeting?
* Add guests -- Should this be limited to guest individuals or also handle guest groups?
* Support for Time Zones (at least using link to TZ converter) -- The displayed timezone should be configurable in the web 
view. An improvement would be to select by default the user timezone (it would be stored in his W3C user profile).
* Meeting information (number, passcode, URI, etc.) -- description
* Agenda -- URI only. As an usability improvement a user can set a default value for a group to build those URIs from template+date elements
  https://github.com/w3c/xxxxxx-wg/meetings/agenda-${YYYY}-${MM}-${DD}.md
  Some groups are using the same URL for all their meetings (eg shared among the various TF of the same WG), we would have default values for meeting info.
* Minutes -- URI, same as for agenda, possible default value from template+date elements
* Send invitations with at least plain text format -- VCALENDAR high priority feature (.ics)
* Get regrets or confirmation: -- requires CalDAV , some email clients offer decline emails to sender.
* Create / update / delete from other calendar clients (e.g. CalDAV)
* Meeting invitation (aka "first reminder") should be sent to the public group mailing list, the invitation should not 
contain sensible info (eg teleconf link or password), which will be displayed on the calendar event page only for an 
authentified user.
* Choice of reminders/notifications of updates on event (eg agenda updated, new time, event canceled, ...): Email reminders can be sent to users directly and not to the group mailing list. Users can set VALARM in their own tools, opt-out from email reminders (in their user profile), or follow the meeting organizer choice (default).


Viewing meetings / events
------------------

All users with W3C accounts have a web view of group meetings: 
-- public view if we integrate public events from the existing W3C events calendar. 

__Features__

* Web interface with a view of a group's meetings  -- API to retrieve info from another page? 
Access control for sensitive info. Public view of non-sensitive info.
* Add (or sync?) with a user's calendar client, i.e. data in a standard format
* Get data to be consulted offline later (e.g. download a .ics file, or CalDAV)
* Access meeting info/agenda/minutes (links)
* Give regrets to the chairs and team contacts or confirm presence -- calendar clients typically send emails to accept/decline. Do we need this in the web view?
The "opt-out from email reminders" is a user-specific setting and global for all meetings, from user profile.

A user calendar can show meetings where they are defined as attendees 
(as a group participant or additional guest), other group meetings, public meetings. They can't add themselves as attendees.
Viewing other (or all) groups meetings is possible, but the viewing filters will not be stored.
Filters could be bookmarkable URIs.
Ideally there would be list or calendar views.

Accessibility is a requirement for all the interfaces.
