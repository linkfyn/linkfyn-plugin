---
name: take-appointments
description: Set up appointments on a Linkfyn shop so customers can pick a service and a time on the shop's appointment page. Use when a Linkfyn shop owner wants customers to book appointments, set opening hours, services, rooms or staff.
---

# Take appointments on Linkfyn

Linkfyn has an Appointments module: customers open linkfyn.co/<shop>/book, pick a service and a free time, and send their name and number. The shop sees it in the Linkfyn app's calendar and confirms it in chat, or it's confirmed automatically.

Changes here are live at once. There is no draft, so read back what you'll change and get a yes first.

## Steps

1. `get_appointment_setup` to see what's there and what each setting can be.
2. Ask, in one message:
   - The services, how long each takes, and the price if they want it shown.
   - Opening hours for appointments, by day.
   - Whether someone confirms each request in chat, or it's confirmed automatically.
   - Whether customers book the shop, a room, or a person. If rooms or people, their names, and whether the customer picks or the shop assigns.
3. Read back the setup in a short list. On yes, call `edit_appointment_setup` with all the changes. Only set it to on (`enabled`) when they say to start taking appointments.
4. Add a button on the page with the action `{"kind": "book"}` (via `edit_page`, see `write-my-page`) so customers can reach the appointment page, and tell them they need to publish for the button to show.
5. Give them the appointment page link (`appointmentPage`) and `setupUrl` to check it in the app.

## Rules

- Say "appointment", never "booking".
- Linkfyn holds the time; it doesn't take payment or deposits. Don't say it does.
- It can't see or change the appointments customers made, or the team. For those, send them to the app.
