# Delta-Time

Peer-to-peer messenger. No server. No accounts. Nothing to trust but math.

![Status](https://img.shields.io/badge/status-alpha-orange)
![License](https://img.shields.io/badge/license-MIT-blue)
![project](https://img.shields.io/badge/open-source-green)

⚠️ **Alpha software, not audited yet.** Read the [Threat Model](./THREAT_MODEL.md) before you rely on this for anything that actually matters.

[Threat Model](./THREAT_MODEL.md) · [License](./LICENSE) · [Contributing](./CONTRIBUTING.md) · [Donate](./Donate.md)

---

## What is Delta-Time

A messenger that doesn't have a company behind it. Messages go directly between users over Tor Hidden Services v3, so there's no server sitting on your conversation history, waiting for a breach, a subpoena, or someone's policy to change.

No phone number, no email, no account. First time you open it, Delta-Time generates a keypair on your device. That's your identity. Every message you send is signed with it, so nobody can forge messages as you.

## The problem

Every message you've sent on Telegram, WhatsApp, even Signal, lives somewhere you don't control. It might be encrypted. The privacy policy might be good, today. None of that is a guarantee, it's a promise, made by people who can get acquired, get hacked, or get a legal order they're not allowed to talk about.

You've probably felt this without ever putting it into words: that low-grade unease about how much of your life sits in someone else's database. Deleting a chat doesn't mean it's gone. A green padlock icon doesn't mean nobody can be compelled to hand over access. The people protecting your data today have no obligation to be the same people, with the same intentions, next year.

The better messengers lower the risk. None of them get rid of it. There's still a server somewhere. Still someone who could, in theory, be pressured, bought, or broken into. You're always one step away from trusting a stranger with a decision you'll never even see happen.

## How Delta-Time solves it

Delta-Time just doesn't have the thing you'd need to trust.

No server means no company database that can leak. No policy that can quietly change. No entity anyone can subpoena. "We take your privacy seriously" is a statement about something, and here there's nothing to make it about.

Your identity is a keypair, not an account. No sign-up, so there's no record you ever signed up. Messages are signed, so nobody, including us, can put words in your mouth.

This isn't privacy done a bit better. It's a different bet entirely: instead of asking you to trust that whoever's holding your data will do right by you, Delta-Time skips holding the data in the first place.

## How it works

- **No central server** – peer-to-peer over Tor Hidden Services v3. Nothing centralized to hack, subpoena, or leak.
- **Local identity, not an account** – Ed25519 keypair, generated on your device, never leaves it.
- **Signed messages** – every message carries the sender's signature, so identity spoofing gets caught at the protocol level instead of relying on a server's word.
- **TOFU pinning, shown to you** – first time you talk to someone, you see their key fingerprint and confirm it yourself. Not buried three menus deep.
- **Encrypted at rest** – your local message history is encrypted on disk, not sitting there in plaintext.
- **Open source** – don't take any of the above on faith, go read the code.

## How this differs

| | Telegram / WhatsApp | Signal | Delta-Time|
|---|---|---|---|
| Central server | Yes | Yes | No |
| Requires phone number | Yes | Yes | No |
| What you're trusting | A company and its policy | A foundation and its server | Nothing, it's just architecture |
| Identity verification | Buried in settings | Optional, easy to skip | Shown up front, on first contact |

## Status

This is alpha software. Bugs, breaking changes, and rough edges are the norm right now, not the exception.

- ✅ Core P2P messaging over Tor v3
- ✅ Ed25519 signing and identity verification
- ✅ Local encryption at rest
- 🔜 Windows build, aiming for beta around July 20–23
- 🔜 Independent security audit, planned for after beta
- ⏳ Android support, looking at an Orbot-based approach

No professional audit has happened yet. Check the [Threat Model](./THREAT_MODEL.md) for the honest version of what's actually covered right now, and what isn't.

## Installation

```bash
git clone https://github.com/<your-username>/delta-time.git
cd delta-time
pip install -r requirements.txt
flet run
```

Packaged builds for Windows and Linux are coming closer to beta. For now, you're running from source.

## Usage

1. Open delta-time. It generates your identity keypair locally, automatically, no input from you needed.
2. Send your public identity to whoever you want to talk to, through any channel you already trust, QR code, text, in person, whatever works.
3. First time you connect, you'll see their key fingerprint. Check it against what they actually sent you before you confirm. This one step is what stops someone from spoofing them, don't skip it.
4. After that, just message normally. Routing over Tor happens in the background.

Tor bridge settings and storage options live in the Settings panel.

## Contributing

At this stage, honest feedback is worth more than code. If you find a bug, a gap in the threat model, or something that just feels wrong, open an issue and tell us.

See [CONTRIBUTING.md](./CONTRIBUTING.md) for setup and code style if you do want to contribute code.

## License

MIT, plus an added disclaimer for privacy and anonymity software. See [LICENSE](./LICENSE) for the details.
