# Linkfyn plugin

Make and run your [Linkfyn](https://linkfyn.co) page from Claude, ChatGPT or Codex. Linkfyn is a link in bio for small businesses that sell through WhatsApp and other chat apps: one mobile page with an order form, where every order arrives in your chat app with the details typed and is saved in the Linkfyn app so you can track it until it's done.

This plugin connects your AI app to Linkfyn and teaches it how to set up your page with you, step by step.

## What you can ask

- "Set up a Linkfyn page for my cake business."
- "Rewrite my page so it's clearer what I sell."
- "Add an order form that asks for the date and pickup or delivery."
- "Let customers book a facial or a massage, Tuesday to Sunday, 10 to 7."
- "Is my page ready to go live?"

## What's inside

- **Connector**: Linkfyn's MCP server at `https://mcp.linkfyn.co/mcp`. You sign in or sign up in Linkfyn's own window (Google, or a code emailed to you); your AI app never sees a password.
- **Skills**:
  - `set-up-linkfyn`: from nothing to a published page.
  - `write-my-page`: words, blocks, order forms and look.
  - `take-appointments`: services, hours, rooms or people.
  - `launch-my-page`: check, publish, test and share.

## What it can and can't do

It can make a shop, edit its page and forms, add photos, publish, and set up appointments. It can't see your customers, orders, appointments or team; those stay in the Linkfyn app. Page changes are a draft until you say publish. Appointment setup changes are live at once, so it asks first.

## Install

- **Claude Code**: `/plugin marketplace add linkfyn/linkfyn-plugin`, then `/plugin install linkfyn`.
- **Claude**: find Linkfyn in the Connectors Directory.
- **ChatGPT and Codex**: find Linkfyn in the app or plugin directory.

## Privacy and terms

[Privacy Policy](https://linkfyn.co/privacy) · [Terms](https://linkfyn.co/terms) · Questions: hi@linkfyn.co
