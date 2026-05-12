# Aramoho-Whanganui RC - Water Log

## What The App Is

This is a digital version of the clubhouse whiteboard.

It answers three simple questions:

- Who is on the water?
- What boat did they take?
- Are they safely back?

The app should be simple enough that a rower can use it while carrying kit, wearing wet hands, or being in a hurry.

## Main Flow

1. A crew taps **Sign Out**.
2. They choose their boat.
3. The app creates the right number of crew-member rows for that boat.
4. They choose each rower from the member list.
5. If the boat is coxed, they choose the coxswain.
6. They tick the captain, usually the person completing sign-out.
7. Each rower's and coxswain's name is colour coded by ability grade.
8. They choose when they expect to be back.
9. The app records the boat as **On Water**.
10. When they return, they tap **Sign In**.
11. If something is broken, they tap **Sign In + Damage**.
12. Damaged boats are marked for repair.

## Screens

### Sign Out

This is the main screen.

It should have big controls, short labels, and no unnecessary typing.

Fields:

- Boat
- One crew-member dropdown for each seat in the selected boat
- Coxswain dropdown for coxed boats
- Captain checkbox beside each rower and coxswain selector
- Colour coded ability grade for each selected member
- Expected back
- Optional notes

Coxed boat types:

- 4+
- 4x+
- 8x+
- 8+

Ability grade colours:

- Novice: yellow
- Intermediate: pink
- Club: red
- Senior: black
- Premier: gold
- Masters: green

### Sign In

This screen only shows boats currently on the water.

Each crew has two actions:

- **Sign In**
- **Sign In + Damage**

### On Water

This is the safety view.

It shows:

- Crews currently out
- What boat they have
- Who is in each boat
- Coxswain, if the boat is coxed
- Each rower's ability grade shown by name colour
- When they are due back
- Whether they are late after the 30-minute grace period

### Plant

This shows boat status:

- Available
- On Water
- Repair
- Derigged

The boat fleet should be populated from the club boat allocation sheet. Boats marked as derigged or in repairs should appear in the plant list but should not be selectable for sign-out.

Boat colours should match the fill colours used in the boat allocation sheet so members can recognise the same visual categories in both places.

The app refreshes the boat allocation sheet on load, every minute while open, and whenever the tab becomes active again. If a boat is changed to Repairs or Derigged in the sheet, it becomes unavailable for sign-out. If it is changed back to Scull, Sweep, Rigged, or Available, it becomes available again and shows as Available in the app.

## Historical Logbook

The app should keep a historical logbook of all outings. The logbook should include the boat, rowers, coxswain, captain, sign-out time, expected-back time, alert time, sign-in time, notes, and damage notes.

The live version should send logbook events to a Google Sheet through a small Google Apps Script web app.

## Phone Pop-Up Notifications

What you want is called **push notifications**.

There are two stages:

### Prototype Stage

The prototype can show phone/browser notifications after the user taps **Enable**.

This works best while the app is open or installed as a web app on the phone.

### Live Club Stage

For reliable phone pop-ups when the app is closed, the app needs:

- A backend server
- Web push subscriptions
- A scheduled overdue check
- A push notification service

That is different from email and SMS. It is the same style of notification used by apps like weather, banking, and calendar apps.

Overdue notifications should be sent 30 minutes after the expected-back time. For example, if a boat is expected back at 7:00pm, the alert should trigger at 7:30pm.

## Design Rules

- Big buttons
- Few screens
- No passwords for normal rowers if possible
- No typing where a dropdown will do
- Late boats are visually obvious after the 30-minute grace period
- Damaged plant is easy to mark
- The safety view is readable at a glance
