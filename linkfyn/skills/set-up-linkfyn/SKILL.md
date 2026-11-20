---
name: set-up-linkfyn
description: Guide a small business owner from nothing to a live Linkfyn page (a link in bio that takes orders or appointments into their WhatsApp or other chat app). Use when someone wants to make a Linkfyn page, a link in bio, or a simple website for their business, or asks to get started with Linkfyn.
---

# Set up a Linkfyn page

Linkfyn gives a small business one link (linkfyn.co/their-shop) with a mobile page and an order form. A customer fills in the form, it opens the shop's chat app with the order typed, and the order is saved in the Leads list in the Linkfyn app. Your job is to get the owner from nothing to a published page in one conversation, asking a few plain questions at a time.

## Before you start

- Signing in happens in Linkfyn's own window when the connector is connected. Never ask for a password or an emailed code in chat. If a tool says they're not signed in, ask them to connect Linkfyn again.
- Call `list_shops`. If they already have a shop, ask whether to work on it or make a new one. If they have one, skip to step 4.

## 1. Ask about the business (one message)

Ask, in one short message:
- The business name.
- What they sell, in a few words (this picks the kind of starter page: food, flowers, print, beauty, events, services, coaching, or other).
- Which chat app customers message them on (WhatsApp unless they say otherwise) and the number or account.

Don't ask for anything else yet. Fill gaps with sensible defaults and say what you assumed.

## 2. Pick the address

Call `check_address` with the name. Offer the address it returns, or the free ones if it's taken. Let them change it. Addresses are 3 to 48 lowercase letters, numbers and hyphens.

## 3. Make the shop

Read back name, address, kind and chat account in one line and ask "Shall I make it?". On yes, call `create_shop`. It saves a starter page as a draft that customers can't see yet.

If it says Linkfyn can't make a shop for this account, explain plainly (new accounts from AI apps can have up to 3 shops, need a confirmed email, and only so many shops are made each day) and point them to request an invite at linkfyn.co. Don't retry.

## 4. Make the page theirs

Before you write anything, ask for 3 to 6 photos of their work, their logo and their Instagram or website, if they haven't shared them. Then use the `design-my-page` skill: it picks a look from their photos and colours, and rebuilds the starter into a page laid out like Linkfyn's best sample pages, in their words. The starter page is only a skeleton; never stop at swapping its words.

Photos: the starter page uses sample photos. Ask for their own:
- If they give a public https link to a photo, or a small one you can read (such as their logo, as a `data:image/...;base64` address of 2 MB at most), use `upload_photo`, then put the returned address in the block with `edit_page`.
- Otherwise give them `addPhotosUrl` from `create_shop` or `get_setup_progress` to upload from their phone, then `list_photos` to use them.

Never leave sample photos on a page you call finished. `get_setup_progress` reports `samplePhotosLeft`.

## 5. Show, then publish

Send them the `editorUrl` to see the page. Ask whether to publish. Only call `publish_page` after they say yes. Then give them their live link (`pageUrl`).

## 6. Next steps

Use the `launch-my-page` skill: send a test order, put the link in their bio, and open the Linkfyn app (`appUrl`) where orders arrive.

## Rules

- Linkfyn doesn't take payments, doesn't run a chat bot, and doesn't read their chats. Never say it does.
- Don't mention prices, plans or upgrades.
- Say "appointment", not "booking".
- One question at a time where you can; owners are often on a phone.
