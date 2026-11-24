# Scratch Studio Inviter

Automate curator invitations to your Scratch studio by scraping followers of active Scratch creators using `scratchattach`.

---

## Overview

Inviting curators manually to a Scratch studio is tedious. This script automates the process by:
- Fetching followers from any active Scratch profile (e.g., popular creators with high activity).
- Paginating through follower lists automatically.
- Sending curator invites directly to your studio via the Scratch API.

---

## Prerequisites

- **Python 3.8+** installed on your system.
- A valid **Scratch account** that has curator/manager permissions in the target studio.
- The `scratchattach` Python library:

```bash
pip install scratchattach
```

---

## Configuration

Open `Scratchattach Studio Linker.py` and replace the placeholder values:

```python
username = "YOUR_SCRATCH_USERNAME"
session = scratch3.login(username, "YOUR_SCRATCH_PASSWORD")

# Scratcher whose followers you want to invite (e.g., "griffpatch")
user = scratch3.get_user("TARGET_SCRATCHER_USERNAME")

# Target studio ID (found in the studio URL: scratch.mit.edu/studios/<STUDIO_ID>/)
studio = session.connect_studio("YOUR_STUDIO_ID")
```

Optional settings:
- `offset`: Adjust where in the follower list to start scraping (default: `900`).

---

## Usage

Run the script from your terminal:

```bash
python "Scratchattach Studio Linker.py"
```

The console will print each invited username along with the total count:
```text
username123 | Count: 1
coolcoder45 | Count: 2
...
```

---

## Rate Limits & Best Practices

Scratch enforces strict community guidelines and API limits on automated studio invitations:

- **100 Invites / Hour Limit**: Scratch restricts each account to adding approximately 100 curators per hour. Exceeding this rate can trigger account flags, temporary blocks, or bans.
- **Account Rotation**: To invite at higher volumes safely, rotate across multiple authorized accounts with pauses between batches rather than running continuously on a single account.
- **Privacy & Security**: Authentication is performed directly against Scratch's servers from your local machine. Never commit your credentials to a public git repository. Use environment variables or a `.env` file if publishing your repository.

---

## Disclaimer

This utility interacts directly with Scratch APIs. Use responsibly and in accordance with the [Scratch Terms of Use](https://scratch.mit.edu/terms_of_use) and Community Guidelines. The author is not responsible for any moderation actions taken against accounts using this script.
