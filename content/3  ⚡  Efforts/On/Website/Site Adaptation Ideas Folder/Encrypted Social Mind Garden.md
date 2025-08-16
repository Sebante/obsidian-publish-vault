---
id: 20250807105539301-78537
date: 2025-08-07
visibility: public
slug: 3--⚡--efforts/on/website/site-adaptation-ideas-folder/encrypted-social-mind-garden
---
---

## Seeking collaboration

*Help me **design**, **implement** or **reflect** on this.*

---

## Non-technical Overview:

Imagine you have a digital notebook where you write down your thoughts, ideas, or notes. Normally, that notebook lives only on your computer, or on a companies server.

This project is about making that notebook **live on the internet** in a way that is still **secure and fully in your control**:

- You can decide if a note is **just for you**, shared with **specific friends**, or made **public for everyone**.

- When you share with friends, they can **reply to your notes** like a conversation, or **link to them** to grow a connected web of ideas — kind of like a shared “[mind garden](/1--🌐--Atlas/Dots/Concepts/Mind-Garden).”

- Everything is **locked with encryption**, which means only the people you choose can actually read your notes. If you ever want to stop sharing, you can “change the lock,” and those people won’t see your future notes anymore.

In short, it’s a **secure, social notebook** that lives on the internet — **encrypted, decentralized, and fully in your control**.

*Scroll down for Technical Overview*

---

### Concept Art and Visual Aids:


<img src="/4--x/PublishedAssets/public---Concept-Art-for-Encrypted-Social-Mind-Garden.png" alt="public - Concept Art for Encrypted Social Mind Garden.png">

---

<img src="/4--x/PublishedAssets/public---Obsidian-Features.png" alt="public - Obsidian Features.png">

---


<img src="/4--x/PublishedAssets/public---Screen-Shot-of-My-Quartz-Hosted-Mind-Garden.png" alt="public - Screen Shot of My Quartz Hosted Mind Garden.png">

---


<img src="/4--x/PublishedAssets/public---Obsidian-Screen-Shot.png" alt="public - Obsidian Screen Shot.png">

---
## Technical Overview:

A concept for **permissioned sharing of encrypted [obsidian notes](/1--🌐--Atlas/Dots/Concepts/Obsidian-Note)** over the **[Nostr](https://en.wikipedia.org/wiki/Nostr) protocol**.

Notes are stored in an encrypted Obsidian vault, published via Nostr relays, and selectively shared based on cryptographic access controls.

The system extends the idea of a personal [mind garden](/1--🌐--Atlas/Dots/Concepts/Mind-Garden) by introducing:

- **Private notes** – visible only to the owner.
- **Invite-only notes** – shared with selected peers.
- **Public notes** – openly published and linkable.

Permissioned viewers can:

- **Reply to notes** to form threaded conversations
- **Link to notes** to collaboratively build inter-connected “mind gardens.”


---

## Core Concepts

- **Vaults** – collections of Obsidian Markdown files encrypted and stored on Nostr.
- **[Notes](/1--🌐--Atlas/Dots/Concepts/Obsidian-Note)** – atomic units of knowledge (Markdown files) that may be private, shared, or public.
- **Threads** – reply chains attached to a note, enabling discussions.
- **[Mind Gardens](/1--🌐--Atlas/Dots/Concepts/Mind-Garden)** – curated sets of linked notes, visible to those with access.

---

## Implementation Details

### Storage & Retrieval

- An **Obsidian plugin or API** manages vault synchronization.
- Notes are encrypted client-side and stored on **Nostr relays**.
- Decryption requires:
    - A user’s **Nostr public key (NPUB)*
    - The corresponding **decryption key** for the current epoch

### Access Control

- A **single vault key** is used with **rotating epochs**.
- The vault owner can rotate the epoch key to revoke access, effectively “scrambling” local plaintext for unauthorized users.
- Sharing access is performed via **Nostr DMs**:
    - The vault owner sends the current epoch decryption key to an authorized NPUB.
    - This provides permissioned synchronization of encrypted vaults.

### Metadata

- Note metadata preserves vault structure, relationships, and permissions.
- Metadata enables:
    - Graph-like connections between notes.
    - Thread tracking for discussions
    - Controlled linking into collaborative “gardens.”

---

## Proof of Concept Scope

This POC does not aim to provide a production-ready system, but to validate key design assumptions:

1. Obsidian vaults can be stored and retrieved over Nostr.
    
2. End-to-end encryption with rotating epoch keys allows revocation and fine-grained sharing.
    
3. Notes can be extended with reply and linking mechanisms to create **social, permissioned knowledge networks** 

---

## Disclaimer on Revocation

Revoking access in this system works going forward, not backward.

When you rotate your key, anyone without the new one will see your notes turn into scrambled text on their next sync — which blocks them from reading future notes. But if they already saw or copied past notes, that can’t be undone. 

In other words: revocation is **strong for new notes**, but only a **soft lock** on old ones. 

Replies, links, and overall structure still stay visible, but the content of your revoked notes will be unreadable.


---

**Comment below to join the conversation :)**