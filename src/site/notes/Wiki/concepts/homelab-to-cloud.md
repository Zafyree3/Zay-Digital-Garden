---
{"dg-publish":true,"permalink":"/wiki/concepts/homelab-to-cloud/","title":"Homelab → Cloud: the translation table","tags":["concept","cloud","iac","homelab","devsecops"],"created":"2026-11-25T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00","dg-note-properties":{"title":"Homelab → Cloud: the translation table","created":"2026-11-25T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00","type":"concept","tags":["concept","cloud","iac","homelab","devsecops"],"sources":["https://github.com/ChiefGyk3D/Clouds-Against-Humanity"],"confidence":"high"}}
---
# Homelab → Cloud: the translation table

The fastest way into cloud is not to start from a definition. It is to start from
what a homelab already does, and find out what the same job is called when it is
rented by the hour.

Almost every cloud concept has a home equivalent. The differences are rarely about
the *idea* — they are about ownership, lifetime and who holds the invoice.

| At home you have | In the cloud it is called | What actually changes |
| --- | --- | --- |
| A Raspberry Pi or old PC running Linux | A **virtual machine** (DigitalOcean calls it a *droplet*) | Rented by the hour, created and destroyed by an API call, and it has a public address from the moment it boots |
| Your home LAN behind the router | A **VPC** (virtual private cloud) | A private network you define, with addresses you choose; nothing is in it unless you put it there |
| The router firewall | A **cloud firewall** | You write the rules. The default is "everything open", so the first job is closing all of it |
| A VPN into the house | **ZTNA** (zero trust network access) | No open port. Access is decided per person, per host, per port — not "you connected to the network, therefore you are trusted" |
| Running commands, and your shell history | **Infrastructure as code** | The environment is text files. Applying builds it; deleting the files alone removes nothing |
| A `.env` file | A **secrets manager** | One place for secrets, with access logging, rotation and expiry |
| Containers you run on the Pi | Containers on a VM | Same tool, different question: the machine is disposable, so nothing may live only on it |
| Copying files to a backup drive | **Version control** | Every change recorded, reviewable, revertible |
| The electricity bill | A **usage bill** | Per hour, and a forgotten machine keeps billing |

## The four ideas worth carrying home

If you take nothing else from a cloud course, take these:

1. **Write the environment down.** A machine you configured by hand is a machine
   nobody can rebuild. A machine described in a file can be destroyed and recreated
   the same afternoon.
2. **Plan, then approve, then apply.** The professional workflow is not "run the
   command". It is: show what *would* change, have a human read it, then change it.
   Everything else — pull requests, CI, approvals — exists to make that safe.
3. **Secrets are fetched, never stored.** Not in the repo, not in a note, not in a
   comment. A deploy identity gets read-only access to exactly the secrets it needs.
4. **Access is per resource, not per network.** "Behind the firewall" is not a
   security model. Identity plus a per-request decision is.

## What does not transfer

The concepts are portable. The *tooling* usually is not: the reference build for this
page uses commercial SaaS for the policy runner, the identity broker and the secrets
manager. Learn the shape — a policy-as-code runner, an identity broker, a secret
store — and then map it onto whatever you actually run, which at home is usually a
WireGuard-based overlay, GitHub Actions and an encrypted file in git.

One more warning: a curriculum that leans on a single provider teaches one provider's
vocabulary. A comparison table across clouds is worth less than knowing what your own
machines are for.

## Where the table comes from

[Clouds Against Humanity](https://github.com/ChiefGyk3D/Clouds-Against-Humanity) —
Apache-2.0, and not a game despite the name (it is a pun on Cards Against Humanity).
It is a small, deliberately cheap DigitalOcean environment where no machine has a
single public inbound port, plus a large wiki of lessons around it. The wiki is the
real product; the repository is the environment the lessons use.

Two honest caveats, both stated by the project itself: the reading and exercises are
free but the hands-on labs run on your own account and your own bill (stages 0–1 are
around $12/month, with a $30/month ceiling enforced in CI), and the AWS/Azure/GCP
pages are labelled unverified drafts — written from vendor documentation, never
applied in a real account.

Treat a deployed lab environment as disposable practice. The durable outputs are the
habit of writing infrastructure down and the habit of threat-modelling before
building.

## Related
- [[Map of Content\|Map of Content]]
- [[Wiki/concepts/personal-knowledge-management\|Personal Knowledge Management]] — the same instinct, applied to notes
- [[Wiki/entities/hermes-agent\|hermes-agent]] · [[Wiki/entities/ollama\|ollama]] — what runs locally, and why that is the default